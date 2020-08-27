# gpg
GPG Instructions
# Generate GPG Key

```
[daniel.nelems@vm-fc-work01:~]$ gpg2 --expert --full-generate-key
gpg (GnuPG) 2.2.13; Copyright (C) 2019 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Please select what kind of key you want:
   (1) RSA and RSA (default)
   (2) DSA and Elgamal
   (3) DSA (sign only)
   (4) RSA (sign only)
   (7) DSA (set your own capabilities)
   (8) RSA (set your own capabilities)
   (9) ECC and ECC
  (10) ECC (sign only)
  (11) ECC (set your own capabilities)
  (13) Existing key
Your selection? 8

Possible actions for a RSA key: Sign Certify Encrypt Authenticate
Current allowed actions: Sign Certify Encrypt

   (S) Toggle the sign capability
   (E) Toggle the encrypt capability
   (A) Toggle the authenticate capability
   (Q) Finished

Your selection? s

Possible actions for a RSA key: Sign Certify Encrypt Authenticate
Current allowed actions: Certify Encrypt

   (S) Toggle the sign capability
   (E) Toggle the encrypt capability
   (A) Toggle the authenticate capability
   (Q) Finished

Your selection? e

Possible actions for a RSA key: Sign Certify Encrypt Authenticate
Current allowed actions: Certify

   (S) Toggle the sign capability
   (E) Toggle the encrypt capability
   (A) Toggle the authenticate capability
   (Q) Finished

Your selection? q
RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (2048) 4096
Requested keysize is 4096 bits
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0) 0
Key does not expire at all
Is this correct? (y/N) y

GnuPG needs to construct a user ID to identify your key.

Real name: bilbo
Email address: bilbo@theshire.com
Comment: example key
You selected this USER-ID:
    "bilbo (example key) <bilbo@theshire.com>"

Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? o
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: key 5B11074CBFC83CAB marked as ultimately trusted
gpg: directory '/home/daniel.nelems/.gnupg/openpgp-revocs.d' created
gpg: revocation certificate stored as '/home/daniel.nelems/.gnupg/openpgp-revocs.d/2A6C6450EF693AED9DB984AB5B11074CBFC83CAB.rev'
public and secret key created and signed.

pub   rsa4096 2019-04-23 [C]
      2A6C6450EF693AED9DB984AB5B11074CBFC83CAB
uid                      bilbo (example key) <bilbo@theshire.com>
```

## After generation

```
[daniel.nelems@vm-fc-work01:~]$ gpg2 -k
/home/daniel.nelems/.gnupg/pubring.kbx
--------------------------------------
pub   rsa4096 2019-04-23 [C]
      2A6C6450EF693AED9DB984AB5B11074CBFC83CAB
uid           [ unknown] bilbo (example key) <bilbo@theshire.com>
```

# Add keys

## Signing key
```
gpg2 --expert --edit-key bilbo@theshire.com
gpg (GnuPG) 2.2.13; Copyright (C) 2019 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Secret key is available.

sec  rsa4096/5B11074CBFC83CAB
     created: 2019-04-23  expires: never       usage: C
     trust: ultimate      validity: unknown
[ unknown] (1). bilbo (example key) <bilbo@theshire.com>

gpg> addkey
Please select what kind of key you want:
   (3) DSA (sign only)
   (4) RSA (sign only)
   (5) Elgamal (encrypt only)
   (6) RSA (encrypt only)
   (7) DSA (set your own capabilities)
   (8) RSA (set your own capabilities)
  (10) ECC (sign only)
  (11) ECC (set your own capabilities)
  (12) ECC (encrypt only)
  (13) Existing key
Your selection? 8

Possible actions for a RSA key: Sign Encrypt Authenticate
Current allowed actions: Sign Encrypt

   (S) Toggle the sign capability
   (E) Toggle the encrypt capability
   (A) Toggle the authenticate capability
   (Q) Finished

Your selection? e

Possible actions for a RSA key: Sign Encrypt Authenticate
Current allowed actions: Sign

   (S) Toggle the sign capability
   (E) Toggle the encrypt capability
   (A) Toggle the authenticate capability
   (Q) Finished

Your selection? q
RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (2048) 4096
Requested keysize is 4096 bits
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0) 0
Key does not expire at all
Is this correct? (y/N) y
Really create? (y/N) y
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.

sec  rsa4096/5B11074CBFC83CAB
     created: 2019-04-23  expires: never       usage: C
     trust: ultimate      validity: unknown
ssb  rsa4096/732296B3D40D31FC
     created: 2019-04-23  expires: never       usage: S
[ unknown] (1). bilbo (example key) <bilbo@theshire.com>
```

## Encrpytion key

