=== SUMMARY ===

Help choosing Bash alias and function names that WON'T come back to bite you
later!

=== VERSION ===

1.0.1

=== MOTIVATION ===

I use Emacs as one of my text editors. Often I prefer it to launch in the
terminal as opposed to in a graphical window which it does by default if it
can. Thus I set the following alias:

alias te='emacs -nw'

I chose te because it was short for Terminal Emacs which made sense from a
mnemonic standpoint. BUT this turned out to be unsafe. Recently I meant to run
"te some_file". Instead I accidentally executed "tee some_file" and it ended
about as well as you can imagine. Happily the file was version controlled but
this was pure luck.

In spite of being a veteran UNIXoid and being well aware of the tee command I
still failed to realize my choice of alias name was an unmitigated disaster.
Hence I started wondering what if there was a system to warn me somehow...

=== A SOLUTION ===

The idea is simple take a proposed function/alias name and spit out known
commands sorted by edit distance from the proposed name. The sort order is
reversed so users can see the closest results without needing to scroll up or
pipe to a pager.

We also query certain package managers if they are present on the system to help
users avoid a name that conflicts with some executable available in the
repositories that they weren't aware of and to avoid the need to rename later
when it turns out the alias shadows some later installed executables.

=== USAGE ===

name-safe-in-bash <proposed_name>

=== LICENSE ===

This is a Freedom Respecting Technology: think Open Source but not just for well
off people with reliable Internet access and an inexplicable desire to be
terminally online. Learn more at:
https://makesourcenotcode.github.io/freedom_respecting_technology.html

It's (admittedly tiny) Open Knowledge Set is as follows:
* the main program source/executable file name_safe_in_bash
  licensed under GNU GPL v3 ( https://www.gnu.org/licenses/gpl-3.0.txt )
* the documentation / Help Information Set consisting of this file
  licensed under GNU FDL v1.3 ( https://www.gnu.org/licenses/fdl-1.3.txt )

=== POSSIBLE FUTURE IMPROVEMENTS ===

Right now we use Levenshtein Distance as the edit distance metric to find exact
matches or possible close commands that could execute in the event of a typo.
While this is mostly good and better than picking a name unaided the current
implementation doesn't take into account situations like accidentally hitting
tab instead of space and getting a completion for a command you didn't want to
execute even though the completed name is quite long and have a big distance
from the proposed name.

It may also be that some kinds of typos are statistically much more likely to
occur than others and hence should be considered a closer match to the proposed
name than they currently are.

It would also be nice to generalize this to shells beyond just Bash though that
may be spun up as another project.

=== CHANGELOG ===

v1.0.1: minor documentation fix

v1.0.0: initial implementation
