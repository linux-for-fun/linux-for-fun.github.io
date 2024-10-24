### **Chapter 3: Terminal Games — The Real Ones**

Oh, nothing brings more chaos to an unsuspecting user’s day than a terminal possessed by the unrelenting force of retro video games. Imagine the horror—a simple login turns into a battle against **Tetris**, or **Snake** takes over their screen, leaving them no escape but to play… or so they think. This chapter, dear trickster, will teach you how to turn your target’s innocent terminal into a nonstop gaming nightmare. Because, really, who doesn’t love a good game when they’re trying to get serious work done?

Ready to wreak havoc? Let’s jump in.

#### **Step 1: Installing the Games**

First things first: You’ll need to install the games you plan to inflict upon your victim. Luckily, Ubuntu comes with a set of classic terminal games packaged under `bsdgames`, which includes a selection of retro delights like **Tetris**, **Snake**, and **Pong**. You’ll also want to install `tint` for a more modern (but still terminal-based) version of **Tetris**.

Start by installing these packages:

```bash
sudo apt update
sudo apt install bsdgames tint
```

Once installed, these games are ready to launch from the terminal. But our goal is not just to install them—no, no, we want to make them *automatically launch* when the user logs in. A simple login becomes an unexpected gaming marathon.

#### **Step 2: Setting the Trap in `.bashrc`**

Now, to force the game to launch immediately upon login, we’re going to edit the `.bashrc` file once again (our trusty weapon of mischief). This file is executed every time a user opens a new shell, so it’s the perfect place to add our little gaming surprise.

Open the `.bashrc` file for editing:

```bash
nano ~/.bashrc
```

At the bottom of the file, add the following line to launch **Tetris** every time the user logs in:

```bash
tint
```

This will start **Tetris** automatically when the user logs into the system. **Tetris** will fill the terminal, and the only way out is to exit the game (which they might not realize immediately). But why stop at just **Tetris**? Let’s take it a step further.

#### **Step 3: The Endless Game Loop**

Oh yes, one game is fun, but what if we want the user to be trapped in a loop of games? Finish one game, and another starts. Finish **Tetris**? Here comes **Snake**. Beat **Snake**? Time for **Pong**. The games never end!

Here’s how to set up the endless loop of terminal games:

```bash
while true; do
    # Start with Tetris
    tint
    
    # After exiting Tetris, launch Snake
    snake
    
    # After exiting Snake, launch Pong
    pong
    
    # Loop back to Tetris for infinite fun
done
```

Add this entire block to the end of the `.bashrc` file. Now, when your target logs in, they’ll be trapped in an infinite cycle of games. Each time they finish one, another will start immediately, giving them no respite from the retro gaming madness.

#### **Step 4: Full-Screen Fun**

To take this prank to the next level, let’s force the games to take over the entire terminal window. **Tetris** and other terminal games will normally adjust to the size of the window, so for maximum confusion, tell your victim to press `Ctrl+Alt+F1` (or another function key depending on their setup) to switch to a full-screen terminal.

Now, when the games launch, they’ll consume the entire screen, making the system look fully overtaken by the game. Imagine your poor target trying to figure out how to escape while their entire terminal is flooded with falling blocks or a snaking trail!

#### **Step 5: How to Escape (Optional)**

We’re not completely heartless. The joy of a good prank comes when the victim finally figures out how to escape. Let’s give them a hidden key combination that lets them break out of the game loop.

Modify the infinite loop script to allow an exit condition. Here’s an updated version:

```bash
while true; do
    # Start with Tetris
    tint
    
    # Check if the secret word has been entered to escape
    echo "Type 'escape' to break free, or keep playing!"
    read input
    if [ "$input" == "escape" ]; then
        break
    fi

    # Launch Snake next
    snake
    
    # Then Pong
    pong
done
```

Now, if the user types the word “escape” at any point between games, the loop will break, and they’ll be returned to their terminal, free at last… but only if they figure out the secret!

