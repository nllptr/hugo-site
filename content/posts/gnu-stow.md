+++
title = "Gnu Stow"
date = 2024-03-11T21:48:38+01:00
tags = ["stow", "neovim", "alacritty"]
+++

For the longest time, I haven't cared too much about keeping my own set of "dotfiles" (or configuration
files) for software that I commonly use. Instead, I've preferred to use software with good defaults
and tried to learn those defaults.

Recently, as I have gotten more into home labbing, I've had the
need to set up the same software on multiple hosts. As a consequence of this, I created a repo for the
single purpose of comitting my configuration files so that they could be used on multiple machines.

My first iteration on this was to just put the files in a `.config` folder, and then write a script
that would put the files in the right place on the host machine. Whenever I had updated my files in
in the git repo, I would need to run the script to overwrite the previous version.

As one does, I watched a lot of YouTube videos on the topic, and soon discovered [GNU Stow](https://www.gnu.org/software/stow/).
It basically does what my script did, but in a cleaner way. In short, Stow creates a symlink for every file in my
folder, "one level up". This means that I don't have to run some sort of update script in order to
copy my changes from the local git repo to their destination.

With my custom script, I had to hard code the source and destination to some extent (I'm no shell scripting pro).
Somewhere along the process, I realized that it was only a matter of time before my update script
would get out of hand.

Stow on the other hand, just creates symlinks to match whatever file structure you have in your repo.

# Some consequences

## Clear process

As I mentioned in the previous section - I like good defaults and conventions. With the assumptions Stow
makes, I have a clear process to adhere to whenever I set up a new environment.

1. Install Stow
2. Clone my dotfile repo to the home folder
3. Run Stow from the repo root

## Hunger for more

Once this very clear workflow was established, I found myself more eager to add to it. I've moved more and
more of my commonly used applications into Stow.

One of the greatest wins was that I finally made the decision to clean up my terminal config. Previously I
used oh-my-zsh. The reason? Good defaults. But over time, as I've added to my `.zshrc`, I've found my terminal
to become slower and slower. It's not by much, but it's noticable. Firing up a new terminal to make a quick change
is annoying when you're forced to wait for a few seconds just for the prompt to become responsive. Yes, I could
take the time to clean it up, but with all of that out-of-the-box configuration that oh-my-zsh provides, it's
hard to know exactly what causes the issues.

A good outcome of this shell overhaul was that I could throw oh-my-zsh away completely. That by itself got
rid of my lag. But I also found Alacritty, a super snappy terminal emulator, that has now replaced my previous
go to solution - iTerm2.

Of course, both the `.zshrc` and the Alacritty config goes into the dotfiles repo.

When I saw how much snappier my terminal could get, and as I now had my config files under control, I started
looking at other places where I could improve my personal toolbox. Text editors is a classic use case, so soon
I found myself building out a neovim config.

# New requirements emerge

So now that I've stared building my dotfiles repo, one idea gnaws in the back of my mind: this needs to be usable
everywhere, otherwise I'm wasting my time. So whenever I pick new software, I give preference to software that is
cross-platform. If Windows is not on the list of supported platforms, that's one excpetion I'm willing to make.

This is one reason that I really like Alacritty. It's cross platform. My previous favorite, iTerm2, made me depend
on iTerm2 specific behavior. The second I moved into a Linux environment, I would sometimes get caught by unexpected
behaviors, usually related to special modifier keys, which Macs have in excess.

Another nice-to-have is that the application is configurable from the `.config` folder. It simply makes for a more
tidy folder structure in your home directory. It's not a hard requirement, but just a preference.

# The long term

My previous stance - prefer good defaults, avoid all customization - has taken the backseat, and I attribute it
all to Stow. I didn't really want to maintain a dotfiles repo if I still had to wrestle with the tedium of
manually putting those files in the right place.
Mostly because of the extra cognitive load of updating my config files. I would have to
make the change, and see that it works in the application, then copy those config changes into my repo.
Too much. But with stow, I edit my config in the local repo, and the changes are reflected in the applications
thanks to Stow's symlinking.

So what does this mean long term? It means that I can take the time to customize my tools. As a software engineer,
there are tons of little optimizations to be made. Before Stow, I didn't want to make that time investment,
because I couldn't manage those optimizations in a good way. But now I can.

I'm not the first to make the analogy, but just as a wood worker takes pride in keeping their workshop clean and
their tools in the right place, so can we hackers keep our config files in order. Just as the wood worker experiments with
the correct blade angle for their hand plane, so we hackers experiment with tool configurations.

And we have something the wood workers don't. We have git :)

https://www.gnu.org/software/stow/

