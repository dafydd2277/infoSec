# Running Notes

- *Lesson01*
    - Download the software, create a short term key, send the ascii-
    armored public key to me.
        - *Don't* upload the key anywhere.
        - *Don't* create a copy.
        - How to decrypt the pointer to lesson02.

- *Lesson02* Prep
    - Create a custom key pair for the interaction.
    - Include it with the lesson.

- *Lesson02*
    - Create a text file.
    - Encrypt the text file with the instructor's public key.
    - Post the ascii-armored text to a gDoc.
    - Share the gDoc with dafydd2277@gmail.com as Editor.

- *Lesson03* Prep
    - Encrypt instructions to delete the first key, create a proper
    email key, and send me the proper key. Paste that into the gDoc.

- *Lesson03*
    - Discuss the value of strong passwords, and the utility of
    password managers.
    - Student creates a regular email encryption key, and sends it to
    me. Use a short expiration. Comment that it's a test email key.

- *Lesson04* Prep
    - Sign and return the key.
    - Encrypt the signed key and lesson04 instructions, and send email
    back.

- *Lesson04*
    - Upload the signed key to https://keys.openpgp.org/.
    - Look at https://www.openpgp.org/software/ for instructions on
    incorporating your email key into your email client.
    - Encrypt and send me the URL to your key.

- *Lesson05* Prep
    - Put the Lesson 05 text in Dropbox. Encrypt and return the URL.

- *Lesson05*
    - Discover that your key has been compromised. Revoke it, and
    upload the revocation to https://keys.openpgp.org/.
    - Try to download the key again.
    - Create a new key, with all the proper information and a comment
    of "Email key" Upload that, and email me the URL.

- *Lesson06* Prep
    - Put Lesson06 in a Pastebin file, with a burn after reading
    setting. Encrypt and email the URL.

- *Lesson06*
    - Get my email key from https://keys.openpgp.net/. Encrypt a file
    using that key and the command line. Email it to me.

- *Lesson07* Prep
    - Put the text of Lesson07 in a gDoc.
    - Put an encrypted meme image in a Pastebin file. Include the link
    in the gDoc.
    - Encrypt the URL to the gDoc.

- *Lesson07*
    - Discuss the value of simplicity, text files, and Markdown.
    Discuss the risks of encrypting Word Docs, PDFs, etc.
    - Discuss how we've been using email, gDocs, pastebin, and
    Dropbox the spread files around.
    - Discuss how diligence and randomness help with security.
    - Discuss using canary phrases.
        - Don't ever write them down when you don't mean them.
        Discuss the canary phrase for your project in person. Then,
        if it gets used in text, you know your part has been
        compromised.



# One Example For Secure Communications

> This was my original brain dump for what I wanted to do here, before
I thought of the lesson format. Once all of this load of garbage is
made pretty and in lessons, this file can be deleted.

## Introduction

Information security is an enormous game of cat and mouse. Your adversaries
want to know what your thinking. You want to prevent them from figuring that
out.

This document introduces you to [GnuPG][intro01] and [OpenPGP][intro02] for
encrypting, well, anything really. Then, we will discuss some ways to share
those encrypted items that minimize the opportunities for interception.

[intro01]: https://www.gnupg.org/download/index.html
[intro02]: https://www.openpgp.org/


## Diligence

First, though, we need to talk about effort. Good information security requires
concentration and repetition. Every time you get lazy, you leave an adversary
an opportunity to crack your security.

For one specific example, in this document I'm going to show you how to create
an ephemeral PGP key pair that only lasts a week. However, that only means that
*no one else* can use the public key after it expires. As long as you have the
private key and the password, you will always have the ability to decrypt
documents secured with that key pair. So, to prevent someone from capturing
your information, you need to delete expired ephemeral keys and adapt to the
fact that old encrypted information will rot into unusability. That's the price
of information security.

One result of developing and practicing the habits of diligence is that you try
to minimize the amount of complexity you build into your secure communications.
That's why this document is plain text. (There's more in the footnote, below.)
Word documents, PDF files, and any kind of file format more complicated than
ASCII text introduces opportunities for an adversary to introduce a means to
break into and read your communications. So, KISS. Keep It Simple. Use plain
text wherever possible.


## Pretty Good Privacy

