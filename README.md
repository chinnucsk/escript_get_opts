An escript get_opts template
============================

This is a template for using Erlang/escript for building simple cli tools using
a getopt style interface.

Setup
-----

Make sure you have the getopt library in your load path.  I use a ~/.erlang file
and a ~/.erl_lib directory to do this:

```bash
echo "code:add_path(\"${HOME}/.erl_libs/libs\")." >> .erlang
mkdir -p .erl_libs/{repos,libs}
git clone https://github.com/jcomellas/getopt.git ${HOME}/.erl_libs/repos/getopt
cd ${HOME}/.erl_libs/repos/getopt
make
cp ${HOME}/.erl_libs/repos/getopt/ebin/getopt.beam ${HOME}/.erl_libs/libs/
```

use
---

Just edit the spec to add options (and remove the test option), then edit usage
and checkopts to reflect the new options.  The main body of the script has been
moved to script/1, there's no need to edit main/1.  The options are passed into
script/1 as a list of tuples and bare arguments are passed in a seperate list.

Opts Example:

```erlang
[
 help,
 {verbose, 2},
 {quiet, 1},
 {test, "A test arg"}
]
```

BareArgs Example:

```erlang
[
 "Arg1",
 "Arg2"
]
```