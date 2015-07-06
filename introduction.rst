.. _introduction:

Introduction
============

Overview
--------

Computer programming skill helps you to solve many real world
problems.  Programming is a process starting from formulation of a
computing problem to producing computer programs (software).  Computer
programming is part of a larger software development process.
Programming involves analysis, design and implementation of the
software. The activity of implementing software is commonly referred
to as coding.  Sometimes coding involves more than one programming
language and use of other technologies.  Learning a programming
language is a key part of the skill required for computer programming
or software development in general.

Using a programming language, we are preparing instructions for a
computing machine.  The computing machine could be a desktop computer,
laptop, mobile phone etc.  There are many programming languages in use
today with varying features.  This book is a comprehensive guide to Go
programming language.

.. sidebar:: Language Features & Facts

   - compiled
   - statically typed
   - garbage collected
   - built-in concurrency
   - very fast compilation
   - no classes
   - 25 keywords
   - two compilers: gc and gccgo

Go, also commonly referred to as Golang, is a general purpose
programming language.  Go was initially developed at Google in 2007 by
Robert Griesemer, Rob Pike, and Ken Thompson.  Go was publicly
released as a free/open source software in November 2009 by Google.

The design of Go was inspired by many other programming languages like
C, Python, occam etc.  Go programs can run on many operating systems
including GNU/Linux, Windows and Mac OS X.

You will require some preparations to learn Go programming. The next
section explains the preparations required.

Preparations
------------

Learning a natural language like English, Chinese, Spanish etc. is not
just understanding the alphabet and grammar of that particular
language.  Similarly there are many things that you need to learn to
become a good programmer.  Even though this book is going to focus on
Go programming, now we are going to see the other topics that you need
to learn.  This section also explains the installation of Go compiler
and setting up the basic development environment.

You will be writing Go programs using a text editor like Notepad,
Notepad++, Gedit, Vim etc.  The file that you create using the text
file is called source file.  The source file will be in plain text
format.  The Go compiler creates executable programs from the source
file.  You can run the executable program and get the output.  So, you
need a text editor and Go compiler installed in your system.

Depending on your operating system, follow the instruction given below
to install the Go compiler.  If you have difficulty following this,
you may get some help from your friends to do this step.  Later we
will write a simple Go program and run it to validate the steps.

You can use any text editor to write code.  If you are not familiar
with any text editor, consider using Vim.  We will go through the Vim
configuration briefly here.

Using a source code management system like Git would be helpful.
Keeping all your code under version control is highly recommended.
You can use a public code hosting service like GitHub, Bitbucket,
GitLab etc. to store your examples.

Linux Installation
~~~~~~~~~~~~~~~~~~

Go project provides binaries for major operating systems including
GNU/Linux.  You can find 32 bit and 64 bit binaries for GNU/Linux
here: https://golang.org/dl

The following commands will download and install Go compiler in a
64 bit GNU/Linux system::

  $ cd $HOME
  $ wget https://storage.googleapis.com/golang/go1.4.2.linux-amd64.tar.gz
  $ tar zxvf go1.4.2.linux-amd64.tar.gz
  $ mkdir $HOME/mygo

The first line ensure that current working directory is the home
directory for the user.  The `HOME` environment variable contains the
path to the user's home directory.

The second line download the 64 bit binary for GNU/Linux.  The `wget`
is a command line download manager.  Alternatively you can use `curl`
or any other download manager to download the tar ball.

The third line extract the downloaded tar ball into `go` directory
inside the home.

The last line creates a directory named `mygo` as the workspace.  This
directory can be used to place binaries, third party packages and your
own Go source code.

You also need to set few environment variables.  Open the
``$HOME/.bashrc`` file in a text editor and enter these lines at the
bottom::

  $ export GOROOT=$HOME/go
  $ export PATH=$PATH:$GOROOT/bin

  $ export GOPATH=$HOME/mygo
  $ export PATH=$PATH:$GOPATH/bin

The first line set `GOROOT` environment variable pointing to
``$HOME/go``.  This is required for proper functioning of Go tools.

The second line append the ``$GOROOT/bin`` to the `PATH` environment
variable.  This will help you to run `go`, `godoc` and `gofmt` commands
from command line.

The third line set the `GOPATH` environment variable pointing to
``$HOME/mygo``.  The GOPATH environment variable specifies the
location of your Go workspace.  The project source files will be added
inside this workspace.

The last line append ``$GOPATH/bin`` to the `PATH` environment
variable.  This will help you to run any executable binaries installed
using Go source code.

Windows Installation
~~~~~~~~~~~~~~~~~~~~

There are separate installers (MSI files) available for 32 bit and 64
bit versions of Windows.  The 32 bit version MSI file will be named
like this: ``go1.x.y.windows-386.msi`` (Replace `x.y` with the current
version).  Similarly for 64 bit version, the MSI file will be named
like this: ``go1.x.y.windows-amd64.msi`` (Replace `x.y` with the
current version).

You can download the installers (MSI files) from here:
https://golang.org/dl

After downloading the installer file, you can open the MSI file by
double clicking on that file.  This should prompts few things about
the installation of the Go compiler.  The installer place the Go
related files in the ``C:\Go`` directory.

The installer also put the ``C:\Go\bin`` directory in the system
`PATH` environment variable.  You may need to restart any open command
prompts for the change to take effect.

You also need to create a directory to download third party packages
from github.com or similar sites.  The directory can be created at
``C:\mygo`` like this::

  C:\> mkdir C:\mygo

After this you can set `GOPATH` environment variable to point to this
location.  Temporarily you can set it like this::

  C:\> set GOPATH=C:\mygo

You can also append ``C:\mygo\bin`` into the `PATH` environment
variable.