```
gpg> addkey
Please select what kind of key you want:
   (3) DSA (sign only)
   (4) RSA (sign only)
   (5) Elgamal (encrypt only)
   (6) RSA (encrypt only)
   (7) DSA (set your own capabilities)
   (8) RSA (set your own capabilities)
  (10) ECC (sign only)
  (11) ECC (set your own capabilities)
  (12) ECC (encrypt only)
  (13) Existing key
Your selection? 8

Possible actions for a RSA key: Sign Encrypt Authenticate
Current allowed actions: Sign Encrypt

   (S) Toggle the sign capability
   (E) Toggle the encrypt capability
   (A) Toggle the authenticate capability
   (Q) Finished

Your selection? s

Possible actions for a RSA key: Sign Encrypt Authenticate
Current allowed actions: Encrypt

   (S) Toggle the sign capability
   (E) Toggle the encrypt capability
   (A) Toggle the authenticate capability
   (Q) Finished

Your selection? q
RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (2048) 4096
Requested keysize is 4096 bits
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0) 0
Key does not expire at all
Is this correct? (y/N) y
Really create? (y/N) y
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.

sec  rsa4096/5B11074CBFC83CAB
     created: 2019-04-23  expires: never       usage: C
     trust: ultimate      validity: unknown
ssb  rsa4096/732296B3D40D31FC
     created: 2019-04-23  expires: never       usage: S
ssb  rsa4096/487E7BD5E474E91B
     created: 2019-04-23  expires: never       usage: E
[ unknown] (1). bilbo (example key) <bilbo@theshire.com>
```

## Authentication Key

```
gpg> addkey
Please select what kind of key you want:
   (3) DSA (sign only)
   (4) RSA (sign only)
   (5) Elgamal (encrypt only)
   (6) RSA (encrypt only)
   (7) DSA (set your own capabilities)
   (8) RSA (set your own capabilities)
  (10) ECC (sign only)
  (11) ECC (set your own capabilities)
  (12) ECC (encrypt only)
  (13) Existing key
Your selection? 8

Possible actions for a RSA key: Sign Encrypt Authenticate
Current allowed actions: Sign Encrypt

   (S) Toggle the sign capability
   (E) Toggle the encrypt capability
   (A) Toggle the authenticate capability
   (Q) Finished

Your selection? s

Possible actions for a RSA key: Sign Encrypt Authenticate
Current allowed actions: Encrypt

   (S) Toggle the sign capability
   (E) Toggle the encrypt capability
   (A) Toggle the authenticate capability
   (Q) Finished

Your selection? e

Possible actions for a RSA key: Sign Encrypt Authenticate
Current allowed actions:

   (S) Toggle the sign capability
   (E) Toggle the encrypt capability
   (A) Toggle the authenticate capability
   (Q) Finished

Your selection? a

Possible actions for a RSA key: Sign Encrypt Authenticate
Current allowed actions: Authenticate

   (S) Toggle the sign capability
   (E) Toggle the encrypt capability
   (A) Toggle the authenticate capability
   (Q) Finished

Your selection? q
RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (2048) 4096
Requested keysize is 4096 bits
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0) 0
Key does not expire at all
Is this correct? (y/N) y
Really create? (y/N) y
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.

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

gpg> q
Save changes? (y/N) y
```

## After adding all keys

```
[daniel.nelems@vm-fc-work01:~]$ gpg2 -k
/home/daniel.nelems/.gnupg/pubring.kbx
--------------------------------------
pub   rsa4096 2019-04-23 [C]
      2A6C6450EF693AED9DB984AB5B11074CBFC83CAB
uid           [ unknown] bilbo (example key) <bilbo@theshire.com>
sub   rsa4096 2019-04-23 [S]
sub   rsa4096 2019-04-23 [E]
sub   rsa4096 2019-04-23 [A]
```

# Export private key

`gpg -a --export-secret-key bilbo@theshire.com > secret_key`

# Gen revocation key

```
[daniel.nelems@vm-fc-work01:~]$ gpg2 -a --gen-revoke bilbo@theshire.com > bilbo_revocation_cert.gpg

sec  rsa4096/5B11074CBFC83CAB 2019-04-23 bilbo (example key) <bilbo@theshire.com>

Create a revocation certificate for this key? (y/N) y
Please select the reason for the revocation:
  0 = No reason specified
  1 = Key has been compromised
  2 = Key is superseded
  3 = Key is no longer used
  Q = Cancel
(Probably you want to select 1 here)
Your decision? 1
Enter an optional description; end it with an empty line:
>
Reason for revocation: Key has been compromised
(No description given)
Is this okay? (y/N) y
Revocation certificate created.

Please move it to a medium which you can hide away; if Mallory gets
access to this certificate he can use it to make your key unusable.
It is smart to print this certificate and store it away, just in case
your media become unreadable.  But have some caution:  The print system of
your machine might store the data and make it available to others!
```

# Export Public key

gpg -a --export bilbo@theshire.com > public_key.gpg


# Backup GPG

Once GPG keys are moved to YubiKey, they cannot be extracted again!

Make sure you have made an encrypted backup before proceeding. Create a thumb drive that is encrypted, and then run copy the contents of:

`~/.gnupg/`

To your encrypted thumb drive.

# GPG Key to Yubikey

Important Transferring keys to YubiKey using keytocard is a destructive, one-way operation only. Make sure you've made a backup before proceeding: keytocard converts the local, on-disk key into a stub, which means the on-disk copy is no longer usable to transfer to subsequent security key devices or mint additional keys.

Previous GPG versions required the toggle command before selecting keys. The currently selected key(s) are indicated with an \*. When moving keys only one key should be selected at a time.

```
[daniel.nelems@vm-fc-work01:~]$ gpg2 --edit-key bilbo@theshire.com
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
$ gpg2 --list-secret-keys
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

### MacOS

#### Pinentry install

`brew install pinentry-mac`

Then edit `~/.gnupg/gpg-agent.conf`
```
/usr/bin/pinentry-mac
```

Then run `ssh-add -L` to confirm your ssh key is present.
