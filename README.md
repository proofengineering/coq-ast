AST Coq Plugin
==============

[![Build Status](https://api.travis-ci.org/proofengineering/coq-ast.svg?branch=master)](https://travis-ci.org/proofengineering/coq-ast)

A Coq plugin for printing semi-canonical abstract syntax trees (ASTs) with unique kernel names or digests of such trees.

Requirements
------------

- [`Coq 8.5`](https://coq.inria.fr/coq-85)
- [`camlp5`](https://camlp5.github.io)

Building
--------

The easiest way to install the plugin is via [OPAM](http://opam.ocaml.org/doc/Install.html):

```
opam repo add proofengineering-dev http://opam-dev.proofengineering.org
opam install coq-ast
```

To build the plugin manually, run `make` in the root directory. Then, to install it, run `make install`.

Usage Examples
--------------

```coq
(* require and import plugin *)
Require Import AST.AST.

(* constants to analyze *)
Require Import List.

(* print list of identifier ASTs as JSON to stdout *)
AST map filter.

(* print list of identifier ASTs as JSON to file *)
AST "asts.json" map filter.

(* print MD5 digests of identifiers as JSON to stdout *)
Digest MD5 map filter.

(* print Adler32 digests of identifiers as JSON to stdout *)
Digest ADLER32 map filter.

(* print MD5 digests of identifiers as JSON to file digests.json *)
Digest MD5 "digests.json" map filter.

(* print ASTs for all identifiers in modules List and Logic as JSON to file asts.json *)
ModuleAST "asts.json" Logic List.

(* print MD5 digests for all identifiers in modules List and Logic as JSON to file digests.json *)
ModuleDigest MD5 "digests.json" Logic List.
```
