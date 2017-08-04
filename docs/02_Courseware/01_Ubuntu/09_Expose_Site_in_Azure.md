## Overview
The final part of this workshop is to practice exposing a container service outside of Azure. We're going to create a simple web server and access it from our local machine.

## Network Security Group (NSG)
Now that our web server is running, let's make it available outside of Azure.

When we created our Ubuntu virtual machine, we accepted the defaults, including the default settings for our NSG.  The default settings only allowed SSH (port 22) access. We need to add a rule to our NSG to allow HTTP traffic over our three ports (8080-8082) so that we can access all three containers.

  1. If you are not still there, go back to the Azure portal and navigate to the settings of your Ubuntu virtual machine.

  2. In the left menu, click on **Network interfaces** <img src="https://raw.githubusercontent.com/AzureWorkshops/images/master/icons_network_interfaces.jpg" class="inline"/>.

  3. This will open the _Network Interfaces_ blade for your Ubuntu virtual machine. Click on the singular, listed interface.

  4. In the left menu, click on **Network security group** <img src="https://raw.githubusercontent.com/AzureWorkshops/images/master/icons_network_security_group.jpg" class="inline"/>.

  5. This will list the currently active NSG.  In our case, it should be the NSG that was created with our virtual machine - **dockerfile-ubuntu-nsg**.  Click on the NSG (**NOTE:** Click on the actual NSG link, **NOT** on **Edit**).

  6. In the left menu, click on **Inbound security roles** <img src="https://raw.githubusercontent.com/AzureWorkshops/images/master/icons_inbound_security_rules.jpg" class="inline"/>.

  7. At the top of the blade, click **Add** <img src="https://raw.githubusercontent.com/AzureWorkshops/images/master/icons_add.jpg" class="inline"/>.

  8. Enter the following configuration:

      * Name: **allow-http**
      * Priority: **1010**
      * Source: **Any**
      * Service: **Custom**
      * Protocol: **Any**
      * Port range: **8080-8082**
      * Action: **Allow**

  9. Click **OK**.

This should only take a couple of seconds.  Once you see the rule added, open a new browser and navigate to the IP address of your Ubuntu virtual machine, including the port number.  The IP address used in this workshop's screen shots is **52.170.85.112** (your IP address will be different).  Using the aforementioned IP address, I would direct my browser to **http://52.170.85.112:8080**.  I would also test the other 2 port numbers (e.g. 8081, 8082). You should see the 'Hello World' page at all three URL/port combinations.