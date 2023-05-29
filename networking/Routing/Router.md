##### User EXEC Mode
- It is the first mode accessed at starting.
- It is indicated by **'>'**
	Router>
	Router ⇒ host name and '>' ⇒ user EXEC mode
- User EXEC mods is very limited
- Users can look at some things, but can't make any changes to the configuration
- Also called ‘user mode’
![](/assets/networking/router-mode-exec.png)

##### Privileged EXEC mode
- It is enabled by 'enable' command
	Router>enable
- It is indicated by **‘#’**
	Router#
- Provides complete access to view the device's configuration, restart the device, etc.
- Cannot change the configuration, but can change the time on the device, save the configuration file, etc.
![](/assets/networking/router-mode-privileged.png)

##### Global Configuration Mode
- It is enabled by ‘configure terminal’ command
```terminal
Router> enable
Router# configure terminal
Router (config)#
	or
Router#conf t
```
- It is indicated by **‘(config)#’**
	Router (config)#


- Set Password
```terminal
Router (config)# enable password passwd
```

### Configuration Files
There are two separate configuration files kept on the device at once.
1. **Running-config:** The current, active configuration file on the device. As you enter commands in the CLI, you edit the active configuration.
```terminal
Router# show running-config
Router# sh run
```
This command will show running config that are altered in running session.

2. **Startup-config:** The configuration file that will be loaded upon restart of the device.
```terminal
Router# show startup-config
Router# sh start 
```
This command will show startup config that are altered in running session.


- Saving configuration
```terminal
Router# write
Router# write memory
Router# copy running-config startup-config
```

- Service protection encryption
	For the encryption of password so that it does't show up in ‘show startup-config’ command
```terminal
Router (config)# service password-encryption
	Better one
Router (config)# enable secret Cisco
```

- Changing host name
```terminal
Router (config)# hostname anyname
```