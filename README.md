# ssh-tor-onion
This repository explains briefly how to ssh through tor network, being able to ssh out of home without a dedicated server.

This explanation is only for Unix users.

### Server Configuration

First we may install the tor package to make use of it, so depending on the distribution, install it:

```
apt install tor
```

#### torrc

This is the configuration file that can be manipulated by using a text editor (vim) in this directory:

```/etc/tor/torrc```

Here delete the next #'s: 

```
HiddenServiceDir /var/lib/tor/other_hidden_service/
#HiddenServicePort 80 127.0.0.1:80
HiddenServicePort 22 127.0.0.1:22
```

This will create a folder on this directory (/var/lib/tor/other_hidden_service/).

Can also change the port with whatever port not being used or the port 8022 if you are using Termux (HiddenServicePort 8022 127.0.0.1:8022).


Accessing the "other_hidden_service" folder, it will be able to see the hostname.

```
cat hostname
```

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx.onion (V3)

This is the new given ssh tor address.

### Client Configuration

It's recommended to make an easy script to avoid typing that much.

To be able to connect through tor, it's need to make ssh go through the tor net. That's why it will be used the `torify` tool that comes with the tor package.

In the client side, type ```whoami``` to know which is the username.

If it's needed to set a password to the account typing ```passwd```.

```
torify ssh user@xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx.onion
```

After reaching the connection, it will prompt a request for the server password.

Once this done, it will be able to interact with the Service terminal via ssh.

## Termux Server Config

In termux it has to be followed the same steps as Unix type, can also use the phone as a service or a tor server.

## Termux Client Config

In termux is not possible to use torify, so it will be needed to download the official Orbot app. In the VPN selector, chose the Termux app to torify all the app via onion, that will let it connect to the onion-ssh host.



