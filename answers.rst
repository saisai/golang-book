.. _answers:

Answers
=======

Chapter 2
---------

**Problem 1:** Write a function to check whether the first letter in a
given string is capital letters in English (A,B,C,D etc).

.. code-block:: go

   package main
 
   import "fmt"
 
   func StartsCapital(s string) bool {
       for _, v := range "ABCDEFGHIJKLMNOPQRSTUVWXYZ" {
           if string(s[0]) == string(v) {
               return true
           }
       }
       return false
   }
 
   func main() {
       h := StartsCapital("Hello")
       fmt.Println(h)
       w := StartsCapital("world")
       fmt.Println(w)
   }

**Problem 2:** Write a function to generate Fibonacci numbers below a
given value.

.. code-block:: go

   package main

   import "fmt"

   func Fib(n int) {
       for i, j := 0, 1; i < n; i, j = i+j, i {
           fmt.Println(i)
       }

   }

   func main() {
       Fib(200)
   }