If you do not know how to set environment variable, just do a Google
search for: `set windows environment variable`.

The `GOROOT` environment variable is not required here as you have
installed the `Go` inside ``C:\Go`` folder.  If you have changed that
location during the installation, set the `GOROOT` pointing to the
location you selected.

Using Vim
~~~~~~~~~

If you are not comfortable with any text editor spend some time (3 to
4 hours) to learn Vim and come back here.  Vim is a good text editor
for writing code.  You can use the `vim-go
<https://github.com/fatih/vim-go>`_ and tagbar plugins to write code.
You can use the `vim-plug <https://github.com/junegunn/vim-plug>`_
plugin manager to install these plugins.

In your ``$HOME/.vimrc`` add this configuration text::

  call plug#begin('~/.vim/plugged')

  Plug 'tpope/vim-sensible'
  Plug 'fatih/vim-go'
  Plug 'majutsushi/tagbar'
  Plug 'scrooloose/nerdtree', { 'on': 'NERDTreeToggle' }
  Plug 'nsf/gocode', { 'rtp': 'vim', 'do': '~/.vim/plugged/gocode/vim/symlink.sh' }

  call plug#end()

  nmap <F2> :NERDTreeToggle<CR>
  au FileType go nmap <F8> :TagbarToggle<CR>
  au FileType go nmap <Leader>gd <Plug>(go-doc)
  au FileType go nmap <Leader>i <Plug>(go-info)

After saving this you can open vim and run `:PlugInstall` command to
install the plugins.  You can also run `:GoInstallBinaries` command to
install all the required binaries.  Before running the command, make
sure that you have completed all the preparations mentioned in the
previous sections.

Hello World!
~~~~~~~~~~~~

It's a tradition in teaching programming to introduce a `Hello World`
program as the first program.  This program normally prints a `Hello
World` to the console when running.

Here is our hello world program.  You can type the source code given
below to your favorite text editor and save it as ``hello.go``.

.. code-block:: go
   :linenos:

   package main

   import "fmt"

   func main() {
       fmt.Println("Hello, World!")
   }

Once you saved the above source code into a file.  You can open your
command line program (bash or cmd.exe) then change to the directory
where you saved the program code and run the above program like this::

  $ go run hello.go
  Hello, World!

If you see the output as `Hello, World!`, congratulations!  Now you
have successfully installed Go compiler.  In fact, the `go run`
command compiled your code to an executable format and then run that
program.  The next chapter explains more about this example.

Using Git
~~~~~~~~~

You should be comfortable using a source code management system.  As
mentioned above Git would be a good choice.  You can create an account
in GitHub and publish your example code there.  If you do not have any
prior experience, you can spend 2 to 3 days to learn Git.

Using Command Line
~~~~~~~~~~~~~~~~~~

You should be comfortable using command line interfaces like GNU Bash
or PowerShell.  There are many online tutorials available in the
Internet to learn shell commands.  If you do not have any prior
experience, you can spend few days (3 to 4 days) to learn command line
usage.

Organizing Code
---------------

As mentioned above, you can place project source files under the
workspace directory.  The workspace directory is denoted by `$GOPATH`
environment variable.  The installation steps explained in the
previous sections, we used `$HOME/mygo` as the workspace directory.

Under the workspace directory there will be three sub-directories
named `bin`, `pkg` and `src`.  The `bin` directory contains executable
binaries created from Go programs.  We have already added this
`$GOPATH/bin` directory to `PATH` environment variable.  This will
help us to execute programs directly without specifying the full path.
The `src` directory contains the source files.  The `pkg` directory
contains package objects used by go tool to create the final
executable binaries.

Under the `src` directory, you can place your code.  Although the
source files are organized into sub-directories.

If you are using GitHub for hosting code, you can create a directory
structure under workspace like this:
`src/github.com/<username>/<projectname>`.  Replace the `<username>`
with your GitHub username or organization name and `<projectname>`
with the name of the project.

.. note:: Go tool

   The command program "go" is called `Go tool
   <https://golang.org/cmd/go>`_.  Go tool command has many
   sub-commands.  To see all commands use ``go help`` and to see help
   of a particular command use ``go help <command>``.  Here is a small
   list of frequently used sub-commands. ::

     build       compile packages and dependencies
     fmt         run gofmt on package sources
     get         download and install packages and dependencies
     install     compile and install packages and dependencies
     run         compile and run Go program
     test        test packages
     version     print Go version
     vet         run go tool vet on packages

The example hello world program we introduced earlier has been pushed
into GitHub here: `https://github.com/baijum/introduction`.  You can
get this code into the workspace using `go get` command::

  $ go get github.com/baijum/introduction

To run this project, go to the project directory and use `go run`
command::

  $ cd $GOPATH/src/github.com/baijum/introduction
  $ go run hello.go
  Hello, World!

We will walk through the hello world example in the next chapter.

Summary
-------

This chapter provided an introduction to Go programming language.
Also briefly mentioned about other topics required to become a good
programmer.  The next chapter provides a quickstart to the language.

.. raw:: html

   <div id="disqus_thread"></div> <script type="text/javascript"> var
   disqus_shortname = 'comprehensivego'; (function() { var dsq =
   document.createElement('script'); dsq.type = 'text/javascript';
   dsq.async = true; dsq.src = '//' + disqus_shortname +
   '.disqus.com/embed.js'; (document.getElementsByTagName('head')[0]
   || document.getElementsByTagName('body')[0]).appendChild(dsq);
   })(); </script> <noscript>Please enable JavaScript to view the <a
   href="https://disqus.com/?ref_noscript" rel="nofollow">comments
   powered by Disqus.</a></noscript>
