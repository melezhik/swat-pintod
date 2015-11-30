# SYNOPSIS

[Swat](https://github.com/melezhik/swat) tests for [pinto daemon](http://search.cpan.org/perldoc?pintod).

This simple test suit could be used in various CI processes, f.e. when running tests in Travis.

# INSTALL

The simples way to enable monitoting for pintod is [sparrow](https://github.com/melezhik/sparrow.git)

    # install Sparrow and dependencies
    cpanm Sparrow

    sudo yum install curl
    sudo yum install git

    # install plugin
    sparrow
    echo swat-pintod https://github.com/melezhik/swat-pintod.git >> ~/sparrow/sparrow.list
    sparrow plg install swat-pintod


    # setup pintod application
    sparrow project foo create
    sparrow project foo add_plg swat-pintod
    sparrow project foo add_site pinto-server 127.0.0.1:3111

    # run tests
    sparrow project foo check_site pinto-server swat-pintod

  
# Swat settings

**PINTO\_PROTOCOL\_VERSION**, default value is `1`

# Example output

    $ sparrow project foo check_site pintod-server swat-pintod
    # sparrow environment initialzed at /home/vagrant/sparrow
    /home/vagrant/.swat/.cache/29435/prove/action/statistics/00.POST.t ..
    ok 1 - POST 127.0.0.1:3111/action/statistics succeeded
    # response saved to /home/vagrant/.swat/.cache/29435/prove/wUZMevEpHP
    ok 2 - output match '200 OK'
    ok 3 - output match /STATISTICS FOR THE "(\w+)" STACK/
    ok 4 - output match 'Status: ok'
    1..4
    ok
    /home/vagrant/.swat/.cache/29435/prove/action/verify/00.POST.t ......
    ok 1 - POST 127.0.0.1:3111/action/verify succeeded
    # response saved to /home/vagrant/.swat/.cache/29435/prove/86vX7UfrLA
    ok 2 - output match '200 OK'
    ok 3 - output match /\#\#\s+(Status: ok)/
    1..3
    ok
    /home/vagrant/.swat/.cache/29435/prove/action/list/00.POST.t ........
    ok 1 - POST 127.0.0.1:3111/action/list succeeded
    # response saved to /home/vagrant/.swat/.cache/29435/prove/6VvGgnWg6f
    ok 2 - output match '200 OK'
    ok 3 - output match /\#\#\s+(Status: ok)/
    1..3
    ok
    /home/vagrant/.swat/.cache/29435/prove/action/roots/00.POST.t .......
    ok 1 - POST 127.0.0.1:3111/action/roots succeeded
    # response saved to /home/vagrant/.swat/.cache/29435/prove/TxvYVi8AW4
    ok 2 - output match '200 OK'
    ok 3 - output match 'Status: ok'
    1..3
    ok
    All tests successful.
    Files=4, Tests=13,  1 wallclock secs ( 0.03 usr  0.00 sys +  0.22 cusr  0.00 csys =  0.25 CPU)
    Result: PASS
    

# COPYRIGHT

Copyright 2015 Alexey Melezhik.

This program is free software; you can redistribute it and/or modify it under the same terms as Perl itself.

# AUTHOR

Alexey Melezhik

