.. _quickstart:

Quickstart
==========

.. sidebar:: Scratch Programming

   If you do not have any prior programming language experience, you
   can can spend few days with Scratch programming.  The Scratch
   website provides an online programming environment:
   `scratch.mit.edu <https://scratch.mit.edu>`_.  Once you are
   comfortable with Scratch, this book will be much easier to
   understand.

This chapter walks through few fundamental topics in Go.  You should
be able to write simple programs using Go after reading and practicing
the examples given in this chapter.  The next 3 sections revisit the
hello world program introduced in the last chapter.  Later we will
move on to few fundamental concepts in Go.

Hello World!
------------

Here is our hello world program again, you can type the below code to
your favorite text editor and save it as ``hello.go``

.. code-block:: go
   :linenos:

   package main

   import "fmt"

   func main() {
       fmt.Println("Hello, World!")
   }

You can open your command line program and run the above program like
this::

  $ go run hello.go
  Hello, World!

This command is easy to use when developing programs.  However, when
you want to use this program in production environment, it is better
to create executable binaries.  The next section briefly explain the
process of building executable binaries and running it.

Building and Running Programs
-----------------------------

You can use the `go build` command to compile the source and create
executable binary programs.  Later this executable can run directly or
copied to other similar systems and run.

.. note:: Text Files vs Binary Files

   A text file contains characters encoded in formats like ASCII or
   UTF-8.  You can use a text editor like Notepad, Notepad++, Gedit,
   Vim etc. to edit these kind of files.  A binary file is a sequence
   of bytes without line breaks (carriage return and/or line feed).
   Binary can be read by the program targeted for that particular
   format.  The executable binaries are targeted for a particular
   operating system running on a specific CPU architecture.  The Go
   source files are text files but the output generated after building
   is a binary file.

To compile (build) the hello world program, you can use this command::

  $ go build hello.go

This command produce an an executable file named `hello` in the
current directory where you run the `build` command.  And you can run
this program in a GNU/Linux system as given below.  The ``./`` in the
beginning of the command ensure that you are running the `hello`
program located in the current directory::

  $ ./hello
  Hello, World!


In Windows, the executable file name ends with `.exe`.  This is how
you can run the executable in Windows::

  C:\> hello.exe
  Hello, World!

The `go build` command produce a binary file native to the operating
system and the architecture of the CPU (i386, x86_64, arm etc.)

The example explained
---------------------

The first line is a clause defining the name of the package to which
the file belongs.  In the above hello world program, the `hello.go`
file belongs to the the `main` package because of this clause at the
beginning of the file::

  package main

A package is a collection of go program files.  Package sources can be
spread across multiple source files in a directory.  If you want to
produce an executable from your program, the name of package should be
named as `main`.  Always use lowercase letters for the package names.

The second line has kept as blank for readability.  The 3rd line is an
`import` declaration.  The `import` declaration enable accessing
external packages from the current package.  In the above example,
`fmt` package is imported like this.

.. code-block:: go

   import "fmt"

If a package is imported, it should be used somewhere in the code,
otherwise the compiler will not compile your program and it will raise
error.  If multiple packages need be imported, you can group the
imports into a parenthesized, "factored" import statement like this.

.. code-block:: go

   import (
       "fmt"
       "math"
   )

The name of the package for the built-in packages will be the name
given within quotes of the import statement.  If the import string is
a path separated by slash, then name of the package will be the last
part of the string.  For example, "net/http" package name is `http`.
For other third party vendor packages, the name should be verified
within the source code.

Names within the imported package can be referred using a dot operator
as you can see below (`fmt.Println`).  A name is considered as
exported if it begins with a capital letter.  For example, the name
`Foo` is an exported name, but `foo` is not exported.

.. sidebar:: The Go Playground

   The `play.golang.org <http://play.golang.org>`_ site can be used to
   share Go source code publicly.  You can also run the programs in
   the playground.

Again we have added one blank line after the import statement for
readability.  The fifth line starts with a function definition.  In
this case, this is a special function named `main`.  A function is a
collection of instructions or more specifically statements.  A
function definition starts with `func` keyword followed by function
name then arguments (parameters) for the function within parenthesis
and finally statements within curly brackets.  The starting curly
bracket should be in the same line where function definition started
and statements should start in the next line.There should be only one
`main` function for an executable program.

Inside the main function, we are calling the `Println` function
available inside the `fmt` package.

.. code-block:: go

   fmt.Println("Hello, World!")

The above function call is a complete statement in Go.  The `Println`
function print the string into standard output of the terminal/console
and also add a new line at the end of the string.

Fundamentals
------------

Data Types and Variables
~~~~~~~~~~~~~~~~~~~~~~~~

In the hello world example, the words that we printed, "Hello, world!"
is a data.  And the type of that data is string.  Go supports data
types like bool, string, int etc.

These are the basic data types available in Go::

  bool

  string

  int  int8  int16  int32  int64
  uint uint8 uint16 uint32 uint64 uintptr

  byte // alias for uint8

  rune // alias for int32
       // represents a Unicode code point

  float32 float64

  complex64 complex128

