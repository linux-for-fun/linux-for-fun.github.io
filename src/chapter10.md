### **Chapter 10: The Mystery Background**

Welcome to **The Mystery Background**, where we take your prank game out of the terminal and onto the desktop itself. Imagine your unsuspecting victim, happily working away, only to notice their desktop wallpaper changing randomly—sometimes to something funny, sometimes to something unsettling, and sometimes to something downright confusing. Slowly but surely, this visual chaos chips away at their sanity.

In this chapter, we’ll learn how to set up scripts to periodically change the victim’s desktop wallpaper without them knowing, ensuring that they spend more time wondering what’s happening than actually working.

Let’s get started.

#### **Step 1: Changing the Wallpaper from the Command Line**

Ubuntu and other Linux systems running GNOME or similar desktop environments have command-line utilities that allow you to change the desktop wallpaper programmatically. The utility we’ll be using for GNOME-based systems is `gsettings`. This tool is great for modifying desktop settings from the terminal.

First, try changing the wallpaper manually to make sure everything is set up correctly:

```bash
gsettings set org.gnome.desktop.background picture-uri "file:///path/to/your/image.jpg"
```

Replace `/path/to/your/image.jpg` with the actual path to the image you want to set as the wallpaper. If it works, the wallpaper should change immediately.

#### **Step 2: Creating the Wallpaper Prank Script**

Now, let’s create a script that will randomly change the desktop wallpaper to a series of different images at random intervals. The key here is to have a collection of images—funny memes, creepy pictures, or just confusing graphics—that will rotate in and out.

First, create a directory to store the images for the prank:

```bash
mkdir ~/wallpaper_prank
```

Add a few images to this directory. You can use any images you like, but for maximum effect, mix in harmless pictures with confusing or unsettling ones.

Next, create a new script called `mystery_background.sh`:

```bash
nano ~/mystery_background.sh
```

Here’s a simple version of the script:

```bash
#!/bin/bash

# Directory where wallpapers are stored
wallpaper_dir=~/wallpaper_prank

# Get a random wallpaper from the directory
random_wallpaper=$(ls $wallpaper_dir | shuf -n 1)

# Change the wallpaper
gsettings set org.gnome.desktop.background picture-uri "file:///$wallpaper_dir/$random_wallpaper"
```

This script randomly selects a wallpaper from the `wallpaper_prank` directory and sets it as the current desktop background. Save the file and make it executable:

```bash
chmod +x ~/mystery_background.sh
```

#### **Step 3: Automating the Wallpaper Changes with Cron**

Now that we have our wallpaper prank script, we want it to run automatically at random intervals to really mess with your victim’s head. We can achieve this by setting up a cron job that runs the script at regular intervals.

Open the crontab editor:

```bash
crontab -e
```

Add the following line to make the script run every 15 minutes:

```bash
*/15 * * * * ~/mystery_background.sh
```

This will run the script every 15 minutes, ensuring that the wallpaper changes regularly, but without making the changes so frequent that it’s immediately obvious. You can adjust the timing to make it more or less frequent, depending on how subtle you want the prank to be.

#### **Step 4: Randomizing the Intervals for Maximum Confusion**

To take this prank to the next level, we can randomize the timing of the wallpaper changes so that it’s not as predictable. Instead of running every 15 minutes, we can create a script that sleeps for a random amount of time between changes.

Here’s an updated version of the `mystery_background.sh` script:

```bash
#!/bin/bash

# Directory where wallpapers are stored
wallpaper_dir=~/wallpaper_prank

# Infinite loop to keep changing the wallpaper
while true; do
    # Get a random wallpaper from the directory
    random_wallpaper=$(ls $wallpaper_dir | shuf -n 1)

    # Change the wallpaper
    gsettings set org.gnome.desktop.background picture-uri "file:///$wallpaper_dir/$random_wallpaper"

    # Sleep for a random amount of time (between 10 and 60 minutes)
    sleep_time=$((RANDOM % 3000 + 600))  # 600 = 10 minutes, 3000 = max extra 50 minutes
    sleep $sleep_time
done
```

