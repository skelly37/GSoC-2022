# My Google Summer of Code 2022 summary

## What and for whom
---
### Organization: [MetaBrainz Foundation](https://github.com/metabrainz)
### Project: [MusicBrainz Picard](https://github.com/metabrainz/picard)
### Mentors: [Laurent Monin (zas)](https://github.com/zas) & [Philipp Wolfer (phw)](https://github.com/phw)
### Main focus: Introducing single-instance mode in Picard 3.0
### GSoC website: [Link](https://summerofcode.withgoogle.com/programs/2022/projects/ItQ0NNLd)
---
## What has been done: TL;DR edition
- Picard works in single-instance mode by default, allowing to force-spawn a new instance
- Picard accepts not just file paths but also URLs, MBIDs and commands as command-line arguments
- The command-line arguments are sent to the existing instance (and processed by it) if possible
- Picard can execute commands passed by the command-line interface; e.g. save all files, show the Picard window or close the app
- **IN PROGRESS** Picard can also load the commands from a text file

## List of PRs
### Single instance mode:
- https://github.com/metabrainz/picard/pull/2116: A big commit where the whole single-instance mode for Picard was designed and introduced (only for file paths though)
- https://github.com/metabrainz/picard/pull/2135: Fixed problems with exiting the app, caused by https://github.com/metabrainz/picard/pull/2116
- https://github.com/metabrainz/picard/pull/2130: Supported URLs (with MBIDs) and `mbid://` links (documented there) can be passed with file paths via CLI to an existing (or to a new one) instance
- https://github.com/metabrainz/picard/pull/2137: Supported commands (like `QUIT` or `SHOW`) can be passed via CLI to an existing instance

### Code refactoring:
- https://github.com/metabrainz/picard/pull/2080: Code explicitly marked as deprecated got removed, my initial commit to get to know the Picard codebase and workflow
- https://github.com/metabrainz/picard/pull/2127: Minor patch, unparsed args are now ignored as they were not used anywhere
- **OPEN** https://github.com/metabrainz/picard/pull/2134: `imp` will be removed in Python 3.12 in favor of `importlib`, removed all `imp` ocurrences
- https://github.com/metabrainz/picard/pull/2139: Refactored the whole process of passing arguments to Picard, replaced '%'-formatted strings with f-strings, more than one arguments can be passed correctly to a command.

### Other:
- https://github.com/metabrainz/picard/pull/2122 + https://github.com/metabrainz/picard/pull/2126: Github Actions gives quicker feedback by shortening the timeouts from 6 hours to 30 minutes
- **OPEN** https://github.com/metabrainz/picard-docs/pull/174: Documented my changes

## TODO
- [ ] Make all the PRs listed here merged
- [ ] Add the following commands: 
    - [ ] `LOG_DUMP`
    - [ ] `LOG_CLEAR`
    - [ ] `LOAD`               (file)
    - [ ] `FROM_FILE`          (load commands)
    - [ ] `REMOVE_EMPTY`       (clusters & albums)
    - [ ] `REMOVE_UNCLUSTERED` (files)
- [ ] Introduce a proper command execution order, by creating a blocking duplicates of currently threaded routines like loading files
- [x] Refactor the tagger class to receive parsed args instead of raw `picard_args` to remove *duplicated* args
- [x] Support multiple arguments in commands like `picard -e LOAD`
- [ ] Document the `mbid://` format and the whole *command-line revolution* of Picard 3.0

## What I have learnt during GSoC 2022
- How to work with other people on GitHub
- How to improve my git experience (e.g. hooks)
- How one can handle inter-process communication (not just named pipes, I had to do some research before choosing such approach)
- How to use Windows API with Python
- Differences between Windows and Unix pipes
- `\0` is the only character that is prohibited on both Windows & Unix in path names
- `/tmp` is not the recommended way to store non-persistent app data on *nix
- `os._exit` might be useful when pythonic threads get broken
- [Importing a tuple in Python](https://github.com/django/django/blob/main/django/contrib/auth/views.py#L12-L17) is underrated. `git diff` gets cleaner, as one sees only the additions

## Some personal thoughts
- Python is a really decent language that helps with starting one's programming journey but the deeper I went, the more annoyances I have encountered (that is why I ended up starting to work as a C++ dev)
- Ultra-safety is a double-edged sword: good luck [terminating Pythonic futures/threads with file operations](https://github.com/skelly37/picard/blob/master/picard/util/pipe.py#L242-L244)
- CI/CD and testing in general is as important as decent codebase
- If one can plan their time well, flexible work hours make their work both more effective and more enjoyable
- Python sometimes change for worse or breaks the code without any reason (e.g. they have switched from using `a` mode into `w` on pipes, ref: [LINK](https://www.mail-archive.com/python-bugs-list@python.org/msg280900.html))
- I will not start any new personal project in Python (especially one using multi-threading, multiple processes etc.), unless forced to do so. Nu for scripting, filling the niche & exploring the functional programming, some statically-typed languages for bigger projects, games, research, etc.
- Impostor syndrome is just an another excuse to procrastinate. Do not be scared to learn & do new things but also ask smart questions. Everyone makes mistakes but if you made it to this org, you are a good fit and have enough qualifications


## Special thanks
The whole MetaBrainz community is awesome and I am glad I have become a part of it, but I would like to express my special gratitude to the people I have directly worked with in any way :) (alphabetical order by github username)

- [atj](https://github.com/atj)
- [phw](https://github.com/phw)
- [rdswift](https://github.com/rdswift)
- [zas](https://github.com/zas)

## Note
This is not a final version, GSoC is planned to last until September

