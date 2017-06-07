## Overview
Based on most of the previous steps, we are ready to build our Dockerfile.  We will mimic those steps for automating our image construction.

## Review
In preparation of writing our Dockerfile, let's review all the steps we've performed up to this point.

  1. Install the latest version of Ubuntu
  2. Update the package references
  3. Install the latest packages
  4. Install and configure Docker
  5. Install Node.js
  6. Install Node Package Manager (NPM)
  7. Download (clone) the sample website
  8. Download website dependencies
  9. Run the web server

As a reminder, since we are constructing an image, we can **ignore** step 4.  We won't need Docker installed inside of the image.

## Create the Dockerfile
Let's go ahead and create the Dockerfile contents.  We'll then examine each line below.

  1. Return to your home folder by typing at the terminal prompt, `cd ~`.

  2. Create a Dockerfile using the `nano` text editor by typing the following: `nano Dockerfile`.  Nano is reminiscent of the old DOS editor.  Of course, you can you `vim` instead if you are comfortable in doing so.  
  **NOTE** 'Dockerfile' is case-sensitive.  

  3. Enter the following without the line numbers. The line numbers are provided for reference below.
  ```bash
  1   FROM ubuntu:latest
  2   MAINTAINER Your Name <you@yourcompany.com>
  3
  4   RUN apt-get update
  5   RUN apt-get upgrade
  6   RUN apt-get install -y nodejs
  7   RUN apt-get install -y npm
  8   RUN ln -s /usr/bin/nodejs /usr/bin/node
  9   RUN apt-get install -y git
  10
  11  RUN git clone https://github.com/AzureWorkshops/samples-simple-nodejs-website.git /var/www
  12  WORKDIR /var/www
  13  RUN npm i
  14
  15  EXPOSE 8080
  16
  17  CMD node /var/www/index.js
  ```

  4. To save, **Ctrl+O**

  5. To exit, **Ctrl+X**

#### Explanation
First, if you remember from the previous steps, we prepended each command with `sudo` to allow the command to be executed with elevated privileges.  By default, all Docker images execute under the identity of the built-in superuser account `root`.  Therefore, we can omit the `sudo`.

**Line 1:** Specifies the base image, including the tag, with which we're starting. In our case, we are using the minimal Ubuntu OS as the base image.

**Line 2:** Specifies the owner of the image with their email address.

**Lines 4-8:** The commands we executed earlier in this workshop that update the system and installs Node.js.

**Line 9:** We were not required to install `git` in our virtual machine. However, because the base image of Ubuntu doesn't include `git` by default, we need to install it manually.

**Line 11:** Downloads (clones) the sample website into the `/var/www` local folder.

**Line 12:** `WORKDIR` is how you change the current directory (compared to `cd`) in a Dockerfile. We are changing to the website home directory.

**Line 13:** Install the website's dependencies.

**Line 15:** Our website server is programmed to use port 8080.  Therefore, similar to a firewall in the image, we open, or _expose_, the port to the outside host.  We will bind to this open port later when we run a container based on this image.

**Line 17:** This starts our web server.  We could have used the `RUN` directive, but the `CMD` directive is designed to execute our long-running process.  While, technically, we could have multiple `CMD` lines in the Dockerfile, the Docker build will ignore all `CMD` lines except the last one.

That's it! That's all there is to creating a Dockerfile.