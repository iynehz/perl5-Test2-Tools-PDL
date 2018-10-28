[![Build Status](https://travis-ci.org/stphnlyd/perl5-Test2-Tools-PDL.svg?branch=master)](https://travis-ci.org/stphnlyd/perl5-Test2-Tools-PDL)

# NAME

Test2::Tools::PDL - Test2 tools for verifying Perl Data Language piddles

# VERSION

version 0.0001\_01

# SYNOPSIS

```perl
use Test2::Tools::PDL;

# Functions are exported by default.

# Ensure something is a piddle.
pdl_ok($x);

# Compare two piddles.
pdl_is($got, $expected, 'Same piddle.');
```

# FUNCTIONS

## pdl\_ok($thing, $name)

Checks that the given `$thing` is a [PDL](https://metacpan.org/pod/PDL) object.

## pdl\_is($got, $exp, $name);

Checks that piddle `$got` is same as `$exp`.

Now this method is internally similar as
`is($got->unpdl, $exp->unpdl)`. It's possible to work with both
numeric PDLs as well as non-numeric PDLs (like [PDL::Char](https://metacpan.org/pod/PDL::Char), [PDL::SV](https://metacpan.org/pod/PDL::SV)).

# DESCRIPTION 

This module contains tools for verifying [PDL](https://metacpan.org/pod/PDL) piddles.

# VARIABLES

This module can be configured by some module variables.

## TOLERANCE

Defaultly it's same as `$Test2::Compare::Float::DEFAULT_TOLERANCE`, which
is `1e-8`. You can override it to adjust the tolerance of numeric
comparison. The behavior is like ["within" in Test2::Tools::Compare](https://metacpan.org/pod/Test2::Tools::Compare#within).

```
$Test2::Tools::PDL::TOLERANCE = 0.01;
```

You can set this variable to 0 to force exact numeric comparison. In this
case the behavior is like ["number" in Test2::Tools::Compare](https://metacpan.org/pod/Test2::Tools::Compare#number).

```
{
    local $Test2::Tools::PDL::TOLERANCE = 0;
    ...
}
```

# SEE ALSO

[PDL](https://metacpan.org/pod/PDL), [Test2::Suite](https://metacpan.org/pod/Test2::Suite), [Test::PDL](https://metacpan.org/pod/Test::PDL)

# AUTHOR

Stephan Loyd <sloyd@cpan.org>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2018 by Stephan Loyd.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
