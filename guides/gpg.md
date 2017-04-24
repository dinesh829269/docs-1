### Setup

1. Install GnuPG: `brew install gnupg`
2. Generate a public/private key pair: `gpg --gen-key`
    1. Select RSA
    2. 4096
    3. 0 (doesn't expire)
    4. Your name (eg. `Dana Silver`)
    5. You don't need a comment
    6. Your email (eg. `dsilver@middlebury.edu`)
3. Upload your public key: `gpg --send-keys <public key id>`

In the infomation printed out like below, `12EC8CCR` is the public key id.
`gpg --send-keys` will never send your private key.

```
sec   4096R/12EC8CCR 2013-08-19 [expires: 2017-08-19]
uid                  Dana Silver <dsilver@middlebury.edu>
ssb   4096R/6D2B2B25 2013-08-19
```

### Encrypt

1. Find and download the public key for the person who's receiving the encrypted message: `gpg --search-keys <recipient's email>`
2. Encrypt the data `echo "something private" | gpg --encrypt --armor --recipient "<recipient's email>"`
3. Send over the output, including the `-----BEGIN PGP MESSAGE-----` and `-----END PGP MESSAGE-----` lines

### Decrypt

1. Decrypt with `gpg --decrypt < <encrypted file's name>`

Note: Both `gpg --encrypt` and `gpg --decrypt` receive input from stdin. It's convenient to use [pbpaste(1)](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man1/pbpaste.1.html) give the commands their input.
