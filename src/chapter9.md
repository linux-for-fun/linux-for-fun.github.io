### **Chapter 9: Fortune’s Fool**

Ah, the classic `fortune` command—long hailed as a harmless source of quirky, often wise, sometimes absurd sayings. But what if we weaponized it? What if we turned those innocent little fortunes into moments of confusion, paranoia, or even existential dread? Imagine your victim typing a command and, seemingly out of nowhere, receiving a cryptic or snarky fortune that leaves them questioning not just their terminal, but their very sanity.

Welcome to **Fortune’s Fool**, where we’ll use the `fortune` command to randomly insert perplexing messages into their everyday terminal interactions.

#### **Step 1: Installing `fortune`**

First, we’ll need to ensure that `fortune` is installed on the target system. Most Linux distributions have it available in their repositories. To install it on Ubuntu, simply run:

```bash
sudo apt update
sudo apt install fortune
```

Once installed, `fortune` will be able to generate random messages from a large collection of sayings, jokes, and proverbs. However, in our hands, this innocent tool is about to become an agent of chaos.

#### **Step 2: Randomly Inserting Fortunes into Commands**

We’ll start by modifying the `.bashrc` file to randomly insert fortunes into everyday commands. We can add a simple condition that triggers a fortune whenever the user runs common commands like `ls`, `cd`, or `mkdir`.

Open the `.bashrc` file:

```bash
nano ~/.bashrc
```

Now, we’ll modify the aliases for these commands to sometimes deliver a fortune. Here’s how we can do it for `ls`:

```bash
alias ls='[ $((RANDOM % 5)) -eq 0 ] && fortune || ls'
```

This command gives a 1 in 5 chance that every time the user runs `ls`, instead of listing files, they’ll receive a random fortune. If the condition isn’t met, `ls` will behave as usual. You can apply this same logic to other frequently used commands.

Let’s add a few more:

```bash
alias cd='[ $((RANDOM % 5)) -eq 0 ] && fortune || cd'
alias mkdir='[ $((RANDOM % 5)) -eq 0 ] && fortune || mkdir'
alias pwd='[ $((RANDOM % 5)) -eq 0 ] && fortune || pwd'
```

Now, there’s a small but ever-present chance that when they navigate through directories, list files, or even create folders, they’ll receive a fortune instead of the expected result. This subtle randomness will keep them on edge.

#### **Step 3: Customizing Fortunes for Maximum Confusion**

The default fortunes are quirky, but we want to take it a step further by adding our own confusing, ominous, or downright absurd messages. We can do this by creating custom fortune databases.

Create a directory for custom fortunes:

```bash
mkdir ~/.fortunes
```

Now, create a text file for your custom fortunes. For example, let’s call it `prank_fortunes`:

```bash
nano ~/.fortunes/prank_fortunes
```

Inside this file, write a series of bizarre, cryptic, or humorous messages. Each fortune must end with a line containing just a single `%` character, which separates the fortunes. Here’s an example:

```
The system is watching you. Always.
%
You have angered the machine. Be cautious.
%
Something strange is happening, but it’s best not to ask questions.
%
Oops, did you mean to do that? The consequences are... unforeseen.
%
Congratulations! You have just deleted an important file. Or did you?
%
```

Once you’ve filled the file with custom messages, you’ll need to compile the fortune file so `fortune` can use it:

```bash
strfile ~/.fortunes/prank_fortunes
```

Now, you can tell the `fortune` command to use your custom fortune file by adding it to the aliases:

```bash
alias ls='[ $((RANDOM % 5)) -eq 0 ] && fortune ~/.fortunes/prank_fortunes || ls'
```

Repeat this process for any other commands you want to target.

#### **Step 4: Timing the Fortunes with Cron**

For an extra layer of mischief, we can schedule random fortunes to appear at unexpected times using `cron`. Imagine your victim is working peacefully, and suddenly, the terminal blurts out an eerie fortune at a random moment.

Set up a cron job like this:

```bash
crontab -e
```

Add the following line to execute a fortune from your custom file every 30 minutes:

```bash
*/30 * * * * fortune ~/.fortunes/prank_fortunes
```

