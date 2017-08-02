# Ethereum Foos - A Curated List Of Costly Ethereum Mistakes To Learn From

This is a list of costly mistakes that have occurred in the Ethereum ecosystem, and some suggestions on how to mitigate the risk of
this happening to you.

<br />

<hr />

## Table Of Contents

* [Mismatch Of Private And Public Keys](#mismatch-of-private-and-public-keys)

<br />

<hr />

## Mismatch Of Private And Public Keys

I was using the [ethaddress.org](https://github.com/ryepdx/ethaddress.org) software to generate a bulk list of paper wallets. I
produced 80+ pairs of private and public keys.

Being paranoid, I tested each generated pair by importing the private key into `geth` using the command 
`geth account import {privatekeyfile}` and I found some of the generated public keys did not match.

So I created my first ever open source issue [#19 Invalid public key / private key generated](https://github.com/ryepdx/ethaddress.org/issues/19).

It turned out that a downstream library used by ethaddress.org had a bug that generated incorrect private and public key pairs -
[ #14 Update ethereumjs-tx dependency](https://github.com/SilentCicero/ethereumjs-accounts/pull/14).

<br />

### How To Prevent This Happening To You

* Always test your new accounts before sending substantial amounts to your account.

<br />

<br />

(c) BokkyPooBah / Bok Consulting Pty Ltd and others - July 23 2017. The MIT Licence.