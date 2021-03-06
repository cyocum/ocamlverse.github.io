---
tags: [ecosystem]
---

# Standard Libraries

OCaml comes with its own [Standard Library](https://caml.inria.fr/pub/docs/manual-ocaml/libref/).
Most OCamlers, however, agree that the built-in standard library is problematic: it's not comprehensive
enough, and it uses outmoded patterns, such as using exceptions rather than error types. The community has
had trouble expanding the library due to namespacing issues.

* Note, however, that since OCaml 4.07, the namespace issue has mostly been fixed, and the standard library is
being expanded to cover more missing use-cases. Additionally, many functions that threw exceptions now have
no-exception counterparts.*

In the absence of a comprehensive standard library, several competitors developed. Due to OCaml's support for
modularity, each can be swapped out for the other wholesale.

* The [standard library](https://caml.inria.fr/pub/docs/manual-ocaml/libref/) offers a selection of functional
data structures (List, Map) and imperative data structures (Array, Queue, Stack). Many of the functions throw
an exception rather than returning an option type. The library also includes the Unix module, which, despite its
name, has many functions that work on Windows. The Unix module is a catch-all for many IO-processing functions.
Also included is the Format module for pretty printing and the Str module for regular expression matching, among
other useful modules.
* [Base](https://github.com/janestreet/base)  is Jane Street Capital's internally developed, battle-tested
standard library implementation. It's also the library covered by the 2nd edition of Real World OCaml. The library
doesn't try to extend the basic standard library, but instead chooses its own design. To the users, the most obvious
difference compared to the other standard library options will be the choice of having labels in function arguments,
similar to the ListLabels, ArrayLabels, etc modules in the standard library. Additionally, Base does not use
polymorphic comparison anywhere in its API.
* [Containers](https://github.com/c-cube/ocaml-containers)  is a lightweight and modern-style standard library which
extends the standard library with additional functionality while applying more modern design concepts. As of version
2.0, Containers does not use polymorphic comparison anywhere.
* [Core](https://github.com/janestreet/core)  is Jane Street's expanded standard library, sitting on top of Base.
Core is more comprehensive than Base.
* [Batteries Included](https://github.com/ocaml-batteries-team/batteries-included)  is a mature, full-featured
standard library, taking the approach of extending the standard library with additional functionality rather than
replacing it wholesale. It includes many data structures and algorithms. Note that Containers came about as a
split-off from Batteries.
* [BOS - Basic OS Interaction](https://github.com/dbuenzli/bos) is an OS interaction layer containing many elements,
including file manipulation, command line argument parsing, etc. It fulfills one of the main functionalities of a
standard library, that being I/O.

## Recommendations
Several non-compatible modern alternatives are recommended:

* Containers + stdlib + BOS: Containers is a modern extension of the stdlib, and extends it in powerful ways.
For OS interaction, BOS is a great fit.
* Base + Core: The Jane Street standard libraries eschew the conventions of the stdlib, and present an
alternative, powerful combination that works particularly well with other Jane Street libraries.
