## Overview
Even though we've installed _system_ dependencies, our website has a couple of library dependencies that we need to install.  We'll also ensure that the website is functioning correctly, before we proceed to build our Dockerfile.

## Download Website Dependencies
We'll need to enter into the website's main folder to install the dependencies.

Type the following into the terminal:
```bash
cd /var/www
sudo npm i
```

You should see a number of progress bars displayed as dependencies are downloaded followed by what looks like a folder hierarchy.

## Test Our Website
The first thing we need to do is run our web hosting server which is handled by Node.js. If we ran this normally from the command-line, it would block all other input.  We would then have to open a second terminal to test our website.  Instead, we're going to run our web server in the background as a detached process.

At the terminal prompt, type:
```
sudo node index.js &
```

**NOTE:** The ampersand at the end of the line instructs the system to run the preceeding command in the background.  When we construct our Dockerfile, we will omit the ampersand so that the process runs in the foreground and creates a long-running process that keeps our container 'alive'.

When you run this command, a number is outputted to the screen. This number refers to a _process id_ (pid). Keep this number handy as we'll use it below to 'kill' the background process.

Additionally, you should see a message stating that our 'server is listening on 8080'.

Test that the web server is returning our site by typing the following:
```bash
curl http://localhost:8080/
```

If all is successful, you should receive some HTML source code back.

#### Stop the Background Process
We don't need the website running any longer now that we know it works.  Additionally, if we kept it running, it's use of the port 8080 could create potential conflicts if another service (e.g. container) is needing that port.

Referring to the process id (pid) above, execute the following command with your id:
```bash
sudo kill <pid>
```

If successful, you should see the following confirmation message:
```bash
[1]+  Exit 143                  sudo node index.js
```

Building our web server has been successful. We are now ready to move forward and replicate our work in building out an image.