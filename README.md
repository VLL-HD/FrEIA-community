# FrEIA-community

The areas where work is needed, and what has to be done, are outlined below.
We plan to improve these areas with generous help from the community.

## Address all issues and PRs

**What?** 

Issues and PRs have been collecting, and we have not had the chance to keep up with them.

**How?**

Go through and answer all open issues. Fix them if it's not much work. 
Close them where appropriate. Also go through the PRs, audit and merge them.

**Difficulty?** 1/5

## FrEIA.modules

**What?** 

There are many modules that are 2-3 years old, introduced for some specific purpose.
Sometimes it turned out that the concept didn't even work and the module is useless.
In some cases, they overlap in functionality with other modules.
Some of them also don't have docstrings or explanations what it does.

**How?**

Ensure that
1. all the modules are useful 
2. the same functionality isn't implemented in two different modules
3. all modules have a useful docstring explaining the arguments
3. the modules work correctly

Go through all the modules listed in `FrEIA/modules/__init__.py`.
Check points 1-3 above, and perhaps 4 (overlap with unittests).

Then deprecate modules that are old or unnecessary, or can be combined with similar ones,
and add docstrings.
Delete the ones that were already deprecated with v0.2 (see `FrEIA/modules/coupling_layers.py`, lines 430-434)

**Difficulty?** 3/5

## Unittests

**What?**

The test coverage is very low.
There is no unified way to test e.g. invertibility, or Jacobian 
(has to be written once, and can work for all modules).

**How?**

Set up the proper structure to test all modules in a universal way,
in addition to module specific tests that may be necessary.
Ensure there is test coverage for everything, including 
`FrEIA.framework.ReversibleGraphNet` and `FrEIA.framework.ReversibleSequential`.

**Difficulty?** 3/5

## Tutorial & documentation

**What?**

The auto-generated docs for the API and modules are old,
and not regularly refreshed. It's also very hard to navigate,
and all the inherited `torch.nn.Module` methods are also included.
The tutorial is just a long README, but would be better in separate files on different topics.

**How?**

* Fix the auto-generated docs (maybe sphinx would work better?)
* Split the README into multiple .md or .rst files for the tutorial
* Improve the tutorial by including new modules (e.g. `AllInOneBlock`),
  and especially `ReversibleSequential` which is fine for 80% of cases and much simpler to understand.
* Add the missing sections about how to write your own modules.
* For the final section of tips, we have better knowledge on a lot of things now
* Perhaps the tutorial can be included into the online documentation

**Difficulty?** 2/5

## Miscellaneous

**What?**
* Add a git tag before the hackathon
* Create a release after the hackathon is done.
* Make sure that `setup.py` and installation instructions still work
* Inquire about continuous integration
* Properly comment `ReversibleGraphNet` and `Node`, it's a recursive nightmare
* Fix the issue with `ReversibleGraphNet._buffers` (i.e. edges on the computation graph) 
  not freeing once they are no longer needed, and also being included in `state_dict()`
* Write some kind of changelog to put in the README, to let people know what has changed

**Difficulty?** 1/5
