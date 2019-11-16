# A booklet explaining how to build a booklet 

[![Build status][badge]][travis]

[travis]: https://travis-ci.org/SquareBracketAssociates/Booklet-PublishingAPillarBooklet
[badge]: https://travis-ci.org/SquareBracketAssociates/Booklet-PublishingAPillarBooklet.svg?branch=master


The result from the latest successful Travis build can be found in the release pane of this page.

# Pillar installation on Mac OS X / Linux

## Building from sources

You first need to get Pillar.

Execute the `build.sh` script found in the `scripts` directory:

```bash
$ git clone git@github.com:pillar-markup/pillar.git
$ cd pillar
$ ./scripts/build.sh
```

Note: For OSX users, you might need to install `wget` via `brew` following for example:

```bash
# The following lines will install both Homebrew and wget, ignore the first one if Homebrew is already installed
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
$ brew install wget --with-libressl
```

## Setting up the environment

You can then proceed to install that pillar build where you want.
For example, you can place it in a hidden directory in your home directory:

```bash
# Go back to the previous directory and 
# move the pillar directory to your HOME
$ cd ..
$ mv pillar ~/.pillar
```

Then add that directory to the PILLAR_HOME and HOME environment variables, for example, by modifying your ``.bashrc`` (or `.zshrc`) with:
```
export PILLAR_HOME="$HOME/.pillar/build"
export PATH="$PATH:$PILLAR_HOME"
```

## Test your installation

To test your pillar installation, open a new terminal and execute the pillar `--version command`. If everything is ok, that should print out (as in the current version) the version of the Pharo VM. For example:

```bash
$ pillar --version
M:    CoInterpreter VMMaker.oscog-eem.2380 uuid: c76d...
```

## Getting started

To create a book, you can start by installing the book archetype in a directory where you want to manage it:

```bash
$ mkdir my-new-book
$ cd my-new-book
$ pillar archetype book
```

You can then edit the pillar files and the pillar configuration file `pillar.conf`.
You might need to add your chapters in the file `index.pillar` following the line:
```
${inputFile:Chapters/YourChapter.pillar}$
``` 

For example, the basic archetype's index:

```
!My first book
${inputFile:Chapters/Chapter1/chapter1.pillar}$
${inputFile:Chapters/Chapter2/chapter2.pillar}$
```

## Building a document

Finally, you can generate your book in pdf or html using the command `pillar build ...`.
LateX is needed to build a pdf, if you have not installed it yet, install the texlive-full in your system
For Linux users, 
```bash
sudo apt-get install texlive-full
```

For OSX users,
```
#We need to install brew if not done before
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

#Then simply run the next line to install texmaker 
$ brew install homebrew/cask/texmaker

#cask is a homebrew addon needed to install 
#texmaker installed through previous line
```

Finally, the generation of your document in pdf or html is done by:
```bash
#First line for pdf, second for html
$ pillar build pdf
$ pillar build html
```

The resulting pdf or html site will be written into the `_result` directory.

# To contribute
- Fork
- Do pull Request 
