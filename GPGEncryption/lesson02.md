# Encryption using GnuPG or OpenPGP

## Lesson 2: Adding Public Keys and Encrypting Files

Student will

- Import the instructor's key into their keychain.
- Copy and paste a recipe into Notepad, and save the file to
`recipe.txt`.
- Encrypt `recipe.txt`.
- Upload `lesson02.asc` to Google Docs.
- Get and encrypt the URL to the Google Doc.
- Email the encrypted URL to the instructor.

```
gpg --import

gpg --list-keys

gpg -ear <instructors key> recipe.txt > lesson02.asc
```

