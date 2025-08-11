# An Introduction to Cisco IOS

Author(s): a_person

Last Updated: 08-09-2025

<details>
<summary>Recommended Prerequisites (click to expand)</summary>
<p>None</p>

</details>

## What is an OS?
An operating system (OS) is system software that manages computer hardware and software resources. Cisco has its own operating system, Cisco IOS, and it is used on their devices, which include routers, switches, and firewalls.

## Access methods
### Console
A physical management port that offers out-of-band access to a Cisco device via a dedicated management channel used solely for maintenance. The main benefit is that the device can be accessed even if no network settings are configured, such as during initial setup. To connect, you'll need a computer with terminal emulation software and a special console cable.

### Secure Shell (SSH)
An in-band, secure method to remotely access the device’s CLI over a network through a virtual interface. SSH requires the device to have active networking services and a configured interface with an IP address. Most Cisco IOS versions include both an SSH server and client for establishing secure sessions. SSH not only used in networking devices, and can be used to access servers.

### Telnet
An insecure, in-band way to remotely access the CLI over a network via a virtual interface. Unlike SSH, Telnet does not encrypt data, so passwords and commands are sent in plaintext, making it suitable only for enviornments, such as lab environments. SSH is strongly recommended instead.

## Terminal Smulation Software
These provide a more graphical way to interact with devices. The most common emulation software is [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html).

## Cisco Command Modes
There are 3 main Command Modes:
### User EXEC Mode
- Indicated by the ``>`` symbol. Example:
```
Router>
```
- Limited in what you can do
- The user can view basic information about the device, but can't make changes to the configuration.
### Privilaged EXEC Mode
- You can enter this mode through using the **enable** command, and exit through **disable** or **exit**. 
- Indicatedby the ``#`` symbol. Example:
```
Router#
```
- Provides complete access to view the device's configuration, restart the device, etc.
- Cannot change the configuration, but can change the time on the device, save the configuration file, etc.

### Global Configuration Mode
- You can enter this mode through using the **configure terminal** command, and exit through **disable** or **exit**. 
- Indicated by ``(config)#`` . Example:
```
Router(config)#
```
- Provides complete access to view the device's configuration, restart the device, etc.
- Cannot change the configuration, but can change the time on the device, save the configuration file, etc.
- Provides access to change the device's running configuration, including interface settings, routing protocols, and security configurations.


## Help Command 
- Single question mark (?) shows available commands or options at the current level. Example:
```
Router> ?
```
This will show all the avaliable commands that you can use in the currrent state.
```
Router> show ?
```
This will show you what parameters are accepted for the show command.
```
Router> s?
```
This will show you all the possible completions of the command.

## Do command
The do command allows you to execute commands in privileged EXEC mode commands without leaving configuration modes.

Example: Checking the running configuration while in interface configuration mode:
```
Router(config-if)# do show running-config
```
## Shortening Commands
Many Cisco IOS commands can be abbreviated as long as the abbreviation is unambiguous.

Example:
```
Router> show running-config
```
can be shortened to:
```
Router> sh run
```
Use ? to confirm what abbreviations are valid.

## Practice
Do the following steps in order:
1. Enter privilaged EXEC mode
2. Enter global configuration mode
3. Exit global configuration mode
4. Exit privilaged EXEC Mode  

**You must enter the FULL commands.**
<div className="iframe-container">
  <iframe
    src="https://orionband.github.io/windowstst/cisco.html?q=enable:configure terminal:exit:exit,enable:configure terminal:exit:disable,enable:configure terminal:exit:disable"
    width="600"
    height="250"
    frameBorder="0"
    tabIndex="-1"
    loading="lazy"
    style={{borderRadius: '15px', outline: 'none'}}
  />
</div>


## Supplementary Resources and Further Reading
- https://www.cisco.com/E-Learning/bulk/public/tac/cim/cib/using_cisco_ios_software/02_cisco_ios_hierarchy.htm
- https://www.cisco.com/c/en/us/td/docs/switches/wan/mgx/mgx_8850/software/mgx_r3/rpm/rpm_r1-1/configuration/guide/appc.pdf
- https://www.youtube.com/watch?v=IYbtai7Nu2g&list=PLxbwE86jKRgMpuZuLBivzlM8s2Dk5lXBQ&index=8
