NodeJS libgit2 bindings
=======================

Created by Tim Branyen [@tbranyen](http://twitter.com/tbranyen)

Currently under active development, `nodegit2` will provide asynchronous native bindings to the `libgit2` C API.

Building
--------

### Dependancies ###
To use `nodegit2`, you will need to have the `libgit2` shared library in `/usr/local/lib` and the `NodeJS`
framework installed, you will also need `git` installed and accessible from your `PATH` to fetch any `vendor/` addons.

### Linux/Mac OS X/BSD Variants ###
__ You can skip this step and `nodegit2` will automatically fetch and install a fresh copy of `libgit2` for you. __

#### Install `libgit2` from [http://libgit2.github.com/](http://libgit2.github.com/) ####

    [tim@thinkpad Projects]$ cd libgit2
    [tim@thinkpad libgit2]$ ./configure
    [tim@thinkpad libgit2]$ make 
    [tim@thinkpad libgit2]$ sudo make install

#### Install `NodeJS` from [http://nodejs.org/](http://nodejs.org/) ####

    [tim@thinkpad Projects]$ cd node-v0.4.0
    [tim@thinkpad node-v0.4.0]$ ./configure
    [tim@thinkpad node-v0.4.0]$ make 
    [tim@thinkpad node-v0.4.0]$ sudo make install

#### Install `nodegit2` by cloning source from __GitHub__ and running the `make` and `make install` commands.  (Future will be on NPM) ####

    [tim@thinkpad Projects]$ git clone git@github.com:tbranyen/nodegit2.git
    [tim@thinkpad Projects]$ cd nodegit2
    [tim@thinkpad nodegit2]$ make
    [tim@thinkpad nodegit2]$ make install

### Windows via Cygiwn ###

#### `nodegit2` has been compiled and tested to work with the setup required to build and run `NodeJS` itself ####

Instructions on compiling `NodeJS` on a Windows platform can be found here:
[https://github.com/ry/node/wiki/Building-node.js-on-Cygwin-(Windows)](https://github.com/ry/node/wiki/Building-node.js-on-Cygwin-(Windows\))

Example API Usage
-----------------

### Creating and reading a repository ###

    var git = require('git2');
    
    // Create a bare repository in the working directory
    git.repo().init( '.git', true, function( err, path, is_bare ) {
        // Read the current repository
        git.repo( '.git', function( err, path ) {
            // ...
        });
    });


Running tests
-------------

__ Ensure the submodules `nodeunit` and `rimraf` are located in the `/vendor` subdirectory. __

If they are not, `cd` into the `nodegit2` dir and run the following git commands to automatically fetch them:
    [tim@thinkpad Projects]$ cd nodegit2
    [tim@thinkpad nodegit2]$ git submodule init
    [tim@thinkpad nodegit2]$ git submodule update 

Then simply run `make unittest` in the project root.

Example of building `nodegit2` bindings and running tests:
    [tim@thinkpad Projects]$ cd nodegit2
    [tim@thinkpad nodegit2]$ make
    [tim@thinkpad nodegit2]$ make unittest 

You will most likely install `nodeunit` and `rimraf` via `npm` or make an alias to the `nodeunit` binary in `/vendor`.

Release information
-------------------

### v0.0.1: ###
    * 1:1 mapping of libgit2 read methods
    * An API that can be easily extended with convenience methods in JS

### v0.0.2: ###
    * Write capabilities

### v0.0.3: ###
    * Custom odb backend

Getting involved
----------------

If you find this project of interest, please document all issues and fork if you feel you can provide a patch.  Testing is of huge importance; by simply running the unit tests on your system and reporting issues you can contribute!
