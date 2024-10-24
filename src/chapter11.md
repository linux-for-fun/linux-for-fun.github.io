### **Chapter 11: Shell Shenanigans—Fake Error Messages**

Nothing sends chills down the spine of an unsuspecting user like the sight of an ominous error message. Imagine the horror as they type a harmless command, only to be greeted by a cryptic warning about "system failure," "critical file corruption," or "data loss." Of course, it’s all fake—just a cleverly placed prank designed to stir up confusion and anxiety.

In **Shell Shenanigans**, we’ll explore how to create convincing, fake error messages that will make your victim think their system is on the verge of collapse. These messages won’t do any real harm, but they’ll certainly make your target sweat.

#### **Step 1: Crafting the Fake Error Messages**

The easiest way to create fake error messages is by using simple `echo` commands combined with strategically placed conditions in their `.bashrc` file. Let’s start by creating some basic error messages that will appear randomly when the user runs common commands.

Open the `.bashrc` file:

```bash
nano ~/.bashrc
```

Add the following line to create an alias for `ls` that occasionally prints a fake error message:

```bash
alias ls='[ $((RANDOM % 5)) -eq 0 ] && echo "ERROR: Filesystem corruption detected. Running fsck..." && sleep 2 || ls'
```

This command gives a 1 in 5 chance that every time the user runs `ls`, they’ll see a scary message like:

```
ERROR: Filesystem corruption detected. Running fsck...
```

The system will pause for two seconds (to make the error seem more real) and then run the `ls` command normally. The user will be left wondering whether something serious is happening to their system.

#### **Step 2: Creating More Convincing Errors**

Let’s add some more complexity to make the error messages look even more realistic. We can add multi-line messages, delays, and even fake progress bars to give the impression that the system is trying to fix the problem.

Here’s how to modify the alias to make the error message more dramatic:

```bash
alias ls='[ $((RANDOM % 5)) -eq 0 ] && echo -e "ERROR: Critical filesystem failure.\nAttempting automatic recovery..." && sleep 3 && echo "[####        ] 40% complete" && sleep 2 && echo "[##########  ] 80% complete" && sleep 2 && echo "Recovery successful." && ls || ls'
```

Now, when the fake error triggers, the user will see something like this:

```
ERROR: Critical filesystem failure.
Attempting automatic recovery...
[####        ] 40% complete
[##########  ] 80% complete
Recovery successful.
```

This will leave them panicked at first, but then relieved when they see the “recovery” was “successful.” The trick is to make the error look just plausible enough that they won’t immediately think it’s a prank.

#### **Step 3: Introducing Random Fake Errors Across Commands**

To make this prank more effective, we should target multiple commands. The more frequently the user encounters fake errors, the more paranoid they’ll become. Let’s add some fake errors to common commands like `cd`, `rm`, and `sudo`.

Here’s how to modify `cd` with a fake error message:

```bash
alias cd='[ $((RANDOM % 4)) -eq 0 ] && echo "ERROR: Directory access denied. Possible disk corruption." && sleep 2 || cd'
```

For `rm`, we can make it even scarier by suggesting that the system is deleting critical files:

```bash
alias rm='[ $((RANDOM % 4)) -eq 0 ] && echo "WARNING: Attempting to remove system files. This action cannot be undone." && sleep 2 || rm'
```

And for `sudo`, let’s make the terminal seem like it’s denying superuser privileges:

```bash
alias sudo='[ $((RANDOM % 4)) -eq 0 ] && echo "ERROR: Insufficient permissions to execute command. Contact system administrator." && sleep 2 || sudo'
```

With these modifications, your victim will encounter random fake errors across multiple commands, increasing their confusion and making the prank more believable.

#### **Step 4: Making the Errors Interactive with `zenity`**

For an extra layer of confusion, we can make use of **`zenity`**, a tool that allows us to create graphical pop-up messages from the command line. This is particularly effective because most users don’t expect graphical errors to come from terminal commands.

First, install `zenity`:

```bash
sudo apt install zenity
```

Now, let’s add some pop-up error messages to our prank. We’ll modify the `ls` command to show a pop-up error before displaying the normal output:

```bash
alias ls='[ $((RANDOM % 5)) -eq 0 ] && zenity --error --text="Critical error: Filesystem corruption detected." && sleep 2 && ls || ls'
```

With this alias, the user will get a graphical pop-up that looks like a real system error. They’ll be forced to click “OK” before the normal `ls` output appears. This combination of graphical and terminal-based errors will make the prank seem even more authentic.

#### **Step 5: The Ultimate Fake Error—Kernel Panic**

