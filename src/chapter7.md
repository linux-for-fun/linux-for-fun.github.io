### **Chapter 7: Keyboard Swap Sabotage**

Ah, the keyboard—our trusty companion, the interface between the mind and the machine. What if we twisted that relationship? Imagine your unsuspecting victim sitting down to type, only to find that every keystroke betrays them. Their carefully composed commands turn into gibberish, their typing skills suddenly crumble, and they begin to question if they've somehow forgotten how to use a keyboard. Welcome to **Keyboard Swap Sabotage**, where we will reassign and swap keys to make your target's typing experience a living nightmare.

#### **Step 1: Using `xmodmap` to Reassign Keys**

The key to this prank (pun intended) is **`xmodmap`**, a utility for modifying keymaps and pointer button mappings in X11 systems. By using `xmodmap`, we can change the behavior of specific keys—swapping them, disabling them, or reassigning them to something completely different.

First, let’s check if `xmodmap` is installed. Most systems will have it by default, but if not, install it using:

```bash
sudo apt install x11-xserver-utils
```

Now, let’s begin the sabotage.

#### **Step 2: Swapping Common Keys**

For the simplest prank, we’ll swap some of the most commonly used keys. Let's start with `A` and `S`, two keys that are close together and frequently used in commands and text. Swapping them will lead to a confusing mess of misspelled words and botched commands.

First, find the keycodes for these keys. You can do this by running:

```bash
xmodmap -pk | grep -i "a"
```

You’ll get something like this:

```
38  A (0x61)  S (0x73)
```

Take note of the keycodes (in this case, `38` for `A` and `39` for `S`).

Now, create a new `xmodmap` file to swap these keys. Open a file called `swap_keys.map`:

```bash
nano ~/swap_keys.map
```

Inside this file, add the following lines:

```bash
keycode 38 = S
keycode 39 = A
```

Save and exit the file. Now, apply the key swap:

```bash
xmodmap ~/swap_keys.map
```

Voilà! The `A` and `S` keys have been swapped. Your target will start typing, only to realize that every attempt to type an "A" results in an "S", and vice versa. The chaos begins.

#### **Step 3: Making It Persistent with `.bashrc`**

Of course, you’ll want this prank to persist beyond just one session. To ensure that the key swap is applied every time the user logs in, we’ll add the `xmodmap` command to their `.bashrc` file.

Open the `.bashrc` file:

```bash
nano ~/.bashrc
```

Add the following line at the end of the file:

```bash
xmodmap ~/swap_keys.map
```

Now, every time the user logs in, their keyboard will be sabotaged with the swapped keys. Perfect for prolonged confusion!

#### **Step 4: Swapping More Keys for Maximum Confusion**

Let’s not stop with just two keys—let’s swap a few more for extra chaos. Here are some fun combinations to mess with:

- Swap `W` and `E` for even more typing frustration.
- Swap the `Enter` key with the `Backspace` key, turning every attempt to submit a command into a deletion.
- Swap `Left` and `Right` arrow keys, causing endless navigation woes.

Here’s how to add these swaps to the `xmodmap` file:

```bash
keycode 38 = S  # A -> S
keycode 39 = A  # S -> A
keycode 25 = E  # W -> E
keycode 26 = W  # E -> W
keycode 36 = BackSpace  # Enter -> BackSpace
keycode 22 = Return  # BackSpace -> Enter
keycode 113 = Left  # Right arrow -> Left arrow
keycode 114 = Right  # Left arrow -> Right arrow
```

Once you’ve saved this modified `swap_keys.map` file, run the `xmodmap` command again:

```bash
xmodmap ~/swap_keys.map
```

Now, typing, navigating, and submitting commands will become a disorienting nightmare of mixed-up keys. Your victim will find themselves constantly correcting errors, moving in the wrong direction, and battling with their own keyboard.

#### **Step 5: Disabling Keys Completely**

