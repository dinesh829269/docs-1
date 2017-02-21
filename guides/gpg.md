### Setup

0. Install GnuPG: `brew install gnupg`
0. Generate a public/private key pair: `gpg --gen-key`
  0. Select RSA
  0. 4096
  0. 0 (doesn't expire)
  0. Your name (eg. `Dana Silver`)
  0. You don't need a comment
  0. Your email (eg. `dsilver@middlebury.edu`)
0. Upload your public key: `gpg --send-keys <public key id>`

In the infomation printed out like below, `12EC8CCR` is the public key id.
`gpg --send-keys` will never send your private key.

```
sec   4096R/12EC8CCR 2013-08-19 [expires: 2017-08-19]
uid                  Dana Silver <dsilver@middlebury.edu>
ssb   4096R/6D2B2B25 2013-08-19
```

### Encrypt

0. Find and download the public key for the person who's receiving the encrypted message: `gpg --search-keys <recipient's email>`
0. Encrypt the data `echo "something private" | gpg --encrypt --armor --recipient "<recipient's email>"`
0. Send over the output, including the `-----BEGIN PGP MESSAGE-----` and `-----END PGP MESSAGE-----` lines

### Decrypt

0. Decrypt with `gpg --decrypt < <encrypted file's name>`

Note: Both `gpg --encrypt` and `gpg --decrypt` receive input from stdin. It's convenient to use [pbpaste(1)](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man1/pbpaste.1.html) give the commands their input.