PGP is based on the concept of "key pairs." Every time you create a key pair,
one key (the "private" key) is for you to keep. The other key (the "public" key)
gets published or sent to your correspondant.

These "private/public key pairs" are very difficult to hack. However, doing so
is not impossible. You need to be very careful with your private keys, and very
aware of how your public keys are being used.


### Key Types

I distinguish my PGP keys into two types. I call them "email keys" and
"ephemeral keys." These are key pairs used for different things, and come with
different and corresponding levels of security.

My email key usually has a two year expiration and is [publicly
available][type001]. Anyone can go to https://keys.openpgp.org/, look up my
email address, and encrypt an email that only I can decrypt.

If I need to have specific converstaions with specific people, I will set up an
"ephemeral key." That key pair will expire in a month or less, depending on my
best guess of the length of the interaction. Also, limit who gets your ephemeral
public key. Only the two people of a particular conversation should have access
to the ephemeral key for that conversation. The more people who have the key,
the more likely it will be compromised.

Now, two important points about ephemeral keys. First, don't expect to the
information kept in this way to last for any length of time. If the information
needs to be kept for a long time, it needs to be secured in another way.
Second, once the key has expired, delete it. This goes back to the diligence
I talked about earlier. Delete the private and public keys from any ephemeral
key pair. If you don't have the private key any more, you can't be forced to
decrypt an old message. That message is gone, never to be recovered.

[type001]: https://keys.openpgp.org/vks/v1/by-fingerprint/042BC7A61817FD78AC85DD4ACC0B3F78FDDBD9AC


### Creating a Key

If you're a Windows user, I'm going to guess that you found [Gpg4win][create01]
to create your first key. If you used the GUI to do it, I'm going to slightly
encourage you to learn how to create keys using the command line via `cmd.exe`.
Graphical User Interfaces are another way your secrecy can be highjacked. While
I would hate to think that Gpg4win or [GPG Keychain][create02] for macOS have
been compromised, using the command line removes yet another layer of potential
complexity.

So, having said that, creating a key through a command is really easy. You just
type in

```
gpg --gen-key
```

The key creation process will walk you through the information you need to
include for the key. 2048 bits of encryption is typically enough, particularly
for ephemeral keys. Use the "comment" field to say something specific about this
ephemeral key. Including the name of the other person in the conversation is a
risk balanced by the fact that the key will be deleted as soon as it expires.

[create01]: https://gpg4win.org/download.html
[create02]: https://gpgtools.org/


## Sharing Files

Many methods exist to share files. (Don't just use one.) Files can be encrypted
and "ascii-armored" and shared as text through Google Docs, Dropbox, Pastebin,
or any number of other methods. Many of these methods have the advantage that
the method of transfer does not easily identify the people participating in
that transfer.

## Homework

If you would like an opportunity for basic practice, let's do this. Create
another PGP key pair. This time, give it a 2 year expiration and include a
comment that this is your public email key. I have added an ephemeral public
key below. Use that to encrypt your public key and post the result at the top
of this page. I will sign your public key using my email key, encrypt the
result, and put that at the top of this page. Then, you can [publish][home01]
that public key for anyone who wants to contact you.

[home01]: https://keys.openpgp.org/


## Footnote

This document was written in [GitHub-flavored Markdown][foot01]. As with any
new language, it takes a little bit of learning. However, you should have
noticed by now that you were getting the gist of how this document would have
been formatted if it were not plain text. Hash characters indicate headers,
square brackets indicate link text and references to the actual links, asterisks
indicate emphasized text, etc. With some practice, your brain will imagine all
of the formatting and skip all of the link references until you're ready for
them. If the formatting here is really breaking your brain, consider getting
the text editor called [Atom][foot02]. It can identify Markdown files based on
the file extension, and use text colors and highlighting to help with
interpretation.

But, underlying it all, this document is still just plain text. This is another
example of the KISS principle. Plain text is as simple as you can get for a
document. Every layer of formatting you add is an opportunity for someone to
insert a way for the document to be tracked. So, and again, minimize complexity
wherever possible when you exchange information. Don't ever forget the great
Montgomery Scott quote: "The more they over think the plumbing, the easier it
is to stop up the drain." Keep your plumbing simple to minimize your
adversary's ability to stop up your drain.


[foot01]: https://guides.github.com/features/mastering-markdown/
[foot02]: https://atom.io/


## Ephemeral Key


