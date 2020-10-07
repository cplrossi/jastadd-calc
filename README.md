# JastAdd Example Project

This is a simple modular expression translator. It uses several components,
focusing on the use of JastAdd system, with AST and aspects definition.
The scanner class is generated by the JFlex scanner generator tool, and the 
parser class is generated by the Beaver LALR parser generator tool.

External dependencies are self contained in the `tools` directory, except 
for Ant.

The Jar artifact needs the Beaver runtime to be executed; a simple method to
run Calc is provided in the `run.sh` script, as described below.

The expressions syntax is very simple, see `res/input0.asc` for an example.

The `prog` directory includes a Java driver that prints sequentially the
results for the given expressions, by using the synthesized attribute
`result` declaratively defined in `spec/Result.jrag`.

By creating new aspects (`.jrag` and `.jadd` files) the translator can be
extended with new functionalities. Furthermore, concrete and abstract syntax
can be extended or modified by editing `.jflex`, `.parser` and `.ast` files
in the `spec` directory.

The Ant `build.xml` reflects the most updated features for all external
packages we use; for example it demonstrates how to use JastAddParser
(Beaver preprocessor) and JastAdd (which have currently no built-in Ant
support).

## Building

Just run

	ant

to build a working jar file in the `jar` directory.

## Running

We provide a shell script in the top-level directory, `run.sh` to try it out.
You can use stdin and then send EOF to process, simply running:

	./run.sh

Or you can provide an input file, like `res/input0.asc` and then executing:

	./run.sh res/input0.asc
