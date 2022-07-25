# My Google Summer of Code 2022 summary

## What and for whom
### Organization: [MetaBrainz Foundation](https://github.com/metabrainz)
### Project: [MusicBrainz Picard](https://github.com/metabrainz/picard)
### Mentors: [Laurent Monin (zas)](https://github.com/zas) & [Philipp Wolfer (phw)](https://github.com/phw)
### Main focus: Introducing single-instance mode in Picard 3.0

## List of PRs
### Picard

### Picard docs

## What I have learnt during GSoC 2022
- How to work with other people on GitHub
- How to improve my git experience (e.g. hooks)
- How one can handle inter-process communication (not just named pipes, I had to do some research before choosing such approach)
- How to use Windows API with Python
- Differences between Windows and Unix pipes
- `\0` is the only character that is prohibited on both Windows & Unix in path names
- `/tmp` is not the recommended way to store non-persistent app data on *nix.
- `os._exit` might be useful when pythonic threads get broken

## Some personal thoughts
- Python is a really decent language that helps with starting one's programming journey but the deeper I went, the more annoyances I have encountered (that is why I ended up starting to work as a C++ dev)
- Ultra-safety is a double-edged sword: good luck [terminating Pythonic futures/threads with file operations](https://github.com/skelly37/picard/blob/master/picard/util/pipe.py#L242-L244)
- CI/CD and testing in general is as important as decent codebase
- If one can plan their time well, flexible work hours make their work both more effective and more enjoyable
- Python sometimes change for worse or breaks the code without any reason (e.g. they have switched from using `a` mode into `w` on pipes, ref: [LINK](https://www.mail-archive.com/python-bugs-list@python.org/msg280900.html))
- I will not start any new personal project in Python (especially one using multi-threading, multiple processes etc.), unless forced to do so. Nu for scripting, filling the niche & exploring the functional programming, some statically-typed languages for bigger projects, games, research, etc.
- Impostor syndrome is just an another excuse to procrastinate. Do not be scared to learn & do new things but also ask smart questions. Everyone makes mistakes but if you made to any org, you are a good fit and have enough qualifications. 


## Special thanks
The whole MetaBrainz community is awesome and I am glad I have become a part of it, but I would like to express my special gratitude to the people I have directly worked with in any way :) (alphabetical order by github username)

- [atj](https://github.com/atj)
- [phw](https://github.com/phw)
- [rdswift](https://github.com/rdswift)
- [zas](https://github.com/zas)

