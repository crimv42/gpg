# GPG Key to Yubikey

Important Transferring keys to YubiKey using keytocard is a destructive, one-way operation only. Make sure you've made a backup before proceeding: keytocard converts the local, on-disk key into a stub, which means the on-disk copy is no longer usable to transfer to subsequent security key devices or mint additional keys.

Previous GPG versions required the toggle command before selecting keys. The currently selected key(s) are indicated with an \*. When moving keys only one key should be selected at a time.

```
[daniel.nelems@vm-fc-work01:~]$ gpg --edit-key bilbo@theshire.com
gpg (GnuPG) 2.2.13; Copyright (C) 2019 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Secret key is available.

sec  rsa4096/5B11074CBFC83CAB
     created: 2019-04-23  expires: never       usage: C
     trust: ultimate      validity: unknown
ssb  rsa4096/732296B3D40D31FC
     created: 2019-04-23  expires: never       usage: S
ssb  rsa4096/487E7BD5E474E91B
     created: 2019-04-23  expires: never       usage: E
ssb  rsa4096/D4BE9C22E7DCD9CE
     created: 2019-04-23  expires: never       usage: A
[ unknown] (1). bilbo (example key) <bilbo@theshire.com>

gpg>
````

### Signing

```
gpg> key 1

sec  rsa4096/5B11074CBFC83CAB
     created: 2019-04-23  expires: never       usage: C
     trust: ultimate      validity: unknown
ssb* rsa4096/732296B3D40D31FC
     created: 2019-04-23  expires: never       usage: S
ssb  rsa4096/487E7BD5E474E91B
     created: 2019-04-23  expires: never       usage: E
ssb  rsa4096/D4BE9C22E7DCD9CE
     created: 2019-04-23  expires: never       usage: A
[ unknown] (1). bilbo (example key) <bilbo@theshire.com>

gpg> keytocard

Please select where to store the key:
   (1) Signature key
   (3) Authentication key
Your selection? 1
```

### Encryption

Type key 1 again to de-select and key 2 to select the next key:

```
gpg> key 1

gpg> key 2

sec  rsa4096/5B11074CBFC83CAB
     created: 2019-04-23  expires: never       usage: C
     trust: ultimate      validity: unknown
ssb  rsa4096/732296B3D40D31FC
     created: 2019-04-23  expires: never       usage: S
ssb* rsa4096/487E7BD5E474E91B
     created: 2019-04-23  expires: never       usage: E
ssb  rsa4096/D4BE9C22E7DCD9CE
     created: 2019-04-23  expires: never       usage: A
[ unknown] (1). bilbo (example key) <bilbo@theshire.com>

gpg> keytocard
Please select where to store the key:
   (2) Encryption key
Your selection? 2
```

### Authentication

Type key 2 again to deselect and key 3 to select the last key:

```
gpg> key 3

sec  rsa4096/5B11074CBFC83CAB
     created: 2019-04-23  expires: never       usage: C
     trust: ultimate      validity: unknown
ssb  rsa4096/732296B3D40D31FC
     created: 2019-04-23  expires: never       usage: S
ssb  rsa4096/487E7BD5E474E91B
     created: 2019-04-23  expires: never       usage: E
ssb* rsa4096/D4BE9C22E7DCD9CE
     created: 2019-04-23  expires: never       usage: A
[ unknown] (1). bilbo (example key) <bilbo@theshire.com>

gpg> keytocard
Please select where to store the key:
   (3) Authentication key
Your selection? 3

gpg> save
```

### Verify card

Verify the subkeys have moved to YubiKey as indicated by ssb>:

```
$ gpg --list-secret-keys
/home/daniel.nelems/.gnupg/pubring.kbx
-------------------------------------------------------------------------
sec   rsa4096 2019-04-23 [C]
      2A6C6450EF693AED9DB984AB5B11074CBFC83CAB
uid                            [ unknown] bilbo (example key) <bilbo@theshire.com>
ssb>  rsa4096/0x732296B3D40D31FC 2019-04-23 [S] [expires: never]
ssb>  rsa4096/0x487E7BD5E474E91B 2019-04-23 [E] [expires: never]
ssb>  rsa4096/0xD4BE9C22E7DCD9CE 2019-04-23 [A] [expires: never]
```

# Using GPG Yubikey for SSH

Add the following config:

## `~/.bash_profile`:

```
# GPG Key for Yubikey
GPG_TTY=$(tty)
export GPG_TTY
export SSH_AUTH_SOCK=$(gpgconf --list-dirs agent-ssh-socket)
gpgconf --launch gpg-agent
```

Then run `ssh-add -L` to confirm your ssh key is present.
