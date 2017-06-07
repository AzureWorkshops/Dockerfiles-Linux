## Overview
Now that we have the host machine configured for Docker, we're going to begin building our web server.  Keep in mind that this virtual machine is serving two purposes: 1) our Docker host; and, 2) our temporary web server until our image is built.

## Install Node.js
Node.js is a JavaScript execution engine that allows us to write server-side JavaScript and utilize it like any other executable file.  With Node.js, we will host a very simple web server.

#### Add EPEL Repository
One installation method for installing Node.js uses the EPEL (Extra Packages for Enterprise Linux) repository that is available for CentOS and related distributions.

To gain access to the EPEL repo, you must modify the repo-list of your installation. Fortunately, we can reconfigure access to this repository by installing a package available in our current repos called `epel-release`.
```bash
sudo yum install -y epel-release
```

#### Download and Install Node.js Runtime
The Node.js runtime is what is responsible for hosting and executing our JavaScript. 

From the terminal prompt, type:
```bash
sudo yum install -y nodejs
```

#### Download and Install NPM
NPM is an abbreviation for _Node Package Manager_.  NPM allows us to install Node.js dependencies for our applications.

At the prompt, type:
```bash
sudo yum install -y npm
```

#### Verify Installation
Let's make sure our installation was successful.

At the prompt, type:
```bash
node -v
npm -v
```

You should receive version numbers for both commands.

We've now successfully completed the installation of Node.js and the Node Package Manager.