## Overview
Now that we have the host machine configured for Docker, we're going to begin building our web server.  Keep in mind that this virtual machine is serving two purposes: 1) our Docker host; and, 2) our temporary web server until our image is built.

## Install Node.js
Node.js is a JavaScript execution engine that allows us to write server-side JavaScript and utilize it like any other executable file.  With Node.js, we will host a very simple web server.

#### Download and Install Node.js Runtime
The Node.js runtime is what is responsible for hosting and executing our JavaScript. 

From the terminal prompt, type:
```bash
sudo apt-get install -y nodejs
```

#### Download and Install NPM
NPM is an abbreviation for _Node Package Manager_.  NPM allows us to install Node.js dependencies for our applications.

At the prompt, type:
```bash
sudo apt-get install -y npm
```

#### Create Symbolic Link
In Linux, a symbolic link is nothing more than a 'virtual pointer' to a file.  It's a way to give a file an alias.  For us, we going to do two things with a symbolic link.  First, we're going to get `nodejs` an alias.  Second, we're going to make the executable globally available so that it can be called from any folder.

At the prompt, enter:
```bash
sudo ln -s /usr/bin/nodejs /usr/bin/node
```

This will create a pointer called `node` that points to `nodejs`.  We can then execute Node.js via either command.  However, `node` is the common name to use.

#### Verify Installation
Let's make sure our installation was successful.

At the prompt, type:
```bash
node -v
npm -v
```

You should receive version numbers for both commands.

## Add Build Dependencies
Some Node.js libraries have outside dependencies that aren't necessarily installed in Ubuntu by default.  Let's install those now.

At the terminal prompt, type:
```bash
sudo apt-get install build-essential
```

We've now successfully completed the installation of Node.js and the Node Package Manager.