## Overview
We have just created our CentOS server.  We now need to apply any available system updates along with installing and configuring Docker to begin working with containers.

## Install Updates
Just like any other operating system, updates are periodically released to support new features and patch any potential security threats.  We will apply the updates first.

  1. If you have not already, connect to your remote CentOS server and login.

  2. From the command prompt, type the following to automatically install all available updates:
  ```bash
  sudo yum update -y
  ```
  3. You'll be required to re-enter your password.

  4. Depending on the number and size of available updates, this process may take a few minutes.  Now would be a good time to take a break.