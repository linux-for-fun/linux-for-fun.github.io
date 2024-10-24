### **Chapter 4: The Talking Terminal**

You know what’s missing from your average, boring Linux terminal? A voice. Oh yes, my friend, let’s give the terminal a personality, a way to mock, spook, and confuse its unsuspecting user. Imagine a terminal that suddenly speaks out loud, delivering random, cryptic, or even snarky messages as the user types innocuous commands. The unsuspecting victim will be left wondering whether their system has developed a mind of its own.

Welcome to the Talking Terminal—a harmless but delightfully unsettling prank that uses text-to-speech technology to make the terminal talk back. Let’s dive in and breathe some life (or creepiness) into the command line.

#### **Step 1: Install `espeak` or `festival`**

To get the terminal talking, we’ll need a text-to-speech program. **`espeak`** is a lightweight option that’s perfect for this prank, but you can also use **`festival`** for more advanced features. Either way, they’ll both do the trick.

Let’s start by installing `espeak`:

```bash
sudo apt update
sudo apt install espeak
```

If you prefer `festival`, install it like this:

```bash
sudo apt install festival
```

Once installed, both tools allow us to convert text to speech and play it through the system’s audio output. Now, we’re ready to turn that terminal into a sarcastic, spooky, or just plain weird talking companion.

#### **Step 2: Triggering Speech with Common Commands**

The beauty of this prank is that we can make the terminal speak whenever the user runs a common command. Let’s choose a command that the user runs often—like `ls` or `cd`—and make the terminal speak after every execution.

To do this, we’re going to modify their `.bashrc` file (yes, again), creating aliases for these commands that execute their normal functionality but also run the `espeak` command to deliver a message.

Open the `.bashrc` file for editing:

```bash
nano ~/.bashrc
```

Add the following alias for the `ls` command:

```bash
alias ls='ls && espeak "Looking good, boss!"'
```

Now, every time the user runs `ls` to list the contents of a directory, the system will obediently show the files but will also speak the message “Looking good, boss!” through the speakers. It’s a harmless but funny surprise, and the more the user runs `ls`, the more they’ll hear the terminal talking to them.

#### **Step 3: Adding Random Messages**

Of course, we don’t want the terminal to say the same thing every time—that would get boring quickly. No, we need to add a little randomness to keep the confusion alive. We’ll create an array of possible messages, and each time the user runs a command, the system will randomly select one to speak.

Here’s an example of how to modify the `ls` command to deliver random speech:

```bash
alias ls='ls && phrases=("Looking good, boss!" "Why are you always listing stuff?" "Are you lost, human?" "I see dead files...") && espeak "${phrases[$RANDOM % ${#phrases[@]}]}"'
```

Now, when the user runs `ls`, the terminal will randomly select from a list of phrases, adding a delightful element of unpredictability. Sometimes it will compliment them, sometimes it will be snarky, and sometimes it will just confuse them.

#### **Step 4: Expanding the Prank to Other Commands**

Why stop at `ls`? Let’s make the terminal talk back for other common commands like `cd`, `pwd`, or even `sudo`. Here are a few more examples:

For `cd` (changing directories):

```bash
alias cd='cd && espeak "Where do you think you’re going?"'
```

For `sudo` (when they’re running something with admin privileges):

```bash
alias sudo='sudo && espeak "Oh, you think you’re in charge now?"'
```

For `pwd` (printing the current directory):

```bash
alias pwd='pwd && espeak "You are here. But where is here, really?"'
```

These aliases will give the impression that the system is paying attention to everything the user does and can’t help but make snarky comments along the way. The more the user interacts with their terminal, the more bizarre and hilarious the experience will become.

#### **Step 5: Using `zenity` for Pop-Up Messages**

If you want to take this prank a step further, you can combine the voice with visual pop-up messages using `zenity`, a tool that creates simple graphical dialog boxes. This way, the terminal can not only speak but also display ominous or absurd messages on the screen.

Start by installing `zenity`:

```bash
sudo apt install zenity
```

Now, let’s add a pop-up message to one of our aliases. Here’s an example that combines speech and a pop-up when the user runs `ls`:

```bash
alias ls='ls && espeak "What are you looking for?" && zenity --info --text="Did you really think you’d find it here?"'
```

Now, every time the user runs `ls`, the system will say, “What are you looking for?” and then display a pop-up message that reads, “Did you really think you’d find it here?” This adds a whole new layer of confusion and entertainment to the prank.

#### **Step 6: The Creepy Factor—Using Timed Messages**

Want to really freak someone out? Set up the terminal to deliver random spoken messages at timed intervals, even when the user isn’t actively typing commands. Imagine the user sitting quietly, working away, when suddenly their terminal blurts out, “I’m watching you...” at random. Spooky, right?

We can use `cron` to schedule random speech at odd intervals. Here’s how to set up a cron job that runs every 15 minutes and speaks a creepy message:

```bash
crontab -e
```

Add the following line:

```bash
*/15 * * * * espeak "I’m watching you..."
```

Now, every 15 minutes, the terminal will speak this eerie message, whether the user is actively working in the terminal or not. You can, of course, replace this with any message you like, depending on how freaked out you want them to be.

#### **Step 7: Disabling the Prank**

As always, every good prank should be reversible. To disable the talking terminal, simply remove the aliases from the `.bashrc` file and restore the original functionality of the commands. Here’s how:

1. Open the `.bashrc` file:

```bash
nano ~/.bashrc
```

2. Remove the lines where you added the aliases for `ls`, `cd`, `sudo`, etc.

3. Save and exit the file, then reload the `.bashrc`:

```bash
source ~/.bashrc
```

If you’ve set up a cron job for timed messages, don’t forget to remove that as well by editing the crontab:

```bash
crontab -e
# Remove the espeak cron job
```

Once these steps are complete, the system will return to its normal, silent self—no more talking back.

#### **Pro Tips for Maximum Effect**

Want to push this prank to its full potential? Here are a few additional ideas:

- **Customize the Messages**: Personalize the speech messages based on the target’s name, habits, or even their job. Imagine the terminal saying, “Oh, working late again, John?” or “I see you’ve been typing that same command for a while. Need help?”
  
- **Random Intervals**: For an extra creepy effect, set the speech to happen at completely random intervals, so the user never knows when the terminal will start talking. Use a cron job with a `sleep` command to create random timing.

- **Combine with Sound Effects**: Use system sounds or the `aplay` command to play random beeps, chimes, or ominous music whenever a certain command is run. This will add a whole new level of atmosphere to the prank.

#### **Why This Works**

The Talking Terminal prank taps into a deep-seated fear many people have: that their machines are watching them. By turning the terminal into a talking, responsive entity, you can create a sense of unease and confusion. But because it’s all lighthearted and easily reversible, the victim will eventually laugh it off—once they stop jumping every time the terminal speaks, that is.

#### **In Conclusion**

The Talking Terminal prank is a perfect blend of technical know-how and playful trickery. It’s simple to set up, endlessly customizable, and guaranteed to confuse your target. Whether you go for funny, creepy, or just plain weird, this prank will leave your victim wondering what the heck is going on with their terminal.

Next up, we’ll dive into the world of sudo with **Chapter 5: Sudon't Do That!**—a guide to messing with everyone’s favorite command: `sudo`.
