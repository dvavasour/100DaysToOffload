# Rediscovering screen and discovering tmux

*"Day 9: A long relationship with text terminals"*

I never used a VT52, but I did use VT52 compatible terminals, and I used genuine VT100s. Later I used VT220s. At university these were connected onto VAXen either directly or via Gandalf switches, then once I started work they hung off GEC4000 series machines. Later we would put SPIF boards onto our Sun boxes (Serial and Parallel InterFace) and for some years I worked at a desk with a VT220 directly onto a Sun box.

This was when I first used GNU Screen. On the big screens on the Sun workstations there was a window manager running, so you would have multiple windows open for your different working contexts. On a terminal I used GNU Emacs as a quasi window system - buffers for editing source files, buffers for running make, or running grep, or running a shell. Hell, for years I used Emacs RMail mode as my email client.

But tools were moving on. My email was on a remote IMAP server, and I defected to PINE. And my colleague introduced me to GNU Screen - a session manager for terminal windows. Its USP for me was the ability to run multiple sessions on a single terminal and switch between them using a Control sequence (as an Emacs user I  quickly changed the escape character from Ctrl-a to Ctrl-z).

I hadn't thought about GNU Screen for years and years until today. Almost everything we do lives in its own window, and you can start another context at the click of a mouse. At times you will end up with many PuTTY windows open, and have to do beat them into submission, but that's just how it is. Then I was watching  a [video](https://www.youtube.com/watch?reload=9&v=2sjqTHE0zok) signposted by [Kev Quirk](https://fosstodon.org/@kev) about git (which I strongly recommend - you'll learn what git does *and then* how to use it). The instructor was moving freely between contexts in a full screen terminal session, and it turns out that not only is Screen still a thing, there is a new emulator *"tmux"*.

This is day one of using tmux. It solves a specific annoyance: having multiple PuTTY windows open onto the same host for different purposes, and finding you're in the wrong context. So, for example, you can have a window as your regular user and another windows as root. You can have a window open in the config file directory where you're hacking, and another window open in the logfile directory. But tmux goes further than that: you can divide the window into panes, so you can have a pane running "tail -f <logfile>.log" while you restart a service in another pane. All within the same PuTTY session. And tmux retains the ability of Screen to detach and reattach a session: apart from anything else, this means that if your connection gets dropped for some reason you haven't lost your context.

I'll need some weeks of usage to settle into my *modus operandi* with tmux, but it's clear that from now my UserData for new instances is going to include *"yum install -y tmux"* immediately after *"yum install -y emacs"*.

#100DaysToOffload