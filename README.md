# NAME

Plack::Util::Load - load PSGI application from class, file, or URL

# SYNOPSIS

    use Plack::Util::Load;

    $app = load_app('app.psgi');
    $app = load_app;

    $app = load_app(5000); 
    $app = load_app(':5000');
    $app = load_app('localhost:5000');
    $app = load_app('http://localhost:5000/');

    $app = load_app("http://example.org/");

    $app = load_app('MyApp::PSGI');

# DESCRIPTION

This module exports the function `load_app` to load a [PSGI](https://metacpan.org/pod/PSGI) application from
file, class name, URL, or port number on localhost. The function will return a
code reference or die.

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