If swapping keys isn’t enough, let’s go one step further—disabling a key entirely. Maybe the victim’s `Ctrl` key mysteriously stops working, or the `Escape` key refuses to do its job. This can be particularly frustrating when they try to use common keyboard shortcuts.

To disable a key, simply map it to `NoSymbol` in the `xmodmap` file. For example, to disable the `Escape` key (keycode `9`), add this to your `swap_keys.map` file:

```bash
keycode 9 = NoSymbol
```

Now, apply the change:

```bash
xmodmap ~/swap_keys.map
```

The `Escape` key will now do nothing, leaving the victim trapped in whatever program or shell they’re trying to exit. This prank is subtle but incredibly effective, especially when paired with other key swaps.

#### **Step 6: Making It Extra Annoying—Periodic Key Reversion**

For an added layer of confusion, you can periodically revert the key changes and then reapply them, leaving the victim wondering if their keyboard is glitching out. We’ll set up a simple cron job to toggle between the normal and swapped key states every few minutes.

Create a script called `toggle_keys.sh`:

```bash
nano ~/toggle_keys.sh
```

Inside the script, add the following:

```bash
#!/bin/bash

# Check if keys are swapped
if xmodmap -pke | grep -q "keycode 38 = S"; then
    # Revert to normal
    xmodmap -e "keycode 38 = A"
    xmodmap -e "keycode 39 = S"
else
    # Swap keys
    xmodmap ~/swap_keys.map
fi
```

Make the script executable:

```bash
chmod +x ~/toggle_keys.sh
```

Now, set up a cron job to run this script every 5 minutes:

```bash
crontab -e
```

Add the following line to the cron file:

```bash
*/5 * * * * ~/toggle_keys.sh
```

This will toggle the key swap every 5 minutes, leaving your target completely disoriented. One moment the keyboard will behave normally, and the next it will be back to chaos. The victim won’t know if it’s a bug, a hardware issue, or pure madness.

#### **Step 7: Restoring the Keyboard to Normal**

As always, you need to be able to restore order once the prank has run its course. To revert the keyboard to normal, simply remove or comment out the key remapping lines from the `xmodmap` file:

```bash
nano ~/swap_keys.map
# Comment out or delete the key remapping lines
```

Then, run the following command to revert the changes:

```bash
xmodmap -e "keycode 38 = A"
xmodmap -e "keycode 39 = S"
```

Also, don’t forget to remove the cron job if you’ve set it up:

```bash
crontab -e
# Remove the toggle_keys.sh entry
```

After this, the keyboard will behave normally again, and your victim can breathe a sigh of relief—until your next prank, of course.

#### **Pro Tips for Maximum Frustration**

- **Swap Modifier Keys**: Swapping the `Ctrl` and `Alt` keys will create chaos in shortcuts, especially for users who rely heavily on `Ctrl+C`, `Ctrl+V`, and other combinations.
  
- **Invisible Key Swaps**: Swap less noticeable keys, like `,` and `.` or `/` and `-`. This will lead to subtle but constant mistakes in typing, driving the victim crazy as they repeatedly hit the wrong key.

- **Random Key Behavior**: Create a script that changes key mappings randomly every few seconds, turning typing into a completely unpredictable experience.

#### **Why This Works**

The beauty of the **Keyboard Swap Sabotage** prank is in its subtlety. The victim will first think they’re making innocent typing mistakes, only to slowly realize that their keyboard is no longer under their control. The confusion builds as they try to figure out why their muscle memory has betrayed them. It’s the perfect blend of technical trickery and psychological frustration.

#### **In Conclusion**

The **Keyboard Swap Sabotage** is a classic prank that delivers frustration in a wonderfully subtle way. By swapping or disabling keys, you turn the user’s most trusted tool into a source of confusion and chaos. And, of course, it’s easy to reverse, ensuring that the prank leaves no permanent damage—just a few shattered nerves.

Next up, we’ll take things to a whole new level of unpredictability with **Chapter 8: Bash Roulette**—where every command becomes a gamble.
