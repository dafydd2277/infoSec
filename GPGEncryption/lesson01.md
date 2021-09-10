# Encryption using GnuPG or OpenPGP

## Lesson 1: Installation and Creating a Key

> This lesson was originally posted to pastebin. Each lesson requires
the student to send information to the instructor. Then, the instructor
would encrypt the location of the next lesson and send the encrypted
reply back to the student.

If you're on Windows, [here's a YouTube tutorial][ref101] for
installing [Gpg4win][ref102]. On macOS,
[here's a YouTube tutorial][ref103] for installing [GPGTools][ref104].
If you have a Chromebook, I believe it's built in. The macOS tutorial
isn't very good. Maybe, one day, I'll buy a web cam and do a better
one.

[ref101]: https://www.youtube.com/watch?v=QmE4LrBSChQ
[ref102]: https://www.gpg4win.org/
[ref103]: https://www.youtube.com/watch?v=JK2q-kYCg1Y
[ref104]: https://www.gpgtools.org/

Follow the instructions in the tutorials for creating your first set of
public and secret keys. Open up the `Advanced Options...` for some of
these settings.

- Use the default key type (`RSA and RSA`)
- Take the default key size of 2048 bits.
- Set the key expiration to 1 week.
- For Name, use "Lesson 1 key."
- For Email, use your real address.
- For the Comment, use "Lesson 1 key."
- Use any simple password that works for you. In a future lesson, we'll
discuss strong passwords. You won't be using this particular key for
very long.

Now, `Export...` your public key using the Ascii armor option, and copy
the entire key, from the first dash in the first `BEGIN` line to the
last dash in the `END` line. Paste that into an email and send it to
me at <dafydd@dafydd.com>.

A note before I continue: from a security standpoint, Graphical User
Interfaces suck. You have no idea what's going on "under the covers."
"Command Line Interfaces," like the Windows Command Prompt application,
are somewhat better. So, all future lessons are going to be working
from the command line, or CLI. This reduces, but won't eliminate, the
number of ways your security can be compromised.

With that out of the way, once I have your first public key, I'm going
to create a [public/private key-pair of my own][ref105] that's just
for us. I will use your public key to encrypt my public key and the
instructions for lesson 2.

[ref105]: https://en.wikipedia.org/wiki/Public-key_cryptography

When you get the encrypted message, copy it out of your email and
paste it into a text file called `lesson02.asc`. Then, from your
command line interface, try this:

```
gpg -d lesson02.asc
```

You should be asked for the password for your key. Once you enter that,
you should get the unencrypted text out to your command window. To send
the text to a file, try this:

```
gpg -d lesson02.asc > lesson02.txt
```

That should create a text file with the instructions for the second
lesson, along with my public key.

