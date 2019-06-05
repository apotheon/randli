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

## setup

You'll need a datafile.  Create a `.data` directory in your home directory if
it does not already exist, and a subdirectory within it called `randli`, then
create your datafile inside that and name it something like `<dataname>.list`.
The `<dataname>` part is the same `<dataname>` indicated in the usage section
below.

Within that datafile, you need to specify a data type (e.g. "name") and a
specific datum (e.g. "H. L. Mencken") for each item you want in your list using
a "key: value" format like the following example:

    name: H. L. Mencken
    name: Antisthenes
    image: /home/hlm/img/cynicism.png

You may wish to create a config file.  Just create a file called `.randli` in
your home directory with lines using a format like this:

    key: value

Each key you specify should match with a key in the datafile.  You do not need
a key-value pair in a config file for any key whose value you just want printed
to the console when randli selects it, though.  You only need a config file
entry for that key when you want randli to run another program when it selects
a datum with that data type.  For instance, this may be a useful example of a
complete datafile:

    image: gm display ${value}

With the above datafile example, any time randli selects "name: Antisthenes" it
just prints "Antisthenes" to the console, because there is no config file entry
for "name", but any time it selects "image: /home/hlm/img/cynicism.png", it
uses GraphicsMagick's executable `gm` with the "display" command to display the
image at `/home/hlm/img/cynicism.png`.

If you have no `.randli` config file at all, the `randli` program will behave
the same as if you have an empty `.randli` file.

## usage:

    $ randli <dataname>
    <datum>

* `<dataname>` = the name given to a datafile used by `randli`
* `<datum>` = a randomly selected datum from the datafile
