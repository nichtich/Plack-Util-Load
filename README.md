# NAME

Plack::Util::Load - load PSGI application from class, file, or URL

# STATUS

[![Build Status](https://travis-ci.org/nichtich/Plack-Util-Load.png)](https://travis-ci.org/nichtich/Plack-Util-Load)
[![Coverage Status](https://coveralls.io/repos/nichtich/Plack-Util-Load/badge.png)](https://coveralls.io/r/nichtich/Plack-Util-Load)
[![Kwalitee Score](http://cpants.cpanauthors.org/dist/Plack-Util-Load.png)](http://cpants.cpanauthors.org/dist/Plack-Util-Load)

# SYNOPSIS

    use Plack::Util::Load;

    $app = load_app('app.psgi');
    $app = load_app; # equivalent

    $app = load_app(5000); 
    $app = load_app(':5000');
    $app = load_app('localhost:5000');
    $app = load_app('http://localhost:5000/');

    $app = load_app("http://example.org/");

    $app = load_app('MyApp::PSGI');

# DESCRIPTION

This module exports the function `load_app` to load a [PSGI](https://metacpan.org/pod/PSGI) application from
file, class name, URL, or port number on localhost. The function will return a
code reference or die. A typical use case is the application of tests. To give
an example, the following test runs on the PSGI application `MyApp::PSGI` by
default. After deployment the same test can be executed with environment
variable `TEST_URL` set to the port or URL where the app is installed:

    use Test::More;
    use Plack::Test;
    my $app = load_app( $ENV{TEST_URL} || 'MyApp::PSGI', verbose => 1 );

    test_psgi $app, sub {
        my $cb = shift;
        ...
    };

    done_testing;

# OPTIONS

The additional options `verbose` can be passed to log HTTP requests and
errors:

    $app = load_app( 'http://example.org/', verbose => 1 ); 

The default value for this option can be set with
`$Plack::Util::Load::VERBOSE`.

# SEE ALSO

[Plack::Util](https://metacpan.org/pod/Plack::Util), [Plack::App::Proxy](https://metacpan.org/pod/Plack::App::Proxy)

# COPYRIGHT AND LICENSE

Copyright Jakob Voss, 2015-

This library is free software; you can redistribute it and/or modify it under
the same terms as Perl itself.
