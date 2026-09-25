Subversion client-side hooks
============================

Subversion supports server-side hooks, but lacks this functionality for the server-side.
This project contains an implementation of client-side event handler, which works by intercepting `svn` calls and passing their command line parameters to local scripts.

Add hooks to a repository
-------------------------

1. Place `bin/svn` in `$PATH` so that `bin/svn` would be called instead of `svn`.

2. In root directory of a checkout, create a directory called `.svnhooks`.

3. Add any of the following executables to `.svnhooks`:

    1. `pre-commit`: to be executed before `svn commit`

    2. `pre-update`: to be executed before `svn update`

    3. `post-checkout`: to be executed after `svn checkout`

    4. `post-commit`: to be executed after `svn commit`

    5. `post-update`: to be executed after `svn update`

Hook scripts
------------

All hook scripts are given all original command line parameters as the causing `svn` call, thus its their responsibility to intercept and parse the parameters.
