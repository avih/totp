# About
This is a fork of https://github.com/angt/totp with two additions:
- Support option `-b` to decode base32 internally.
- Support option `-h` to print a short usage message.

When not using `-b` or `-h`, this fork is identical to upstream.

The plan is to merge upstream changes if/when upstream is updated.
There are no plans to add more features in this fork.

Pre-compiled Windows binaries (32/64) are available at the
[Releases](https://github.com/avih/totp/releases) page.

These binaries (or any other build of this source) can be used
out-of-the-box with github 2FA to generate an OTP token, without
any external dependencies (i.e. no need for `base32` utility):

    echo GITHUB-SECRET | totp -b

For problems with the Windows binaries or the additions in this fork,
please create an [issue](https://github.com/avih/totp/issues) here.

For other problems or requests, it would be better to create
an [upstream issue](https://github.com/angt/totp/issues).

Thanks to @[angt](https://github.com/angt) for writing this excellent
utility!

Below is the original upstream `README.md` content, with these changes:
- The `git clone` URL was modified to point to this fork.
- Additional example of the `-b` option which this fork supports.
- Added sub-title "secret" for existing content about that utility.

---

# totp
A tiny command line utility to generate OTP tokens

## Build and install

Clone the repository:

    $ git clone https://github.com/avih/totp
    $ cd totp

Then, run as `root`:

    # make install

As usual, you can customize the destination with `DESTDIR` and `prefix`.

## Usage

    $ echo -n JBSWY3DPEHPK3PXP | base32 -d | totp
    $ 123456

Or

    $ echo JBSWY3DPEHPK3PXP | totp -b
    $ 123456

## secret

It has been thought for [secret](https://github.com/angt/secret),
maybe it will be directly integrated in a future version, in the meantime:

### Add a new TOTP key

    $ echo -n JBSWY3DPEHPK3PXP | base32 -d | secret set test/totp
    
### Generate a TOTP token

    $ secret show test/totp | totp
    $ 123456
    
---
For feature requests and bug reports,
please create an [issue](https://github.com/angt/totp/issues).