This script now runs in an infinite loop and changes the wallpaper at random intervals, between 10 and 60 minutes. To run this script automatically when the user logs in, add it to their `.bashrc` file:

```bash
nano ~/.bashrc
```

At the end of the file, add:

```bash
~/mystery_background.sh &
```

This will launch the script in the background every time the user logs in. They won’t even know it’s running, but they’ll soon start to notice that their wallpaper changes unpredictably throughout the day.

#### **Step 5: Choosing the Perfect Wallpapers**

To maximize the impact of this prank, it’s essential to pick a good mix of wallpapers. Here are a few ideas:

- **Funny images**: Include a few harmless memes or jokes to throw them off the scent. They might think someone’s just messing around in a fun way.
  
- **Creepy images**: Throw in some eerie images, like glitch art, strange abstract visuals, or unsettling close-up photos. These will make the victim question what’s really going on.

- **Weird graphics**: Use confusing pictures—like screenshots of their own desktop, but slightly altered, or random abstract art that doesn’t make sense. The goal is to make them wonder if the system is glitching.

- **Thematically appropriate images**: If you want to make it more personal, use images that reference the user’s work or interests, but in strange or distorted ways. For example, if they’re into coding, you could use images of broken code or error messages.

#### **Step 6: Adding Subtle Clues for Extra Paranoia**

If you really want to mess with their head, add subtle clues to the prank. Occasionally, set the wallpaper to something that hints at the prank without fully revealing it. For example:

- A screenshot of their desktop, but with tiny changes—an icon missing, or something slightly out of place.
- A message in the background, like “I’m watching you” or “System compromised,” written in faint text or hidden in an image.
- A wallpaper that looks like the login screen, making them think they’ve been logged out.

These clues will make the victim second-guess themselves, adding an extra layer of psychological manipulation to the prank.

#### **Step 7: Disabling the Prank**

Eventually, the victim will want to escape the never-ending cycle of wallpaper madness. To stop the prank, they’ll need to find and disable the script. If they’re savvy enough, they might check the cron jobs or `.bashrc` file, but until then, the chaos continues.

To disable the prank, simply:

1. Remove the cron job:

```bash
crontab -e
# Remove the line containing mystery_background.sh
```

2. Remove the script from `.bashrc`:

```bash
nano ~/.bashrc
# Remove or comment out the line running the script
```

Once these steps are taken, the wallpaper will stop changing randomly, and the system will return to normal.

#### **Step 8: Making It Even More Diabolical**

Want to crank up the chaos even further? Here are some advanced ideas:

- **Random File Placement**: Along with changing the wallpaper, drop random files onto the desktop, such as text files with cryptic messages or bizarre images. The combination of new wallpapers and mysterious files will drive the user crazy.
  
- **Timed Pranks**: Set up different wallpapers for different times of day—normal images in the morning, but progressively weirder as the day goes on. By the evening, the wallpapers are fully bizarre.

- **Gradual Change**: Start with completely normal wallpapers and slowly introduce weirder and weirder ones over the course of days or weeks. This slow burn will create a growing sense of unease.

#### **Why This Works**

The **Mystery Background** prank works because it subtly interferes with something the user takes for granted—their desktop. Changing the wallpaper is a harmless action, but when done randomly and without explanation, it creates a sense of unease and confusion. The user will be left wondering whether they’ve triggered a bug, been hacked, or are simply losing their mind. It’s the perfect long-term prank that builds psychological tension without causing any real harm.

#### **In Conclusion**

**The Mystery Background** is a brilliant prank for those who love visual mischief. It’s subtle, random, and works over time to erode the victim’s sense of normalcy. By changing their wallpaper at unpredictable intervals, you create a prank that’s both confusing and hilarious, and the best part? It’s easily reversible when the fun is over.

Next up, we’ll dive back into terminal trickery with **Chapter 11: Shell Shenanigans — Fake Error Messages**, where we’ll craft convincing, fake error messages to make your victim think their system is on the brink of collapse.
