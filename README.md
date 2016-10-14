# SUPER Android Analyzer #

[![Build Status](https://travis-ci.org/SUPERAndroidAnalyzer/super.svg?branch=develop)](https://travis-ci.org/SUPERAndroidAnalyzer/super)
[![Build status](https://ci.appveyor.com/api/projects/status/7xuikqyne4a2jn7e/branch/develop?svg=true)](https://ci.appveyor.com/project/Razican/super/branch/develop)
[![Coverage Status](https://coveralls.io/repos/github/SUPERAndroidAnalyzer/super/badge.svg?branch=develop)](https://coveralls.io/github/SUPERAndroidAnalyzer/super?branch=develop)

<img src="vendor/results_template/img/logo.png" alt="SUPER Android Analyzer logo" title="SUPER Android Analyzer" width="150">

*Secure, Unified, Powerful and Extensible Rust Android Analyzer*

SUPER is a command-line application that can be used in Windows, MacOS X and Linux, that analyzes
.apk files in search for vulnerabilities. It does this by decompressing APKs and applying a series
of rules to detect those vulnerabilities.

But, why create a new analyzer? Is it not enough with MobSF, Qark, Androbugs…? Well, we think it's
not enough. All of them have two main issues we wanted to fix: They are written in Java or Python
and they are not easily extensible. They are not meant to be used by businesses directly working in
Android analysis, and don't put that kind of functionality first.

Our approach solves those issues in different ways: We first decided to use **Rust** as our
programming language. The language developed openly by Mozilla Foundation gives us lots of
utilities to work with regular expressions, files etc. and, most importantly, it enables us to
create a secure software that does not depend in *JVM* or *JIT* compilers. With Rust, stack
overflows, segmentation faults etc. are directly not possible, which makes sense in a security
centered application. And it also gives us enough power to do efficient analysis, giving us the
option to automate it in high volume. This is given by Rust zero-cost abstractions, that gives us
an efficiency only comparable to C/C++.

And secondly, we decided to make the software 100% extensible: All rules are centered in a
`rules.json` file, and each company or tester could create its own rules to analyze what they need.
It's also modular, so that new developments can easily add new functionality. Finally, a templating
system for results reports (that will be improved in future updates) gives users the ability to
personalize the report.

It also gives great code review tools, directly in the HTML report, so that anyone can search
through the generated code with syntax highlighting for even better vulnerability analysis.

## Installation ##

We have released some binaries in the [download page](http://superanalyzer.rocks/download.html) for
Windows (8.1+), and Linux, and we are
[creating MacOS X packages](https://github.com/SUPERAndroidAnalyzer/super/issues/18). We only have
64-bit packages for now. If you need to use SUPER in a 32-bit system, or in MacOS X, you will need
to [compile SUPER from source](http://superanalyzer.rocks/download.html#compile-from-source). For
that, you will need to install **Rust** with [rustup.rs](https://www.rustup.rs/).

*Note: It requires Java 1.7+ and OpenSSL to run.*

## Usage ##

SUPER is very easy to use. Just download the desired *.apk* into the *downloads* folder (create
that folder if necessary) and use the name as an argument when running the program. After the
execution, a detailed report will appear in the *results* folder with that application name. There
are a few usage options available:

```
USAGE:
    super [FLAGS] <package>

FLAGS:
        --bench      Show benchmarks for the analysis.
        --force      If you'd like to force the auditor to do everything from the beginning.
        --open       Open the report in a browser once it is complete.
    -h, --help       Prints help information
    -q, --quiet      If you'd like a zen auditor that won't talk unless it's 100% necessary.
    -V, --version    Prints version information
    -v, --verbose    If you'd like the auditor to talk more than necessary.

ARGS:
    <package>    The package string of the application to test.
```

## Contributing ##

Everybody is welcome to contribute to SUPER. Please check out the [SUPER Contribution Guidelines](https://github.com/SUPERAndroidAnalyzer/super/blob/develop/contributing.md)
for instructions about how to proceed.

## License ##

This program is free software: you can redistribute it and/or modify it under the terms of the GNU
General Public License as published by the Free Software Foundation, either version 3 of the
License, or (at your option) any later version.
