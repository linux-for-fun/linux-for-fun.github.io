### **Chapter 1: Login Loop of Doom (But Not Really)**

Oh, the sweet, sweet joy of watching someone attempt to log into their system, only to be greeted with an endless loop of failure! But remember, dear reader, we’re not here to break their spirit, just to toy with their patience—ever so delicately. Enter the *Login Loop of Doom*: a harmless prank that will trap your victim in a perpetual cycle of login attempts, making them wonder if they’ve stumbled into some twisted tech nightmare. But no fear—there’s always a way out. The trick is knowing how to set the trap just right.

Let’s begin, shall we?

#### **The Setup: Modifying `.bashrc` or `.bash_profile`**

The magic of this prank lies in one of the most innocent and unassuming files on any Linux system: the `.bashrc` or `.bash_profile`. These files are automatically executed every time a user logs into their shell. Normally, they’re used for setting environment variables, loading aliases, or running startup scripts. But for us? It’s the perfect place to lay our little trap.

**Step 1: Access Your Target’s Shell Config File**

First, you need access to the user’s `.bashrc` or `.bash_profile` file. Typically, you’ll find these in the user’s home directory (`/home/username`). If you’re pranking yourself for practice, it’s as simple as running:

```bash
nano ~/.bashrc
```

or:

```bash
nano ~/.bash_profile
```

(Note: `.bashrc` is more commonly used in Ubuntu for non-login shells, while `.bash_profile` gets executed in login shells. But hey, either one will do the trick depending on how your target typically logs in.)

**Step 2: Insert the Login Loop of Doom**

Now, here’s where we unleash a bit of chaos. What we want is to prevent the user from ever reaching their terminal by looping them back to the login prompt. A simple way to achieve this is by adding a line that will force an immediate logout every time the `.bashrc` (or `.bash_profile`) is executed.

Here’s a neat trick:

```bash
while true; do
    clear
    echo "Login failed. Please try again."
    sleep 1
done
```

Add this innocent-looking loop to the bottom of their `.bashrc` file. This little gem will immediately clear the screen, print an ominous “Login failed. Please try again.” message, and repeat forever. The user will log in, see this, and—just like that—get kicked back into oblivion.

**Step 3: Save the File and Exit**

After inserting your diabolical loop, save the file (`Ctrl + O` to write, `Ctrl + X` to exit if you’re using nano). Now, wait for your unsuspecting victim to log in and be consumed by the loop of doom.

#### **What Will They See?**

Now, here’s the fun part: What exactly happens when they try to log in? Let me paint you a picture.

Your victim, blissfully unaware, enters their username and password like they do every day. They’re probably thinking about how much work they have to do or, better yet, how everything is going smoothly for once. But then... the screen flashes. Instead of their beautiful command line, they’re greeted with:

```
Login failed. Please try again.
```

Huh? Maybe they mistyped their password? They’ll try again, of course. Enter password. *Boom*—same message. Now the real fun begins.

As they start to sweat, they’ll try everything: logging out and back in, rebooting the system, maybe even Googling on another device for “Ubuntu login issues.” Little do they know, the answer is hiding in plain sight—right in their `.bashrc` file.

#### **Giving Them an Escape: The Secret Exit Key**

Of course, we’re not monsters (well, not *total* monsters). Every prank should have a way out. Otherwise, where’s the fun when they realize it’s you behind the madness? Let’s give them a chance to escape—*if* they’re clever enough to figure it out.

We can modify our script to include a hidden exit condition. For instance, let’s allow them to break the loop if they type a specific word or press a particular key. Something subtle, like a secret code, that only you know about.

Here’s an updated version of the script with a hidden escape key:

```bash
while true; do
    clear
    echo "Login failed. Please try again."
    echo "Hint: Say the magic word."
    read input
    if [ "$input" == "letmein" ]; then
        break
    fi
    sleep 1
done
```

This version adds a prompt asking the user to “Say the magic word.” If they happen to type "letmein," the loop will break, and they’ll regain access to their precious terminal. Of course, it’s entirely up to you whether you want to give them that hint. Maybe you leave it out entirely for a few hours of extra confusion before revealing the secret!

#### **How to Reverse the Prank**

Once your victim has suffered long enough, it’s time to end the charade and let them back into their system. This part is crucial—remember Rule #2: All pranks must be reversible.

If they haven’t figured it out themselves, you can either:
- Log in with an administrator account and remove the prank from their `.bashrc` file.
- Send them a cryptic message telling them to check their `.bashrc`.
- Or if you’re feeling particularly devilish, wait for them to beg for help!

To remove the loop, simply access the `.bashrc` again and delete the lines you added:

```bash
nano ~/.bashrc
# Remove the loop lines, save, and exit.
```

Once that’s done, everything will return to normal—*as if nothing ever happened*. Ah, the beauty of temporary chaos.

#### **Pro Tips for Maximum Effect**

Want to push this prank to the next level? Oh, I knew you would. Here are a few extra twists you can throw in for extra laughs:

- **Add Random Messages**: Instead of always showing “Login failed. Please try again,” mix it up! You can create a variety of random failure messages like, “Authentication denied,” or “Access to root required,” or even “System compromised!” Keep them on their toes, wondering just how bad the situation is.

- **Increase the Delay**: Set the sleep timer to a higher value, so the victim has to wait 5, 10, or even 30 seconds between each failed attempt. The more they have to wait, the more frustrated they’ll get, thinking it’s a system error.

- **Mess with the Hint**: If you’re giving them a hint for the exit word, make it something cryptic or weird, like “Only_the_chosen_may_pass” or “42_is_the_answer”. Watch them scratch their heads trying to decode your mind games.

- **Timed Break**: You could set the loop to automatically break after a certain amount of time, giving them a temporary sense of relief—before the prank triggers again on their next login.

#### **Why This Works**

You see, this prank is a beautiful mix of simplicity and psychological warfare. By using something as basic as a loop in the `.bashrc` file, you can create an illusion of system failure. Your victim will be stuck in a seemingly endless login loop, convinced that something has gone horribly wrong with their beloved Ubuntu system. And yet, there’s no real damage. No files lost. No data corrupted. Just pure, unadulterated confusion.

Isn’t it marvelous?

#### **In Conclusion**

The Login Loop of Doom is just the start of our journey into the land of Linux pranks. It’s subtle, effective, and most importantly—reversible. You’ve made your victim panic, question their sanity, and hopefully laugh at the absurdity of it all. 

So go on, my fellow trickster, and let chaos reign. The next chapter awaits, where we dive into the magical world of phantom printers. But remember—play nice, and always give them a way out. Or not.
