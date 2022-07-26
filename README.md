# My Google Summer of Code 2022 summary

## What and for whom
### Organization: [MetaBrainz Foundation](https://github.com/metabrainz)
### Project: [MusicBrainz Picard](https://github.com/metabrainz/picard)
### Mentors: [Laurent Monin (zas)](https://github.com/zas) & [Philipp Wolfer (phw)](https://github.com/phw)
### Main focus: Introducing single-instance mode in Picard 3.0

## List of PRs
### Single instance mode:
- https://github.com/metabrainz/picard/pull/2116: A big commit where the whole single-instance mode for Picard was designed and introduced (only for file paths though)
- https://github.com/metabrainz/picard/pull/2135: Fixed problems with exiting the app, caused by https://github.com/metabrainz/picard/pull/2116
- **OPEN** https://github.com/metabrainz/picard/pull/2130: Supported URLs (with MBIDs) and `mbid://` links (documented there) can be passed with file paths via CLI to an existing (or to a new one) instance.

### Code refactoring:
- https://github.com/metabrainz/picard/pull/2080: Code explicitly marked as deprecated got removed, my initial commit to get to know the Picard codebase and workflow
- https://github.com/metabrainz/picard/pull/2127: Minor patch, unparsed args are now ignored as they were not used anywhere
- **OPEN** https://github.com/metabrainz/picard/pull/2134: `imp` will be removed in Python 3.12 in favor of `importlib`, removed all `imp` ocurrences

### Other:
- https://github.com/metabrainz/picard/pull/2122 + https://github.com/metabrainz/picard/pull/2126: Github Actions gives quicker feedback by shortening the feedback from 6 hours to 30 minutes
- https://github.com/metabrainz/picard-docs/pull/174: Documented my changes

## TODO
- [ ] Make all the PRs listed here merged
- [ ] Handle https://tickets.metabrainz.org/browse/PICARD-2526
- [ ] Document the `mbid://` format and the whole *command-line revolution* of Picard 3.0

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

## Note
This is not a final version, GSoC is planned to last until September