#### **Step 6: Trigger the Prank at the Right Time**

Of course, the magic of this prank is timing. If you want to truly catch them off guard, consider using a cron job to trigger the prank at a specific time—perhaps right before a meeting, or in the middle of their workday.

Add the prank script to their crontab like so:

```bash
crontab -e
```

Then schedule it to run at a random time:

```bash
0 9 * * * /path/to/game_loop.sh &
```

This will launch the game loop at 9:00 AM every day. Feel free to adjust the timing to your liking—maybe have it trigger at lunchtime or at the end of the workday for maximum confusion.

#### **Step 7: The Victim’s Perspective**

Let’s pause for a moment and consider what your victim will experience when this prank hits.

1. **Login Surprise**: They log into their system, expecting to be greeted by their familiar terminal prompt, only to be instantly thrown into a game of **Tetris**. At first, they’ll think it’s funny, maybe even nostalgic. “Oh, how cute,” they might say. But then…
   
2. **Game After Game**: They finish **Tetris**, hit escape, or manage to lose the game, and instead of returning to their terminal—*boom*—**Snake** takes over. Now they start to get a little more confused. What’s going on here?

3. **Endless Loop**: The realization dawns: they’re trapped. There’s no escape. No terminal, just an endless series of retro games. They might frantically try `Ctrl+C` to break the loop, but the games keep coming. The sense of helplessness grows. “Is this my life now? Just games forever?”

4. **The Escape (Maybe)**: If they figure out that typing “escape” between games will end the madness, they might breathe a sigh of relief. If not… well, they’ll have to come to you for help eventually. That’s when you reveal your evil handiwork with a sly grin.

#### **Step 8: Reversing the Prank**

As always, you need to be able to reverse this prank once the joke has played out. To restore normal functionality, simply remove the game loop from the `.bashrc` file:

```bash
nano ~/.bashrc
# Remove the game loop lines, save, and exit.
```

If you’ve used cron to schedule the game loop, remove it by editing the crontab:

```bash
crontab -e
# Remove the game_loop.sh entry.
```

After that, the system will return to normal, and your target will be free from the reign of endless terminal games.

#### **Pro Tips for Maximum Chaos**

Want to make this prank even more devilish? Of course you do. Here are a few ways to up the ante:

- **Customize the Games**: Change the text that appears within the games. For example, edit the victory screen of **Tetris** to display something like, “You’ll never escape, mortal!” Or modify **Snake** to display taunting messages whenever they lose.
  
- **Randomize the Games**: Instead of always launching **Tetris** first, randomize the game order so your victim never knows what’s coming next. You can easily achieve this by shuffling the game sequence in the script using a random number generator.

- **Add Sound Effects**: Install a terminal sound utility like `beep` or use `aplay` to add sound effects when the games start. Hearing the familiar sounds of retro games blaring from the system will only deepen the confusion.

- **Force a High Score Message**: After the user inevitably loses the game, display a custom high score screen with a message like, “You’ve been hacked by [Your Name]. Good luck getting out!” It’ll send chills down their spine as they realize who’s behind it.

#### **Why This Works**

Terminal games are the perfect blend of nostalgia and surprise. Your victim won’t expect their terminal to become an arcade overnight, and the sheer frustration of being unable to return to their normal workflow is both hilarious and harmless. They’ll be confused, annoyed, and maybe even entertained—but most importantly, they’ll be at your mercy.

And when they finally break free, you can share a good laugh and remind them that all work and no play makes for a dull terminal.

#### **In Conclusion**

The Terminal Games prank is a masterclass in subtle torment. It’s fun, harmless, and easy to set up—but it packs a punch in terms of confusion and frustration. Whether you trap them in a loop of retro games or leave them wondering how to escape, this prank is sure to leave a lasting impression.

And now, dear reader, onto the next diabolical chapter. Up next: **The Talking Terminal** — because sometimes, your terminal should talk back.
