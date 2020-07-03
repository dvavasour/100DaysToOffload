# Git or not?
*"Day 19: There are two sorts of applications - those where you can check your work into git and those where you can't."*

Before I start this post, if there are any non-technical readers _git_ is a toolkit for managing code. It allows you to track versions, make branches, tag releases and more. Many pieces of free/libre software have robust names, and _git_ is one of them.

# File Formats and Wire Protocols
Back in the twentieth century, before REST or XML or JSON was a thing, I remember a colleague had a .sig line _"Look after the wire protocols and the file formats and the application will look after itselt"_. At the time everyone was _"going OOT"_ which in the worst cases meant buying a C++ compiler to compile your C code. But the emphasis was on methods of writing software, functional recomposition, and only a little thought was given to APIs and file formats.

Some years ago I read a piece written by someone who'd worked at both Google and Amazon. He laid out what, as a developer, made Amazon different from the ground up: APIs were (and I suspect still are) **EVERYTHING**. The discipline around APIs comes directly from Jeff Bezos: if you write any component to go anywhere into the technology stack at Amazon, the API **must** be fixed and documented and published, usable both within Amazon and by partners. And the availability and stability and useability of service within the Amazon technology stack makes it scalable and modificable. But that's not the primary subject of this post.

# If it ain't plain it ain't text
This post was going to be about OpenSCAD. The break since my last post is because I've been going through the larval stage with OpenSCAD, designing a case for my Pi-zero/inky-pHAT room temperature display. I've tried various 3D modelling tools, and have plumped for OpenSCAD.

In OpenSCAD you don't draw the item you're modelling: you write a text file that describes it in terms of solid shapes and their relationship to each other. This means that if, for example, you add an opening in a shape, the change is simple enough to be recognised by _diff_.

So as I've been learning and using OpenSCAD, I've been registering and committing my work to _git_.

# Git friendly file formats
Lots of pieces of software have file format that are notionally an ASCII representation. Hell, a Microsoft Word document saved as .docx is a zipfile of a mess of XML files. My criterion for "git friendly" is this:

> If you make a small change, running a _diff_ should show just that change, ideally in one place.

### Git friendly software
Here are a few pieces of software I use that are _git friendly_:

- **OpenSCAD** [3d modelling with geometric shapes]
- **Lilypond** [Music engraving]
- **LaTeX** [Document preparation]
- **Splunk** [Data analytics - everything in the GUI is writen to a .conf file]
- **Ghostwriter** [Hey, it's markdown!]

Here are a few pieces of software that are disappointingly _git unfriendly_:

- **Inkscape** - A simple file with a few rectangles in has a **lot** of elements


I'll update theselists as further thoughts come to me, marking the updated items. If anyone can suggest a git friendly diagramming tool that would be **really** appreciated.



This post is day 19 of my #100DaysToOffload challenge. Visit https://100daystooffload.com to get more info, or to get involved.