If you really want to push the victim over the edge, you can simulate a fake kernel panic. This is the Linux equivalent of the Blue Screen of Death, and seeing it will send any user into a panic. Thankfully, we can simulate one using a clever script.

First, create a new script called `fake_kernel_panic.sh`:

```bash
nano ~/fake_kernel_panic.sh
```

Here’s what the script should look like:

```bash
#!/bin/bash

# Clear the screen to simulate a full-screen panic
clear

# Display the fake kernel panic message
echo "Kernel panic - not syncing: Fatal exception"
sleep 1
echo "CPU: 0 PID: 1 Comm: init Not tainted 5.4.0-42-generic #46~18.04.1-Ubuntu"
sleep 1
echo "Hardware name: Fake Machine Model (Fake CPU, Genuine Linux)"
sleep 1
echo "[  0.000000] Call Trace:"
sleep 1
echo "[  0.000001] Kernel panic - not syncing: Fatal exception"
sleep 1
echo "[  0.000002] Rebooting in 10 seconds..."
sleep 10

# Exit the fake panic
clear
echo "Panic resolved. System recovered."
```

Make the script executable:

```bash
chmod +x ~/fake_kernel_panic.sh
```

You can trigger this fake kernel panic randomly by adding it to a command like `sudo`:

```bash
alias sudo='[ $((RANDOM % 10)) -eq 0 ] && ~/fake_kernel_panic.sh || sudo'
```

Now, every so often, running `sudo` will trigger this fake kernel panic, making the user believe their system has crashed. After 10 seconds, the “panic” will resolve itself, leaving the user wondering what just happened.

#### **Step 6: Making It Even More Realistic with `dmesg`**

To add even more authenticity to your fake errors, you can pipe fake log messages into `dmesg`, the command that shows kernel and system logs. Users often check `dmesg` when they see errors, so why not fill it with fake error messages?

First, create a script that injects fake logs into `dmesg`:

```bash
nano ~/fake_dmesg.sh
```

Add the following lines to simulate system errors:

```bash
#!/bin/bash

# Inject fake error messages into dmesg
dmesg -n1
echo "[  0.000001] EXT4-fs error (device sda1): ext4_find_entry:1455: inode #2: comm bash: reading directory lblock 0"
echo "[  0.000002] EXT4-fs (sda1): Remounting filesystem read-only"
```

Make it executable:

```bash
chmod +x ~/fake_dmesg.sh
```

Now, you can trigger this fake log injection from any command, like so:

```bash
alias cd='[ $((RANDOM % 5)) -eq 0 ] && ~/fake_dmesg.sh && cd || cd'
```

Whenever the alias is triggered, the fake log messages will be injected into `dmesg`, making it seem like there’s a real system issue happening. If your victim checks `dmesg` for more information, they’ll see these convincing error logs.

#### **Step 7: Disabling the Fake Errors**

As always, once the prank has run its course, you’ll want to leave your victim a way to disable the fake errors and return to normal. They can do this by removing the aliases from the `.bashrc` file.

To disable the fake errors:

1. Open the `.bashrc` file:

```bash
nano ~/.bashrc
```

2. Remove or comment out the alias lines that contain the fake errors.

3. Save the file and reload the `.bashrc`:

```bash
source ~/.bashrc
```

Once the aliases are removed, the system will return to its normal, error-free state—though your victim will likely be on edge for a while longer, wondering if the errors will return.

#### **Step 8: Making It Even More Evil**

If you want to push the prank to its limits, here are some extra ideas:

- **Gradual Esc

alation**: Start with small, harmless fake errors and gradually increase the intensity and frequency. Begin with small warnings, then escalate to kernel panics and filesystem corruption messages.

- **Timed Pranks**: Use `cron` to trigger fake errors at specific times of day, making it seem like the errors are tied to specific system processes or events.

- **Interactive Errors**: Use `zenity` to create interactive error messages that force the user to click buttons like “Retry” or “Abort,” even though neither option makes a difference.

#### **Why This Works**

The **Shell Shenanigans—Fake Error Messages** prank works because it plays on the user’s trust in the system. Error messages are usually serious, and seeing them pop up unexpectedly creates a sense of panic and urgency. By making the errors look real and introducing randomness, you keep the victim on edge, wondering whether their system is about to break.

#### **In Conclusion**

**Shell Shenanigans** is a highly effective prank that preys on the user’s trust in their system. By creating realistic, fake error messages, you can send your victim into a spiral of confusion, frustration, and maybe even panic—all without causing any real harm. Just remember to reverse the prank when the fun is over, and enjoy watching your victim squirm in the meantime.

Next up, we’ll wrap things up with **Chapter 12: The Final Laugh**, where we review the best pranks from the book and explore how to safely reset everything when the prank war finally comes to an end.
