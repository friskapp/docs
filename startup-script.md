# Install Frisk using A start-up script

You can install Frisk easily on DigitalOcean or Vultr using a start up script that we made ... 

> {note} After installation complete you should change your [mail configurations](./after-installing-frisk#mail-configurations)

 <a name="what-startup-script"></a>
## [What is startup script](#what-startup-script)
It's a setup file that is written to install and configure a server without the need to do it manually. We made a wizard that auto-generate a startup script to install Frisk (head to [frisk.app/setup](/setup)) 

 <a name="how-to-use-it-with-digital-ocean"></a>
## [How to use it with DigitalOcean](#how-to-use-it-with-digital-ocean)
- Create new droplet
![do-1](/images/docs/do-startup-script-1.png)
- Select image: Ubuntu 18.04 or any new LTS version.
![do-1](/images/docs/do-startup-script-2.png)
- From available settings: check "Enable User Data"
![do-1](/images/docs/do-startup-script-3.png)
- Paste the generated script you got from [frisk.app/setup](/setup) into User Data field then save it.
![do-1](/images/docs/do-startup-script-4.png)
- Lastly Create your droplet.
![do-1](/images/docs/do-startup-script-5.png)

 <a name="how-to-use-it-vultr"></a>
## [How to use it with Vultr](#how-to-use-it-with-vultr)
- Deploy new server
- Choose Server Type: Ubuntu 18.04 or any new LTS version.
- Click "Add New" from Startup Script
![vultr-1](/images/docs/vultr-startup-script-1.png)
- Type any name in Name field and keep "boot" in type field, then paste the generated script you got from [frisk.app/setup](/setup) into script field then save it.
![vultr-1](/images/docs/vultr-startup-script-2.png)
- Lastly deploy your server.

