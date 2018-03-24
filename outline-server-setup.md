How to setup an Outline VPN Server on Ubuntu 16.04 Server

This guide will show you how to install Outline Server on an Ubuntu 16.04 Server, use Outline Manager for Windows and connect to your Outline Server on Windows and Anroid.

# Install Outline Manager for Windows

For now, Outline Manager only support Windows and Linux. I'll show you how to do on Windows.

Use this link to download Outline Manager for Windows
~~~~
https://raw.githubusercontent.com/Jigsaw-Code/outline-releases/master/manager/Outline-Manager.exe
~~~~

# Install Outline Server

## Requirement
* An Ubuntu 16.04 Server
* Sudo non-root user
* Docker installed

Mainly, there are two ways to install Outline Server on an Ubuntu Server.

## Simple way

Install Outline Manager on your computer, login to Digital Ocean using your own account and follow the instruction on the screen.

## Die Hard

If you wanna use your own server or just don't like DO, this is for you.

### Install Docker

You will need to install Docker on your server first. If not, run the following command:

~~~~
sudo curl -sS https://get.docker.com/ | sh
~~~~

### Install Outline

All you need to do is run this command:

~~~~
sudo wget -qO- https://raw.githubusercontent.com/Jigsaw-Code/outline-server/master/src/server_manager/install_scripts/install_server.sh | bash
~~~~

When you finished, the output should be like:

~~~~
Please copy the following configuration to your Outline Manager:
{ 
  "apiUrl": "https://1.2.3.4:1234/XXXXXXXXXXXX", 
  "certSha256": "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX" 
}
~~~~

Just leave it there. You will need these information in the next step. That's enough for the server side. Now, we will move to the client side.

### Get the access key

1. Open Outline Manager. Scrool down to the Advanced Mode and click on **Get started** button;
2. Copy everything within (include) the {}  of the key on your server at the last step and paste it the field at the next screen;
3. Click **Done**;
4. There is a key automatically created for you (named 'My Access Key'). If you click 'Get Connected' next to it, you will be walked through how to download the appropriate client for your platform without needing to open up a new page. (Thanks to [r/sandrigo](https://www.reddit.com/user/sandrigo);
5. If you want to get a new key to share with your friends, Click **Add key**, and you will get something like "Key 1", click **Share**, it will show you the link to get the access key, click **Copy to Clipboard** and send it to your friends. (HEADS UP: EVERYONE WHO HAS THE LINK WILL BE ABLE TO CONNECT TO YOUR SERVER)

~~~~
https://s3.amazonaws.com/outline-vpn/index.html#/invite/ss//XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
~~~~

5. Paste it to browser
6. Click on **Connect this device**, it will show you the key, click **Copy** to get the key.

### Connect to Outline

For now, Outline only support Android, Windows and Chrome OS. Outline for iOS and MacOS is coming soon.

**Windows**

~~~~
Windows 7.0+
~~~~

Use this link to download Outline for Windows
~~~~
https://raw.githubusercontent.com/Jigsaw-Code/outline-releases/master/client/Outline-Client.exe
~~~~

1. Install Outline for Windows to your computer. Open it.
2. Click on + button at the upright corner.
3. Paste the key you copied above to the field and click **Add server**
4. Click **Connect** at the next screen, wait until it connected.
5. Enjoy.

Note: If it shows "key invaild", just try to reconnect several times.

**Android**

~~~~
Android 5.0+
~~~~

~~~~
https://play.google.com/store/apps/details?id=org.outline.android.client
https://github.com/Jigsaw-Code/outline-client/releases
~~~~

Download Outline for Android from the CH Play or Github (You should choose the version with `Latest release` tag) and repeat the steps for Windows above.

# Setting Outline to work with Proxy SwitchyOmega (Advanced)

By default, Outline uses different ports everytime you reconnect, then it's pretty hard to use Proxy SwitchyOmega. But if you really want to, so here is the way:

**HEADS UP: YOU WILL NEED TO CHANGE THE PORT MANUALLY EVERYTIME YOU RECONNECT OUTLINE**

1. Firstly, you need to install the Proxy SwitchyOmega extension [for Chrome](https://chrome.google.com/webstore/detail/padekgcemlokbadohgkifijomclgjgif) or Proxy SwitchyOmega plugin [for Firefox](https://addons.mozilla.org/en-US/firefox/addon/switchyomega/);
2. Go to Proxy SwitchyOmega Options (Normally, right click on the Proxy SwitchyOmega icon in your browser > Options);
3. Choose **New Profile**, give it a name (Here I use Outline VPN), select **Proxy Profile** and click Create.
4. On the next screen, at Proxy servers, select HTTP from the scroll down menu, fill in 127.0.0.1 in the Server field.
5. Open **Internet Options** in your computer (**Open Network and Sharing Center > Internet Options**), then select **Connections > LAN Settings**, look at **Proxy Server**, you will find the port you need.
6. Back to Proxy SwitchyOmega Options, fill that port to the Port field, click Apply changes.
7. Choose **New Profile**, give it a name (Here I use Auto - Outline), select **Switch Profile** and click Create.
8. Click Add a rule lists, from Rule list rules, select Outline VPN.
9. At Rule List Config section, select Auto Proxy, and paste the link below to Rule List URL field, click Apply changes, and then click Download Profile Now.
10. Now, click on Proxy SwitchyOmega icon in your browser, choose Auto - Outline. By this way, you will save lots of traffic on your VPN server, and get the faster speed when connect to sites you don't want to or don't need to connect via a VPN.

# Conclusion

## Pros
- Easy to setup
- Simple and friendly UI client
- Secure
- From Google, haha.

## Cons
- Only supports Windows and Android for now

# One more thing
- This guide is free for use. But if you want to get me some coffee, just send it to my Paypal: https://paypal.me/pmtuan. Much appreciate!