# Basic Router and Switch security

Author(s): a_person

Last Updated: 08-09-2025

<details>
<summary>Recommended Prerequisites (click to expand)</summary>
<p>Introduction to Cisco IOS</p>

</details>

## Enable Password
The `enable password` command sets a password required to enter privileged EXEC mode on Cisco devices.

### Syntax
```
Router(config)# enable password your_password
```

### Important notes
- Stored in plain text in the configuration file
- Visible when viewing the running configuration
- Provides basic protection but not recommended for production environments
- Can be seen by anyone with access to the configuration



## Enable secret

The `enable secret` command provides a more secure alternative to the `enable password` command as it uses a hashing algorithm. When there are both ``enable password`` and ``enable secret``, ``enable secret`` takes precedence because Cisco IOS always prefers the more secure option.

### Syntax
```
Router(config)# enable secret your_password
```


## Protecting Console
This configuration secures console access to the device by applying a password requirement. It specifies the console line (``line console 0``), sets a password (``password your_console_password``), and enables password checking on login (``login``). 

```
Router(config)# line console 0
Router(config-line)# password your_console_password
Router(config-line)# login
```

## Password Encryption Service

The `service password-encryption` command enables automatic encryption of passwords in the configuration file using Type 7 encryption. Later in the article, we will be talking about the differences between the various encryption types. ``service password-encryption`` is not strong security and is mainly for obscuring passwords from casual viewing.

**What it affects:**
- Line passwords (console, vty, aux)
- Enable password (but not enable secret)
- Username passwords (but not username secrets)
- SNMP community strings
- Other plaintext passwords in configuration

### Syntax
```
Router(config)# service password-encryption
```

## Cisco Password Encryption Levels

Cisco devices use different encryption levels to secure passwords stored in configuration files:

### Type 0 - Plain Text
- No encryption applied
- Password visible in clear text
- Default behavior without encryption services
- **Example:** `password 0 MyPassword123`

### Type 7 - Cisco Proprietary Encryption
- Basic obfuscation using Vigenère cipher
- Reversible encryption (easily decoded)
- Enabled with `service password-encryption`
- **Example:** `password 7 094F471A1A0A464058`

### Type 5 - MD5 Hash
- Uses MD5 hashing algorithm
- One-way encryption 
- As you may or may not already know, MD5 is vulnerable to collision attacks, making it not as secure as other hashing algorithms.
- Used by `enable secret` and `username secret` commands
- **Example:** `enable secret 5 $1$mERr$hx5rVt7rPNoS4wqbXKX7m0`

### Type 8 - PBKDF2 with SHA-256
- Password-Based Key Derivation Function 2
- Uses SHA-256 hashing with salt
- **Example:** `username admin secret 8 $8$mERr$hx5rVt7rPNoS4wqbXKX7m0$`

### Type 9 - Scrypt
- Latest and most secure encryption type
- Uses scrypt key derivation function
- Resistant to hardware attacks
- **Example:** `username admin secret 9 $9$mERr$hx5rVt7rPNoS4wqbXKX7m0$`



## Practice
Do the following steps in order:
1. Enable password encryption
2. Set the secret to ``C1sc0R0cks``
3. Set the console password to ``CyberPatriot1!``

**You must enter the FULL commands.**
<div className="iframe-container">
  <iframe
    src="https://orionband.github.io/windowstst/cisco.html?i=config&q=service password-encryption:enable secret C1sc0R0cks:line console 0:password CyberPatriot1!:login"
    width="600"
    height="250"
    frameBorder="0"
    tabIndex="-1"
    loading="lazy"
    style={{borderRadius: '15px', outline: 'none'}}
  />
</div>

## Labs
- [CCNA Lab 003 PKT download (JIT)](https://drive.google.com/file/d/132NG6fJ03XcguOsChH-JXqafaOxTZMXd/view?usp=sharing) 
- [CCNA Lab 003 walkthrough (JIT)](https://www.youtube.com/watch?v=Gj-8agyq4yQ&list=PLxbwE86jKRgMQ4HTuaJ7yQgA2BoNwY9ct&index=4)
- [Day 4 Basic Security Lab PKT download(JIT)](https://drive.google.com/file/d/1SukSVB9OKMG49aiqwfOdqc1lU6jVigrW/view?usp=sharing)
- [Day 4 Basic Security Lab PKT walkthrough(JIT)](https://drive.google.com/file/d/1SukSVB9OKMG49aiqwfOdqc1lU6jVigrW/view?usp=sharing)

## Supplementary Resources and Further Reading
- https://www.youtube.com/watch?v=IYbtai7Nu2g&list=PLxbwE86jKRgMpuZuLBivzlM8s2Dk5lXBQ&index=8&pp=iAQB
- https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst2960cx_3650cx/software/release/15-2_7_e/configuration_guide/b_1527e_consolidated_3560cx_2960cx_cg/m_sec_passpr_cg.pdf
