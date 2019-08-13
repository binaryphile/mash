Mash
====

Bash utility for project-specific aliases/functions inspired by
Makefiles

Mash allows you to create project-specific Mashfiles which define bash
aliases and functions that you can call from the command-line.

It is not a build utility like make, it simply gives you a way to define
"targets" which you can call directly as arguments to mash much like
make does.

Quick Start
-----------

Clone this repo and add **bin** to your PATH. You can use a bash package
manager such as [basher] to automate this for you.

Create a Mashfile in your project directory. Create aliases or functions
normally in that file (no need for a [shebang]).

Call the function/alias from the Mashfile directory with:

    mash FUNCTION_OR_ALIAS [ARGS]

ARGS are passed to the function or appended to the alias command.

Examples
--------

Mashfile:

    alias ctl="supervisorctl -c $(dirname "$BASH_SOURCE")/supervisor.conf"

Where **supervisor.conf** is in the same directory as the Mashfile.

CLI:

    mash ctl status

Note that mash doesn't prevent you from calling functions or commands
defined outside the Mashfile, such as:

    mash echo hello

While that's not a feature, it's not something I plan to remove as it's
tricky to limit the called functions to those defined in an arbitrary
file.

Imports
-------

Unless the environment variable **MASH\_LEGIBLE** is set to *0*, mash
will automatically load all of the libraries from the [legible bash]
framework.

These functions will be available to your Mashfile.

Extending Mash
--------------

Mash will autoload any **\*.bash** file in the **mash** folder under
Mashfile's location. You can manually source files within Mashfile, but
you don't have to by following this convention.

Why Mash?
---------

Mash is a portmanteau of *make* and *bash*, much like rake is for *ruby*
and *make*. Since several projects already use *bake*, I went the other
way. I do find it interesting that both ways are popular things you can
do with potatoes, however.

------------------------------------------------------------------------

The Markdown in this document was formatted with [pandoc].

  [basher]: https://github.com/basherpm/basher
  [shebang]: https://wiki-dev.bash-hackers.org/scripting/basics#the_shebang
  [legible bash]: https://github.com/binaryphile/legible
  [pandoc]: https://pandoc.org/
