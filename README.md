# github-badge-cache-buster
A small tool that uses curl to PURGE the github cache for badges displayed in README.md files

Unfortunately github caches badges ( on a server called camo.githubusercontent.com ) quite agressively.
This leads to badge data being out of date a lot of the time.

There is a large list of bugs open (and incorrectly closed) relating to this.
Some of them are.....
- #111
- #116
- #218
- #224
- #414

