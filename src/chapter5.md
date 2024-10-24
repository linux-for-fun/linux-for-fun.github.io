### **Chapter 5: Sudon't Do That!**

Ah, `sudo`. The sacred command. The one that grants mere mortals the power of the root user, allowing them to wield the full might of the system with just a few keystrokes. But what if, my dear agent of chaos, we could turn this power into something... *mischievous*? What if, instead of granting them root access, `sudo` delivered snarky comments, cryptic warnings, or downright absurd messages? Welcome to the world of **Sudon't Do That!**, where we take the holiest of Linux commands and make it the punchline of our next great prank.

#### **The Setup: Tweaking `sudo` with Aliases**

We’ll begin by hijacking the `sudo` command using an alias—an incredibly simple yet devastatingly effective way to redirect `sudo` to do our bidding. With just a few modifications to the `.bashrc` file, we can make `sudo` behave in all sorts of unexpected ways, from harmless jokes to making the user doubt their very existence.

Let’s dive in.

#### **Step 1: Creating a Basic Alias for `sudo`**

First, we’re going to create a basic alias that changes the response when someone runs `sudo`. We won’t disable the command entirely (we want them to get their work done eventually), but we’ll insert a little delay or message before the actual `sudo` command runs.

Open the `.bashrc` file for editing:

```bash
nano ~/.bashrc
```

Now, let’s add this simple alias for `sudo`:

```bash
alias sudo='echo "Are you sure you want to do that?" && sudo'
```

With this alias in place, every time the user runs `sudo`, they’ll first see the message “Are you sure you want to do that?” before the command executes normally. This is just the tip of the iceberg, though—let’s get more creative.

#### **Step 2: Adding Humor and Snark**

Now that we’ve got the basic alias down, it’s time to make things more fun. Let’s add some random snarky comments that will pop up every time the user tries to use `sudo`. These will make them second-guess whether they should even be using the command at all.

Here’s an improved version of the alias that adds random humor:

```bash
alias sudo='responses=("I don't think so, buddy!" "Permission denied, because I said so." "You think you're in charge now?" "Sudo who? Sudo you!") && echo ${responses[$RANDOM % ${#responses[@]}]} && sudo'
```

With this alias, each time the user runs `sudo`, they’ll be greeted with one of these snarky messages before the command executes. Every time they use `sudo`, it’s a new, sarcastic comment—turning a simple command into an unexpected encounter with the terminal’s “attitude.”

#### **Step 3: Adding a Delay for Extra Annoyance**

Want to ramp up the annoyance factor? Let’s add a delay before `sudo` executes, just to mess with their patience. This way, every time they run `sudo`, they’ll get the usual snarky message, followed by a pause where nothing happens—forcing them to wait for a few seconds before the command finally runs.

Here’s how to add a random delay between 1 and 5 seconds:

```bash
alias sudo='responses=("I don't think so, buddy!" "Permission denied, because I said so." "You think you're in charge now?" "Sudo who? Sudo you!") && echo ${responses[$RANDOM % ${#responses[@]}]} && sleep $((RANDOM % 5 + 1)) && sudo'
```

Now, every time the user runs `sudo`, they’ll get a snarky comment, and then have to wait for a random amount of time before the command actually executes. This will drive them nuts, especially if they’re in a hurry!

#### **Step 4: Fake Errors for Maximum Confusion**

Next, we can take things up a notch by introducing fake error messages. Imagine the horror when the user tries to run `sudo`, only to be greeted with a terrifying error message like “System compromised” or “Root access revoked.” The beauty of this is that it’s all just for show—the command will still run eventually, but only after we’ve made them sweat a little.

Here’s how to add fake error messages to the alias:

```bash
alias sudo='errors=("System compromised. Please contact your administrator." "Root access revoked." "Unauthorized access detected." "Security breach in progress.") && echo ${errors[$RANDOM % ${#errors[@]}]} && sleep 3 && sudo'
```

With this version of the alias, every time the user runs `sudo`, they’ll see one of these terrifying fake error messages, followed by a delay. Only after the delay will the actual `sudo` command run, leaving the user thoroughly confused and probably panicking, at least for a few moments.

#### **Step 5: Creating the Ultimate `sudo` Prank—Infinite Loop of Denial**

Now, if you’re feeling particularly evil, we can take things even further with an infinite loop of `sudo` denial. In this version of the prank, no matter how many times they try to use `sudo`, the command will always respond with some snarky message or fake error, but it will never actually execute. This is perfect for temporarily locking them out of `sudo` privileges in the most annoying way possible.

Here’s how to set up the infinite loop:

```bash
alias sudo='responses=("Not today, friend." "Maybe later." "Nope, try again." "Nice try, but no.") && while true; do echo ${responses[$RANDOM % ${#responses[@]}}]; sleep 2; done'
```

With this alias, every time the user runs `sudo`, they’ll be trapped in an endless loop of denial. The terminal will just keep spitting out snarky messages, forcing them to admit defeat. Of course, you’ll need to restore normal functionality eventually (maybe after they beg for mercy), but in the meantime, enjoy the chaos.

#### **Step 6: Giving Them an Out (Eventually)**

No prank is complete without an exit strategy. After all, you don’t want to lock them out of `sudo` forever—they might actually need it. Once the prank has run its course, you can revert the alias and return `sudo` to its original functionality.

To remove the prank, simply edit the `.bashrc` file and remove the alias line:

```bash
nano ~/.bashrc
# Remove the sudo alias line
```

Then, reload the `.bashrc` file to restore normal functionality:

```bash
source ~/.bashrc
```

With the alias removed, `sudo` will go back to being the boring, all-powerful command it was meant to be. But until then, enjoy watching your victim suffer through the terminal’s endless taunts.

#### **Step 7: Taking It Further—Make `sudo` Demand Random Passwords**

For a final twist, let’s make `sudo` even more frustrating by making it demand random, nonsense passwords. This one is sure to confuse the heck out of your target, especially when they know their actual password works, but the system insists on something else.

You can achieve this by modifying the `sudo` prompt to ask for a password like this:

```bash
alias sudo='responses=("Please enter the secret password." "You must guess the correct passphrase." "What is the airspeed velocity of an unladen swallow?") && echo ${responses[$RANDOM % ${#responses[@]}]} && sudo'
```

Now, whenever the user runs `sudo`, they’ll be asked to enter some ridiculous password or answer a nonsensical question before the actual `sudo` command executes.

#### **Why This Works**

The beauty of the `sudo` prank lies in its psychological warfare. People are used to `sudo` being a serious, no-nonsense command, so when it starts acting up, delivering snarky comments, fake errors, or random delays, it throws them completely off balance. The prank is simple to set up, harmless to the system, and easy to reverse—but in the meantime, it creates an infuriating and hilarious experience for your victim.

#### **In Conclusion**

The `Sudon't Do That!` prank is a masterstroke of mischief. Whether you opt for lighthearted snark, fake error messages, or an infinite loop of denial, this prank is sure to confuse and amuse in equal measure. Just remember to give your victim a way out before they completely lose their mind—and enjoy the chaos you’ve sown in the meantime.

Next up, let’s dive into some truly deceptive territory with **Chapter 6: Alias Apocalypse**—where we turn innocent commands into unpredictable chaos.
