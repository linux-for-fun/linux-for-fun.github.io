### **Chapter 2: The Phantom Printer**

Ah, printers. The eternal bane of every sysadmin’s existence. They never work when you need them to, they jam at the worst moments, and let’s not even get started on the arcane rituals sometimes required to get a wireless connection. But today, we’re not here to solve printer problems. Oh no, my dear reader, we’re here to create *new* ones. Introducing: The Phantom Printer.

Imagine this: your target’s machine starts sending print jobs to a printer that doesn’t exist, at completely random intervals. One moment everything is peaceful, the next, the system is queuing up a mysterious document with no clear explanation. The best part? It’s all a figment of their imagination—there is no printer, no actual files. Just confusion. Delicious, beautiful confusion.

Let’s begin.

#### **Step 1: Install CUPS**

First things first, we need to ensure that the system has **CUPS** (the Common Unix Printing System) installed. Most Linux systems come with CUPS already set up, but just in case, it’s easy enough to install.

On Ubuntu, run:

```bash
sudo apt update
sudo apt install cups
```

CUPS is the printing service that manages all printer-related activities on the system. We’ll use it to create the illusion of a working printer that doesn’t actually exist. *How delightful.*

#### **Step 2: Create a Fake Printer**

Now that CUPS is installed, it’s time to create our phantom printer. A printer that shows up in the system but isn’t connected to any actual hardware. It’s a ghost printer, floating in the ether, waiting to haunt its unsuspecting user.

Here’s how we add a fake printer:

1. Open a browser and navigate to the CUPS web interface, which can be accessed locally via:

```
http://localhost:631
```

2. Click on **Administration** and then **Add Printer**. If prompted, log in with your admin credentials.
3. In the list of devices, select **LPD/LPR Host or Printer**.
4. Name your phantom printer something innocuous but slightly ominous, like `Phantom_Printer` or `MysteryPrint`. Something that will only deepen their confusion.
5. Continue through the setup process, but when it asks for a driver, select **Generic**. It won’t matter, because the printer doesn’t really exist!
6. Finish the setup, and voilà, you’ve created a printer that’s destined to haunt their print queue.

#### **Step 3: The Ghost Print Job Script**

Now for the main event: random print jobs. We’re going to write a small shell script that sends random files or nonsense to the printer at random intervals. The beauty of this is that the target won’t notice until they check their printer queue and see it filling up with mysterious jobs.

Let’s create a script called `phantom_printer.sh`:

```bash
#!/bin/bash

# Define some fake document names to add confusion
documents=("Project_X_report.pdf" "Invoice_2039.txt" "Presentation_Draft.pptx" "Confidential_Memo.docx")

# Randomly select a document to "print"
random_doc=${documents[$RANDOM % ${#documents[@]}]}

# Send the random job to the phantom printer
lp -d Phantom_Printer $random_doc

# Wait for a random period (between 1 and 60 minutes)
sleep_time=$((RANDOM % 3600))
sleep $sleep_time
```

This script randomly selects one of the fake document names and sends it to the phantom printer at intervals ranging from a few seconds to an hour. The randomness is key—it keeps them guessing when the next ghost print job will strike.

#### **Step 4: Automating the Chaos with Cron**

The fun doesn’t stop here. We want this script to run automatically in the background, without needing to manually start it every time. Enter **cron**, our favorite task scheduler.

To set up our phantom printer to haunt them all day, we’ll add this script to their cron jobs:

1. Open the cron editor:

```bash
crontab -e
```

2. Add the following line to execute the `phantom_printer.sh` script at system startup and every 30 minutes after that:

```bash
@reboot /path/to/phantom_printer.sh &
*/30 * * * * /path/to/phantom_printer.sh &
```

Now, every time the system starts, the script will begin its reign of terror, sending print jobs at random intervals to the phantom printer. The user will occasionally check their printer queue and see files mysteriously appearing. 

#### **Step 5: What Will They See?**

Once the script is up and running, here’s what your target will experience:

1. They’ll be happily going about their day when—*boom*—a print job appears. Maybe they have notifications enabled, so they get a popup like “Project_X_report.pdf has been sent to Phantom_Printer.”
   
2. Naturally, they’ll check their printer queue, only to see the mysterious file sitting there, waiting to be printed. But the printer? Nowhere to be found. Confusion begins to creep in.

3. Over the course of the day, more random files appear. Each time, they grow more perplexed, trying to figure out where the print jobs are coming from. Maybe they’ll even start unplugging things, thinking they’ve been hacked.

4. The real beauty comes when they finally give up and try to remove the phantom printer—only to realize that it doesn’t seem to be connected to anything. “How did this printer even get here?” they’ll wonder. “Is my system haunted?”

#### **Step 6: The Grand Finale—Let Them In On the Joke**

At some point, you’ll have to reveal your masterful prank. But how you do it is entirely up to you. Here are a few delightful ways to pull back the curtain:

- **The Printer That Never Was**: Leave a sticky note or send a message with a cryptic hint, like: “Perhaps the printer was inside you all along...” Let them puzzle over it until they figure it out.
  
- **The Big Reveal**: If you’re feeling merciful, you can casually mention, “Oh, have you tried checking your cron jobs lately?” and watch the realization dawn.

- **Double Down**: Instead of revealing the prank, add a second phantom printer and let the chaos continue. Make them think they’ve removed one, only for another to appear. Infinite printers, infinite confusion.

#### **Pro Tips for the Phantom Printer**

Want to take the Phantom Printer prank to the next level? Here are some devilish ways to amplify the fun:

- **Add More Fake Printers**: Set up multiple phantom printers, each with more confusing or nonsensical names. Bonus points if you name them things like “Shadow_Printer,” “GhostQueue,” or “SpookyPrint.”

- **Involve Real Printers**: If your target is already using a real printer, configure the phantom printer to be set as the default. Watch as their documents mysteriously vanish into the phantom print queue instead of their real printer.

- **Fake Error Messages**: Combine this prank with some fake error pop-ups. Use a tool like `zenity` to generate random error messages like, “The Phantom Printer requires a sacrifice. Please insert more paper.” It’ll drive them *mad*.

#### **How to Reverse the Prank**

As always, every good prank needs an off switch. To end the Phantom Printer’s reign of terror, simply remove the cron job that launches the script:

```bash
crontab -e
# Remove the lines with the phantom_printer.sh script
```

Then, you can either delete the phantom printer through the CUPS web interface or leave it there as a haunting reminder of the chaos you’ve sown.

To delete the printer, go back to `http://localhost:631`, select **Printers**, find your phantom printer, and click **Delete Printer**. Simple as that.

#### **Why This Works**

The brilliance of the Phantom Printer prank lies in its subtlety. Printers are notoriously unreliable, so when a mysterious print job appears, the user will naturally assume it’s just the system being its usual annoying self. But as the jobs keep coming—seemingly out of nowhere—the confusion builds, eventually spiraling into full-blown paranoia.

They’ll wonder if they’ve been hacked, if there’s a hidden printer somewhere in the building, or if the system is cursed. The fact that the print jobs don’t actually go anywhere only adds to the frustration. They’ll search high and low for the source of the phantom prints, but alas, the only real culprit is the one grinning behind the screen—you.

#### **In Conclusion**

The Phantom Printer is a slow-burn prank that drives your victim to the edge without ever truly harming anything. It’s a perfect example of how to exploit the everyday frustrations of technology and turn them into something hilariously absurd. And, as always, it’s easily reversible once the fun is over.

Now that we’ve thoroughly spooked the printers, get ready for the next trick. In Chapter 3, we’re going to force some real games into the terminal—games that *never stop*.
