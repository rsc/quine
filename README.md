# Quine

In logic, [Quine's paradox](https://en.wikipedia.org/wiki/Quine%27s_paradox)
shows that a sentence that is not directly self-referential can nonetheless be paradoxical.
In particular, this sentence asserts that the sentence itself is false:

> “yields falsehood when preceded by its quotation” yields falsehood when preceded by its quotation.

In computing, a _quine_ is a program that prints its own source code,
usually by using the same trick as Quine's sentence.
For example, this Scheme program is a quine:

	((lambda (x) `(,x ',x))
	'(lambda (x) `(,x ',x)))

Ken Thompson's [Turing Award lecture](https://web.archive.org/web/20130314092153/http://cm.bell-labs.com/who/ken/trust.html)
is all about quines and computer security.

This Git repository holds the source code to some other quines.
Most are direct uses of the quotation pattern, like the two above, but a few
are worth additional notes.

## Shell

[qshell](qshell) takes advantage of the Unix kernel to arrange the quotation.
When the kernel is asked to run with a program beginning with `#!`,
it instead runs the program named by the remainder of that line,
with the name of the program file itself as an additional argument.
The file [qshell/quine](qshell/quine) is a single line:

	#!/bin/cat

To run this program, the kernel would execute:

	/bin/cat qshell/quine

which will in turn print the source code.

## Zip

The [qzip](qzip) directory contains compressed archives that manage
to write a quine using the DEFLATE compression method's bytecode programs.
See [Zip Files All The Way Down](https://research.swtch.com/zip) for details about how they were constructed.

