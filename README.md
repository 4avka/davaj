# davaj

While everyone is pressuring, coercing and generally nagging Google's Golang team to turn Go into Java, this is the opposite. Go v255.255.255 (ie, -1.-1.-1)

## What is this nonsense?

Go is a fantastic language, of all the ones in common use, it is the nearest thing to my personal ideal. I am a bit old-school, and in my youth I learned MS Basic and 68000 assembler. I don't like the way Go is Going, although the the epic Three (Rob Pike, Ken Thompson and Robert Griesemer are fighting off the clamorings for all the things that would make Go indistinguishable from Java, C++ and C#, obviously they have to compromise to some extent.

This project will start out as a preprocessor, and a greatly simplified standard library, and here is the list of main points that will be covered in the revision:

- Elimination of interface method sets
    These are so minimally useful, and so easily abused, they really don't belong in the language if it is consistent in its aim to eliminate things that lead to bad, unreadable and unmaintainable code, as well as eliminating the wonderful fast compilation that makes it almost feel like Python in its interactivity
- Combine if and switch statements into a single, compact switch-like structure
    They are all the same, in the end, and it will maintain the optional first clause that can declare in-scope variables for all sub-blocks of the statement. The type switch will of course be retained, as it enables the only rational form of dynamic typing - where the code knows and can handle anything that might be there
- Elimination of package level variables
    Except for functions and constants. The biggest reason for this has to do with the fact that package level variables obstruct the use of concurrency
- Methods can be declared in-scope on any type accessible in a package. Currently one is limited to declaring them within the same package as the type definition. One can get around this by declaring a new local type in the current spec, but there is no real reason to clutter the code up with this redundant nonsense. A simple substitution engine could move all receivers to first parameter so easily, it is an unnatural and obstructive restriction.
- Function type signature aliasing
    Especially if one is using the composite pattern, the declaration of new closures relating to an existing type signature such as contained within a struct, is a lot of verbosity. The @ symbol is unused in the language and allows instant programmatic differentiation between a type name `packagename.Typename`
- Elimination of the concept of public/private variables
    If someone is so inclined to dig around in the source code and wants to poke hornets' nests by directly addressing variables, so be it. As in above the elimination of interface method sets and permission to add methods to existing types, the replacement for interface methods is the declaration of structs containing methods. Instead of this 'does not implement interface' issue, which is quite opaque and unapproachable to the especially beginner, one simply ends up with a nil panic trying to call the method, which alerts the programmer to the non-existence of an implementation, in a more obvious way. Forcing the use of capitalisation effectively halves the possible namespace for a set of functions bound to a data structure, and on the other side, by making the programmer define the methods alongside the values in a compound type, one has a more intuitive object looking notation without the complexity of compilation, and the extra advantage that overloading implementations, even chaining them, can be performed easily, eliminating the issue greatly complained about in the lack of OOP features in Go. They are then available instead in the manner implemented in functional languages.

This is a work in progress, the specification is far from complete, this is just an overview of the many facets of the Go language that in my opinion need to be simplified and at the same time made more powerful.

For now this is just blue sky. I anticipate that it will be a couple of years before I can actually do something about this, maybe 5 before I can get enough collaborators to actually build it, but it will morph out of the Go 1.0 codebase and standard library.