This will cause a fortune to appear in the terminal every half-hour, even if the user isn’t running any commands. The randomness of these timed messages will create a creeping sense of unease, as if the system is alive and sending cryptic messages of its own accord.

#### **Step 5: Integrating Fortunes with Other Pranks**

**Fortune’s Fool** works best when combined with other pranks. You can integrate fortunes with **Bash Roulette**, **Terminal Games**, or even **The Talking Terminal**. For instance, after a user is forced to play a game of **Tetris**, they could be greeted with a fortune saying:

```
You’ve won the game, but at what cost?
```

Or, after a mysterious reboot triggered by **Bash Roulette**, the terminal could display:

```
Reboot complete. The system knows more than it lets on.
```

Here’s how you might combine fortunes into a **Bash Roulette** script:

```bash
#!/bin/bash

# Define the random chance (1 in 5)
roulette=$((RANDOM % 5))

if [ $roulette -eq 0 ]; then
    # Randomly choose a prank
    prank=$((RANDOM % 5))

    case $prank in
        0)
            echo "Surprise! Launching Tetris."
            tint
            ;;
        1)
            echo "Rebooting terminal... or is it?"
            sleep 3
            clear
            fortune ~/.fortunes/prank_fortunes
            ;;
        2)
            echo "Here’s some wisdom: "
            fortune ~/.fortunes/prank_fortunes
            ;;
        3)
            echo "Beware... you have angered the terminal."
            espeak "You have angered the terminal."
            ;;
        4)
            echo "Playing a sound just for fun."
            aplay /usr/share/sounds/alsa/Front_Center.wav
            fortune ~/.fortunes/prank_fortunes
            ;;
    esac
else
    # Run the command normally
    "$@"
fi
```

In this version, every time a prank is triggered, it also delivers a random fortune from your custom file, adding a layer of mystique to every action.

#### **Step 6: Escaping the Fortune Trap**

As always, you need to leave a way for the victim to escape the prank once they’ve had enough. To stop the fortunes from appearing, the user can simply remove the aliases from their `.bashrc` file or disable the cron job.

To disable the cron job:

```bash
crontab -e
# Remove the line containing the fortune command
```

To remove the aliases, they can open the `.bashrc` file and comment out the fortune-related aliases:

```bash
nano ~/.bashrc
# Comment out or remove the fortune aliases
```

After that, they can reload the `.bashrc`:

```bash
source ~/.bashrc
```

Once these changes are made, the terminal will return to its normal, non-fortune-spouting self. But until then, they’ll be bombarded with cryptic wisdom every time they least expect it.

#### **Step 7: Making It Even More Evil**

For maximum confusion, you can make the fortunes progressively weirder or more ominous. Start with harmless jokes or silly sayings, but gradually introduce darker, more cryptic messages, making the user feel like something more sinister is going on. By the time they realize it’s a prank, they’ll have gone through a rollercoaster of emotions.

For example:
1. **Day 1**: Harmless jokes: “Why don’t programmers like nature? It has too many bugs.”
2. **Day 2**: Mild confusion: “The files you seek are not where you think.”
3. **Day 3**: Paranoia sets in: “The system knows. The system watches.”

By building this escalation into your custom fortune file, you can prolong the prank and make the experience truly memorable.

#### **Why This Works**

**Fortune’s Fool** works because it plays on the user’s expectation that the terminal is a serious, predictable tool. By inserting random, cryptic messages into their workflow, you create an atmosphere of confusion and mystery. The user will begin to wonder if they’ve triggered a hidden Easter egg, installed malware, or angered some digital deity. The randomness and subtlety make it a long-lasting and highly effective prank.

#### **In Conclusion**

**Fortune’s Fool** is a masterclass in psychological warfare. It’s subtle, customizable, and endlessly creative. By inserting random fortunes into everyday commands, you turn the user’s terminal into a cryptic oracle that confounds and amuses in equal measure. And, as with all great pranks, it’s easily reversible—once they figure out what’s going on.

Next, we’ll dive into a more visual prank: **Chapter 10: The Mystery Background**, where we’ll change desktop wallpapers at random intervals, slowly driving your victim to madness.
