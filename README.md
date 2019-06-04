# randli

The term "randli" comes from "random-lists-items", as it selects a list item
randomly from a (flat file, currently YAML) database of lists, and either
prints it or runs a command using that list item selection as an argument.

This is presently a stupid script to produce randomized prompts, either a
character name (likely an existing character in your game or story, but you can
add whatever names you like) or an image (opened automatically), to kick-start
the inspiration when planning a new scene.  I have plans to generalize it.  At
this time, it's just barely enough to serve a very narrow purpose that inspired
me to write it in the first place.

In its nascent form, it works, but it offers no help documentation output, no
error checking, no particular generalization of utility, no configuration, no
substantive portability, and so on.  At least some of that will change for the
better in time to come.

## installation:

Copy or link the executable in this project's `bin/` directory to your
execution path.

## usage:

    $ randli <dataname>
    <datum>

* `<dataname>` = the name given to a datafile used by randli
* `<datum>` = a randomly selected datum from the datafile
