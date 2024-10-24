### **Chapter 8: Bash Roulette**

Ah, the terminal—so reliable, so predictable. You type a command, it does what you expect. But what if every time you typed something, you weren’t quite sure what would happen? Maybe your command works as intended. Maybe it launches a game of **Tetris** instead. Or, perhaps, it just prints a cryptic message or plays a sound. Welcome to **Bash Roulette**, where every command is a gamble, and the terminal is no longer your obedient servant but a mischievous, unpredictable trickster.

In this chapter, we’ll craft a script that injects randomness into the user’s terminal experience, turning ordinary commands into a game of chance. Let the chaos begin.

#### **Step 1: Setting Up the Bash Roulette Script**

First, we need to create a script that will randomly decide whether a command runs normally or triggers a prank. This will be the heart of **Bash Roulette**. Let’s start by writing a simple version that randomly chooses between executing the user’s command and launching something unexpected.

Create a new file called `bash_roulette.sh`:

```bash
nano ~/bash_roulette.sh
```

Inside this script, we’ll define the roulette behavior. For now, let’s keep it simple: when the user runs a command, the script will randomly decide whether to execute it normally or trigger a surprise.

Here’s the basic version:

```bash
#!/bin/bash

# Define the random chance (1 in 5)
roulette=$((RANDOM % 5))

if [ $roulette -eq 0 ]; then
    # Surprise! Launch a game of Tetris
    echo "You hit the jackpot! Playing Tetris instead."
    tint
else
    # Otherwise, run the command as normal
    "$@"
fi
```

This script gives the user a 1 in 5 chance of their command being hijacked to launch **Tetris**. The other four times, their command will run normally. Save the file and make it executable:

```bash
chmod +x ~/bash_roulette.sh
```

#### **Step 2: Making the Script Affect All Commands**

Now that we’ve got the basic roulette behavior, let’s make sure it applies to all commands the user runs. We can do this by modifying their `.bashrc` file to alias every command to pass through our `bash_roulette.sh` script.

Open the `.bashrc` file:

```bash
nano ~/.bashrc
```

Add the following line to alias all commands through the roulette script:

```bash
alias *='~/bash_roulette.sh "$@"'
```

This ensures that every command the user types—whether it’s `ls`, `cd`, or `cat`—gets passed through **Bash Roulette**. Every action becomes a gamble.

#### **Step 3: Expanding the Prank Possibilities**

Why stop at **Tetris**? Let’s expand the list of possible pranks, so that each command could trigger a variety of surprises. Here’s an updated version of the script with a few more mischievous options:

```bash
#!/bin/bash

# Define the random chance (1 in 5)
roulette=$((RANDOM % 5))

if [ $roulette -eq 0 ]; then
    # Randomly choose a prank to play
    prank=$((RANDOM % 4))

    case $prank in
        0)
            echo "Surprise! Launching Tetris."
            tint
            ;;
        1)
            echo "Whoa, slow down! Rebooting your terminal..."
            sleep 3
            clear
            ;;
        2)
            echo "Random wisdom for you: "
            fortune
            ;;
        3)
            echo "Beware... you have angered the terminal."
            espeak "You have angered the terminal."
            ;;
    esac
else
    # Run the command normally
    "$@"
fi
```

Now, every time a command is run, the user faces a 1 in 5 chance of triggering one of the following pranks:
- **Tetris**: Launches the game **Tetris**.
- **Terminal reboot**: Clears the terminal, giving the illusion that it’s rebooting.
- **Fortune**: Displays a random fortune using the `fortune` command.
- **Angry terminal**: The terminal talks back with an ominous message using `espeak`.

You can, of course, add as many different pranks as you want by expanding the `case` block with more creative ideas.

#### **Step 4: Adding Sound Effects for Extra Fun**

To add another layer of confusion, let’s introduce sound effects using the `aplay` or `espeak` commands. This will make the terminal not only unpredictable but also noisy. For example, you can make the terminal play a creepy sound when a command fails the roulette.

Let’s add this to the script:

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
            ;;
        2)
            echo "Here’s some wisdom: "
            fortune
            ;;
        3)
            echo "Beware... you have angered the terminal."
            espeak "You have angered the terminal."
            ;;
        4)
            echo "Playing a sound just for fun."
            aplay /usr/share/sounds/alsa/Front_Center.wav
            ;;
    esac
else
    # Run the command normally
    "$@"
fi
```

Now, one of the pranks will play a sound using the `aplay` command, making the terminal even more unpredictable and annoying.

#### **Step 5: Cron Jobs for Periodic Chaos**

Want to add another layer of randomness? Set up a cron job that periodically triggers **Bash Roulette** at random times, even when the user isn’t actively typing commands.

Create a new cron job like this:

```bash
crontab -e
```

Add the following line to execute the script every 15 minutes:

```bash
*/15 * * * * ~/bash_roulette.sh "echo Random terminal event!"
```

Now, every 15 minutes, the script will run on its own, surprising the user with random events. They’ll be sitting there, minding their own business, when suddenly their terminal talks back, clears itself, or plays a sound. Pure chaos.

#### **Step 6: Escaping the Roulette**

Eventually, your victim will want to escape the madness. To disable the roulette and restore their terminal to normal, they’ll need to remove the alias from the `.bashrc` file.

Here’s how to disable the prank:

1. Open the `.bashrc` file:

```bash
nano ~/.bashrc
```

2. Remove or comment out the alias line:

```bash
# alias *='~/bash_roulette.sh "$@"'
```

3. Save the file and reload the shell:

```bash
source ~/.bashrc
```

Once the alias is removed, the terminal will return to normal behavior, and commands will run as expected again.

#### **Step 7: Making It Even More Evil**

If you want to make **Bash Roulette** truly diabolical, here are a few extra ideas to take the prank to the next level:

- **Silent Sabotage**: Instead of giving clear messages when a prank triggers, make some pranks silent, so the user doesn’t even know something weird happened until later (e.g., secretly editing files or changing directory locations).
  
- **File Corruption Warnings**: Add a prank that pretends to corrupt important files. For example, you can display a message like, “Warning: Critical system file deleted.” Of course, it won’t actually delete anything, but the user won’t know that.

- **Command History Editing**: Create a prank that modifies the user’s command history, so they can’t see the commands they actually typed, adding another layer of paranoia.

#### **Why This Works**

The beauty of **Bash Roulette** is in its randomness. The unpredictability makes it unsettling for the victim, as they never know what will happen when they execute a command. One moment it’s business as usual, the next they’re playing **Tetris** or hearing ominous sounds from their terminal. It turns the most mundane actions into a source of anxiety, and because it’s all done through harmless pranks, the user can’t help but laugh once they figure out what’s going on.

#### **In Conclusion**

**Bash Roulette** is a perfect blend of technical trickery and psychological games. By introducing randomness into the terminal experience, you transform the user’s interaction with the system into a high-stakes game of chance. And as with all great pranks, it’s easily reversible, ensuring that the fun leaves no lasting damage—just a good laugh and a confused victim.

Next up, we’ll dive into another sneaky way to mess with your victim’s head: **Chapter 9: Fortune’s Fool**, where we use the `fortune` command to randomly insert snarky, confusing, or downright cryptic messages into their terminal sessions.
