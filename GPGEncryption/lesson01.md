# Encryption using GnuPG or OpenPGP

## Lesson 1: Installation and Creating a Key

> This lesson was originally posted to pastebin. Each lesson requires
the student to send information to the instructor. Then, the instructor
would encrypt the location of the next lesson and send the encrypted
reply back to the student.

If you're on Windows, [here's a YouTube tutorial][ref101] for
installing [Gpg4win][ref102]. On macOS,
[here's a YouTube tutorial][ref103] for installing [GPGTools][ref104].
If you have a Chromebook, I believe it's built in.

Follow the instructions in the tutorials for creating your first set of
public and secret keys.

- Use the default key type (`RSA and RSA`)
- Take the default key size of 2048 bits.
- Set the key expiration to 1 week.
- Use any name you want, your real email address, and a comment of
"Lesson 1 key."
- Use any simple password that works for you. In a future lesson, we'll
discuss strong passwords. You won't this particular key for very long.

Your command should look something like this when you're done. (Note
that the dollar sign at the beginning of a line is a command prompt.
Don't type it in.)

```
$ gpg --full-generate-key
gpg (GnuPG) 2.2.20; Copyright (C) 2020 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Please select what kind of key you want:
   (1) RSA and RSA (default)
   (2) DSA and Elgamal
   (3) DSA (sign only)
   (4) RSA (sign only)
  (14) Existing key from card
Your selection? 1
RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (2048)
Requested keysize is 2048 bits
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0) 1w
Key expires at Thu 16 Sep 2021 08:15:18 PM PDT
Is this correct? (y/N) y

GnuPG needs to construct a user ID to identify your key.

Real name: David Barr
Email address: dafydd@dafydd.com
Comment: Lesson 1 Key
You selected this USER-ID:
    "David Barr (Lesson 1 Key) <dafydd@dafydd.com>"

Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? O
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: key 889E4B6B0D39F32B marked as ultimately trusted
gpg: revocation certificate stored as '/home/dafydd/.gnupg/openpgp-revocs.d/405B9143E2DB2F9024DDD379889E4B6B0D39F32B.rev'
public and secret key created and signed.

pub   rsa2048 2021-09-10 [SC] [expires: 2021-09-17]
      405B9143E2DB2F9024DDD379889E4B6B0D39F32B
uid                      David Barr (Lesson 1 Key) <dafydd@dafydd.com>
sub   rsa2048 2021-09-10 [E] [expires: 2021-09-17]
```


Now, you should be able to list your keys. Try these two commands.

```
$ gpg --list-keys

$ gpg --list-secret-keys
```


Your computer should have printed a list of your keys. You should have
one public and one secret key. Now, you're going to export the public
key.

```
$ gpg --export -a 405B9143E2DB2F9024DDD379889E4B6B0D39F32B
-----BEGIN PGP PUBLIC KEY BLOCK-----

(Lots of not-actually-random characters in lines 64 characters long.)
-----END PGP PUBLIC KEY BLOCK-----
```

Email that entire block of text, including the complete BEGIN and END
lines, to me. I will use your public key to encrypt the location of the
second lesson and email it back to you. When you get the encrypted
message, it will look something like this:

```
-----BEGIN PGP MESSAGE-----

(Lots of not-actually-random characters in lines 64 characters long.)
-----END PGP MESSAGE-----
```

Copy all of that text, including the complete `BEGIN` and `END` lines,
into a text file. Then, execute

```
$ gpg -d <file>
```

using the name of the file. Once decrypted, you'll find a URL for the
second lesson. That one will give you my public key and teach you how
to encrypt a message back to me.

[ref101]: https://www.youtube.com/watch?v=QmE4LrBSChQ
[ref102]: https://www.gpg4win.org/
[ref103]: https://www.youtube.com/watch?v=JK2q-kYCg1Y
[ref104]: https://www.gpgtools.org/

