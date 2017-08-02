# Ethereum Foos - A Curated List Of Costly Ethereum Mistakes To Learn From

Status: Just commencing work on this. Enter a GitHub issue if you have further information to include into this report.

This is a list of costly mistakes that have occurred in the Ethereum ecosystem, and some suggestions on how to mitigate the risk of
this happening to you.

<br />

<hr />

## Table Of Contents

* [Check Your Crowdsale Contract Parameters](#check-your-crowdsale-contract-parameters)
* [Even Commonly Used Software Can Have Costly Bugs](#even-commonly-used-software-can-have-costly-bugs)
* [Mismatch Of Private And Public Keys](#mismatch-of-private-and-public-keys)

<br />

<hr />

## Check Your Crowdsale Contract Parameters

Jul 31 2017

[REXMls](http://rexmls.com/)'s deployed their [RexToken](contracts/RexToken_DeployedAt_0x99d439455991f7f4885f20c634c9a31918d366e5.md) crowdsale contract to
[0x99d439455991f7f4885f20c634c9a31918d366e5](https://etherscan.io/address/0x99d439455991f7f4885f20c634c9a31918d366e5#code) with an incorrect
`vault` address.

Ethers contributions to the crowdsale contract were transferred to the incorrect `vault` address [0x3e4b00b607d0980668ca6e50201576b00000000](https://etherscan.io/address/0x3e4b00b607d0980668ca6e50201576b00000000),
instead of the correct `vault` address of [0x03e4b00b607d09811b0fa61cf636a6460861939f](https://etherscan.io/address/0x03e4b00b607d09811b0fa61cf636a6460861939f).

As no one has the private key to the incorrect address, the amount is forever locked in the incorrect address.

### Losses

* [6,687.6257271739995 ETH](https://etherscan.io/address/0x03e4b00b607d0980668ca6e50201576b00000000#internaltx)

### How To Prevent This Happening To You

* Always triple check the parameters in your crowdsale contract before releasing the address to participants
* If possible, send a contribution transaction of your own and check that the ethers reach the destination account correctly

### Further Information

* [Did REXmls ICO just lost 6600 ETH due to a copy&paste error?](https://www.reddit.com/r/ethtrader/comments/6qryc2/did_rexmls_ico_just_lost_6600_eth_due_to_a/)
* [The Solution](https://blog.rexmls.com/the-solution-a2eddbda1a5d)

<br />

<hr />

## Even Commonly Used Software Can Have Costly Bugs

Jun 18 2016

A hacker found a vulnerability in the Parity Multisig and stole ~ USD 32 million from 3 of these multisig wallets after exploiting this vulnerablity. The groups suffering losses from
this hack were [Edgeless](https://medium.com/@tomasdraksas/edgeless-response-to-parity-hack-3e35e20ba85c),
[Swarm City](https://press.swarm.city/follow-up-statement-from-the-swarm-city-core-team-3ab0f1274ad3) and
[æternity](https://blog.aeternity.com/parity-multisig-wallet-hack-47cc507d964d). 

The White Hat Group checked the 500+ wallets suffering from the same vulnerability and exploited this vulnerability to secure ~ USD 208 million before returning all the funds back to
the original owners. 

### Losses

* ~ USD 32 million

### How To Prevent This Happening To You

* Don't rely on software that is commonly used if you have to secure a large amount of funds. Check that you are using the correct version of the software, and this this software
  has been sufficiently checked, tested and audited

### Further Information

* [Parity Multisig Vulnerability - White Hat Group Rescue Reconciliation](https://github.com/bokkypoobah/ParityMultisigRecoveryReconciliation)
* [The WHG has Returned 100% of the Rescued Funds to their Rightful Owners](https://www.reddit.com/r/ethereum/comments/6qrjr5/the_whg_has_returned_100_of_the_rescued_funds_to/)
* [An In-Depth Look at the Parity Multisig Bug](http://hackingdistributed.com/2017/07/22/deep-dive-parity-bug/)

<br />

<hr />

## Mismatch Of Private And Public Keys

Feb 8 2016

I was using the [ethaddress.org](https://github.com/ryepdx/ethaddress.org) software to generate a bulk list of paper wallets. I
produced 80+ pairs of private and public keys.

Being paranoid, I tested each generated pair by importing the private key into `geth` using the command 
`geth account import {privatekeyfile}` and I found some of the generated public keys did not match.

So I created my first ever open source issue [#19 Invalid public key / private key generated](https://github.com/ryepdx/ethaddress.org/issues/19).

It turned out that a downstream library used by ethaddress.org had a bug that generated incorrect private and public key pairs -
[ #14 Update ethereumjs-tx dependency](https://github.com/SilentCicero/ethereumjs-accounts/pull/14).

### Losses

* 121 ETH - [Trying to recover my 121 ETH from 2015 js bug](https://www.reddit.com/r/ethereum/comments/6chqyk/trying_to_recover_my_121_eth_from_2015_js_bug/)

### How To Prevent This Happening To You

* Always test your new accounts before sending substantial amounts to your account
  * Test by unlocking your private key in another client and check the public key
  * Test by sending a small amount of ethers to your new account, then sending back the ethers to the originating account

### Further Information

* [PSA: Check your EthAddress.org wallets (and any other wallet generated using ethereumjs-accounts)](https://www.reddit.com/r/ethereum/comments/47nkoi/psa_check_your_ethaddressorg_wallets_and_any/)

<br />

<br />

(c) BokkyPooBah / Bok Consulting Pty Ltd - Aug 2 2017. The MIT Licence.