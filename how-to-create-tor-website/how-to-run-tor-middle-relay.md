### 1. Enable Automatic Software Updates

One of the most important things to keep your relay secure is to install security updates timely and ideally automatically so you can not forget about it. Follow the instructions to enable [automatic software updates](https://community.torproject.org/relay/setup/guard/debian-ubuntu/updates) for your operating system.

### 2. Configure Tor Project's Repository

Configuring the Tor Project's package repository for Debian/Ubuntu is documented **[here](https://support.torproject.org/apt/tor-deb-repo/)**. Please follow those instructions before proceeding.

### 3. Package installation

Ensure you update the packages database before installing the package, than call `apt` to install it:

```
# apt update
# apt install tor
```

### 4. Configuration file

Put the configuration file `/etc/tor/torrc` in place

```
Nickname    myNiceRelay  # Change "myNiceRelay" to something you like
ContactInfo your@e-mail  # Write your e-mail and be aware it will be published
ORPort      443          # You might use a different port, should you want to
ExitRelay   0
SocksPort   0
```

> Contact Info is not necessary if we are running the single relay itself

### 5. Restart the service

Restart the `tor` daemon, so your configuration changes take effect:

```
# systemctl restart tor@default
```

### 6. Final Notes

If you are having trouble setting up your relay, have a look at our [help section](https://community.torproject.org/relay/getting-help/). If your relay is now running, check out the [post-install](https://community.torproject.org/relay/setup/post-install/) notes.

----

### How to monitor the new tor relay and check the data regading the relay then use the tool named `Nyx`

> Nyx is a command-line monitor for Tor. With this you can get detailed real-time information about your relay such as bandwidth usage, connections, logs, and much more.

https://nyx.torproject.org/#home

> and here's a video to support it https://youtu.be/npg3cBJusnA?t=536