# ssh-tor-onion
This repository explains briefly how to ssh through tor network , being able to ssh out of your home without a dedicated server.
This  explanation is only for unix users.

### Server Configuration
First we may install the tor package to make use of it, so depending your distribution, install it:
```apt install tor```
#### torrc
this is the configuration file that you can manipulate by using a text editor (vim) in this directory:
```/etc/tor/torrc```
Here we will delete the next #'s:
```
HiddenServiceDir /var/lib/tor/other_hidden_service/
#HiddenServicePort 80 127.0.0.1:80
HiddenServicePort 22 127.0.0.1:22

```
This will create a folder on this directory (/var/lib/tor/other_hidden_service/).
You can also change the port with whatever port you use or by the port 8022 if you are using termux (HiddenServicePort 8022 127.0.0.1:8022).
And this will be the configuration.
If you acces to the "other_hidden_service" folder you will be able to see your hostname.
```cat hostname```
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx.onion (V3)
This is your new tor ssh adress.

### Client Configuration

I reccomend you to make an easy script to avoid typing that much.
To be able to connect through tor we will need to make ssh go through the net tor. Thats why we will using the `torify` tool that comes with the tor package.
In your client side type whoami to know which is your username
If you need set a password to your account doing `passwd`
`torify ssh user@xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx.onion`
This will request you your passwd.
Once this done you will be able to interact with your Service terminal via ssh.

## Termux Server Config
In termux you have to follow the same steps as unix type, you can also use your phone as a service or a tor server.

## Termux Client Config
In termux is not posible to use torify so we will need to download the offical Orbot app. In the VPN selector we will chose the Termux app to torify all the app via onion that will let us connect to our onion-ssh host.



