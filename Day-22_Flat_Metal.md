# A World Conference on Rolling Steel
*"Day 22: Very Big Mangles."*

## Checking drawings into git

This post was going to be an extension of the "*git or not*" subject. My question "*What drawing packages are there where you can commit your work to git?*" has two answers: one from now and one from the 1980s.

- **The answer from now** is to use ***draw.io*** and unselect "compressed" under the preferenence menu. That way you get good descriptive XML that, for a lot of editing, allows `diff` to do its thang. You have most of the advantages of modern drawing (e.g. connectors attached to obects) with a readable descriptive file format.
- **The answer from the 1980s** is ***xfig***. It has its own descriptive file format ... and as soon as I looked at it the scene dissolved into a flashback.

## The rest of this post is a flashback
### Flat Metal rolling in the 1980s

The year is 1988 and I'm three years out of university, working at GEC in Rugby. With a degree in Engineering Science (with a third year option of Electrical Engineering) I've landed in Britain's largest electrical engineering company in its heyday. Having left university heading for a career in electrical machinery and power electronics, I've swerved into mathematical modelling and control for steel rolling.

Hot rolling of flat steel (sheet) is an industry with a massive financial throughput: in the 1980s our rule of thumb was that stopping a rolling mill caused losses of tens of thousands of pounds per hour. The upside of this financial throughput is that quite big investments can be justified for small improvements.

In the mid to late 1980s we were just getting to the point where we could model how thick the metal would be when rolled (using metalurgical properties and temperature measurements to calculate the set points for the very big mangles). Minimising the length of material that was out of tolerance would give enough financial gain to justify investments. Until this point the set points were applied using lookup tables, and the race into active control featured the automation engineering giants of the day: General Electric; GEC; Asea; Alsthom; Siemens; MDS; Hitachi; Toshiba.

At the point where I hit this scene, attention was moving from not just controlling rolled metal thickness but also the profile and flatness: flat metal isn't really flat, it's thicker in the middle than at the edge (this is known as crown or profile). It's a function of the fact that the rolls used to flatten it will bend under the force. Not only do we have to consider the crown when rolling it, we also have to ensure that the thickness reduction from rolling is proportional across the width: if we roll it too thin at the edges then they'll be too long and will be wavy like a pie crust. Fixing wavy edges means more downstream processing which costs money.

### A World Conference

Everyone was racing towards controlling crown and wavy edges at the same time, and we in GEC had our own story to tell. A conference was convened in 1988 in Pittsburgh for those working on the problem, both in the engineering companies and the steel producers, to share their findings and experience.

This sort of conference in the 1980s was pretty formal. People wore suits and presented finished material. In the days before Powerpoint, this meant that you put your presentation onto 35mm slides (which is why they are still called slides in Powerpoint and equivalents) which would get loaded into a slide carousel for projection. Those of us whose presentations were a little more "immediate" could get away with using overhead projection and took A4 or letter size acetates with us to the conference.

I was nominated to represent GEC at this conference. As a 25 year old, three years out of university, I was going to America for the first time to a learned conference. And I had to write a paper to present.

### In which we finally talk about (x)fig

We submitted a written paper - probably now lost forever. I think I wrote it using LaTeX and, in the pre-PDF days, we printed it and put the printout in an envelope to post to the conference organisers, who published it in a proceedings journal.

For the accompanying presentation we decided we'd talk about curve fitting: the bending of the rolls in a mill is neither linear nor parabolic, and we/I had experimented with quartic fits to our models of deformation. What I wanted to show at the conference was how we overlaid modelled curves on both the simulated results and real life measurements from a traversing thickness gauge.

The mechanisms needed to show this were surprisingly difficult. There was no Matlab to make plots, this was all to be done on an overhead projector.

Reader, I used fig (before it was renamed xfig). I was able to make fig diagrams which each had alignment crosses for overlaying on an overhead projector. The results of the simulation or measurements or fit could be spat out of a FORTRAN program as a series of points to be pasted into a .fig file (using emacs), giving a faithfully aligned set of curves that could be overlaid to show the refinements in fitting. For the time, we were pushing the boundaries of presentation technology to bring the curve fitting process to life. And as I sat down, the session chairman said to me off microphone "Wow, that was amazing" - our presentation had hit the mark.

### Epilogue

While writing this piece, I did a quick search for our paper: I'd assumed it was lost in posterity, lying somewhere in a vault in Pittsburgh. Happily I found, via a search of public internet, [a paper in which we are cited as a reference](https://www.jstage.jst.go.jp/article/isijinternational/47/9/47_9_1300/_pdf). Like the snail that looked back after crawling across a beautiful piece of polished marble, I can proudly say "I left my mark".

A sincere thank-you to the original developers of fig.




*This post is day 22 of my #100DaysToOffload challenge. Visit [https://100daystooffload.com](https://100daystooffload.com) to get more info, or to get involved.*