The keyword `var` is used to declare a list of variables.  The
variable declaration can be at package or function level.

.. code-block:: go

   var variable type
   var variable type = value
   var variable = value
   var variable1, variable2 type = value1, value2

If value is not given, a default zero value will be assigned.  The
zero value is: 0 for numeric types, false for Boolean type, and empty
string for strings.

Here is an example.

.. code-block:: go

   var name string
   var age int = 24
   var length = 36
   var width, height int = 3, 6

Inside a function, the `:=` short assignment statement can be used in
place of a `var` declaration.  The type of the value will be inferred
during the compile time.  See these two examples.

.. code-block:: go

   name := "Jack"
   age := 24

In the above example, the `name` variable will become a string type
and the age will become am int type.

For loop
~~~~~~~~

The `for` loop is the only one looping construct available in Go.

Here is an example `for` loop to get sum of values starting from 0
up to 10.

.. code-block:: go

   package main

   import "fmt"

   func main() {
       sum := 0
       for i := 0; i < 10; i++ {
           sum += i
       }
       fmt.Println(sum)
   }

The initialization and increment part are optional as you can see
below.

.. code-block:: go

   package main

   import "fmt"

   func main() {
       sum := 1
       for sum < 1000 {
           sum += sum
       }
       fmt.Println(sum)
   }

An infinite loop can be created using a `for` without any condition as
given below.

.. code-block:: go

   package main

   func main() {
       for {
       }
   }

If
~~

One of the common logic that is required for programming is branching
logic.  Based on certain criteria you may need to perform some
actions.  This could be a deviation from normal flow of your
instructions.  Go provides `if` conditions for branching logic.

Consider a simple scenario, based on money available you want to buy
vehicles.  You want to buy a bike, buf if more money is available you
also want to buy a car.

.. code-block:: go
   :linenos:

   package main

   import "fmt"

   func main() {
       money := 10000
       fmt.Println("I am going to buy a bike.")
       if money > 15000 {
           fmt.Println("I am also going to buy a car.")
       }
   }


You can save the above program in a file named `buy.go` and run it
using `go run`.  It's going to print like this::

  $ go run buy.go
  I am going to buy a bike.

As you can see, the print statement in the line number 9 didn't print.
Because that statement is within a condition block.  The condition is
`money > 15000`, which is not correct.  You can change the program and
alter the money value in line number 7 to an amount higher than 15000.
Now you can run the program again and see the output.

Now let's consider another scenario where you either want to buy a bike
or car but not both.  The `else` block associated with `if` condition
will be useful for this.

.. code-block:: go
   :linenos:

   package main

   import "fmt"

   func main() {
       money := 20000
       if money > 15000 {
           fmt.Println("I am going to buy a car.")
       } else {
           fmt.Println("I am going to buy a bike.")
       }
   }

You can save the above program in a file named `buy2.go` and run it
using `go run`.  It's going to print like this::

  $ go run buy2.go
  I am going to buy a car.

Similar to `for` loop, the `if` statement can start with a short
statement to execute before the condition.  See the example given
below.

.. code-block:: go
   :linenos:

   package main

   import "fmt"

   func main() {
       if money := 20000; money > 15000 {
           fmt.Println("I am going to buy a car.")
       } else {
           fmt.Println("I am going to buy a bike.")
       }
   }

A variable that is declared along with `if` statement is only
available within the `if` and `else` blocks.

Function
~~~~~~~~

Function is a collection of statements.  Functions enables code
reusability.  Function accepts parameters and return values.
Consider this mathematical function.

.. math::

   f(r) = 3.14r^2


This function square the input value and multiply with 3.14.
Depending on the input value the output varies.

.. digraph:: function

   "f(r)" [shape=box];
   "r" -> "f(r)" -> "y";

As you can see in the above diagram, x is the input and y is the
output.  A function in Go take input arguments and perform actions and
return values.  A simple implementation of this function in Go looks
like this.

.. code-block:: go
   :linenos:

   func Area(r float64) float64 {
       return 3.14 * r * r
   }

The function declaration starts with `func` keyword.  In the above
example, `mathFunc` is the function name which can be later used to
call the function.  The arguments that can be received by this
function is given within brackets.  The line where function definition
started should end with an opening curly bracket.  The statements can
be written in the next line on wards until the closing curly bracket.

Here is a complete example with usage of the Area function.

.. code-block:: go
   :linenos:

   package main

   import "fmt"

   func Area(r float64) float64 {
       return 3.14 * r * r
   }

   func main() {
       area := Area(5.0)
       fmt.Println(area)
   }

In the above example, the `Area` function is called in line number 10
with an argument of `5.0`.  We are using the short variable
declaration.  The type of the variable `area` will be `float64` as the
`Area` function returns with that type.

Summary
-------

We started with a hello world program and briefly explained it.  Then
this chapter introduced few basic topic in Go programming language.
The next chapters will explain the fundamental concepts in more
detail.

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
