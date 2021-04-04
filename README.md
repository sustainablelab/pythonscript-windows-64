# Context

All contents in this repo (except for this `README.md`) is just
the `windows-64` folder from:

https://github.com/touilleMan/godot-python-assetlib-repo/tree/master/addons/pythonscript

touilleMan's GitHub page for the project is here:

https://github.com/touilleMan/godot-python

TODO(slab): Setup a similar repo copy of the `osx-64` folder for
macOS users.

## Getting this the normal way

Normally this is installed by opening Godot and searching for
`pythonscript` in the **AssetLib**. And that is how I obtained
this copy, version 0.50.0.

## For collaborators on Windows and macOS

So why do I need this copy -- what's wrong with installing
through Godot? My collaborators are Windows and macOS users and
they do not use Godot. I created this copy to make it easier for
them to run my Godot projects.

Ideally, I'd just give them a Windows or macOS executable.
Unfortunately, project export does not yet work on Windows and
macOS for projects that use the pythonscript addon.

So, instead of walking folks through downloading pythonscript via
the Godot AssetLib:

- I make this repo a git submodule in my Godot project
- I tell my collaborators:
    - to `git clone` the project
    - and to run the two `git submodule` commands that copy this
      repo (and my other submodules) into their local repo

# Steps for making a new project

Create a Godot project. Add this repo as a submodule:

```bash
git submodule add ...
```

The directory structure should be:

```
project-folder/
    addons/
        pythonscript/
            SUBMODULE GOES HERE AND IS NAMED: windows-64/
```

Similarly, Python packages that I wrote that are used in the
project and are under development are treated the same way. I add
the Python package as a submodule in the addons folder, then
install it in **editable** mode for the python.exe *used by
pythonscript*:

```
project-folder/
    addons/
        pythonscript/
            windows-64/
                python.exe <--- THIS PYTHON
```

I install in **editable** mode so that collaborators get updates to
my Python package simply by pulling the changes, rather than
having to remember how to reinstall via pip. It also saves me
time not having to upload minor patches to PyPI.

# Steps for cloning an existing project

Clone the project like you would any other repo:

```bash
git clone ...
```

The submodules are empty folders. Pull the submodules in with
these two commands:

```bash
git submodule init
git submodule update
```
