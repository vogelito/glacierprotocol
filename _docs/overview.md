---
title: About CryptoGlacier
description: CryptoGlacier is the step-by-step, secure, multi-blockchain,
  multi-signature, cold storage protocol for long-term storage of crypto assets
  based on the popular Glacier Protocol
redirect_from:
  - /docs/
---

CryptoGlacier is a step-by-step protocol for storing crypto assets in a
highly secure manner. It is based on the popular [Glacier Protocol](https://glacierprotocol.org/).

There are two main differences between CryptoGlacier and Glacier:
* CryptoGlacier adds support for other cryptocurrencies
* CryptoGlacier is not intended for personal storage, but situations where
various, distinct, keyholders must agree with each other to access funds

CryptoGlacier **does not address institutional security**
needs such as internal controls, and transparent auditing. It **does prevent**
access to funds by a single individual.

Just as Glacier, CryptoGlacier is also intended for:

* **Large amounts of money ($100,000+)**: CryptoGlacier thoroughly considers corner
cases such as obscure vectors for malware infection, human error resulting in loss
of funds, and so on.
Even if your crypto holdings are more modest, it's worth considering using
CryptoGlacier. If crypto proves successful as a technology, it will appreciate
10x (or much more) in the coming years. Security will become increasingly
important if your holdings appreciate and crypto becomes a more attractive
target for thieves.
Consider [Glacier Protocol](https://glacierprotocol.org/) if you're looking for
personal storage.
* **Long-term storage**: CryptoGlacier not only considers the crypto security
landscape today, but also a future world where crypto is much more valuable
and attracts many more security threats.
* **Infrequently-accessed funds**: Accessing highly secure funds is
cumbersome and introduces security risk through the possibility of human
error, so it is best done infrequently.
* **Technically unskilled users**: Although the CryptoGlacier protocol is long, it is
clear and straightforward to follow. Some technical expertise is required.

The CryptoGlacier protocol covers crypto storage, not procurement. It assumes you
already possess crypto and wish to store it more securely.

If you are already familiar with crypto security concepts and are certain that
you want high security, multi-signature, cold storage, you may prefer to read
[Trusting This Protocol](#trusting-this-protocol) and then skip to the section
[Choosing a Multisignature Withdrawal Policy](../overview/multi-signature-security#choosing-a-multisignature-withdrawal-policy).

## Supported Cryptocurrencies

This document currently supports:
* Bitcoin
* Bitcoin Cash
* Ethereum
* Etherum-based ERC20 tokens
* Litecoin
* XRP



## Trusting this protocol

Funds secured using CryptoGlacier can only be as secure as its design.
As previously mentioned, CryptoGlacier is based on the Glacier protocol but
has some important distinctions and at the time of writting it hasn't yet
attracted widespread Expert Advisory or Community Review.

CryptoGlacier and CryptoGlacierScript, the CryptoGlacier companion software,
are **open source**. The code is straightforward and well-commented to
facilitate easy review for flaws or vulnerabilities.
[View it on Github](https://github.com/vogelito/CryptoGlacierProtocol).

All documentation and code related to this protocol is under open licenses
(Creative Commons for the document, MIT license for the code), enabling others
to publish their own revisions. Inferior alternatives will tend to lose
popularity over time.

If you like, you may review the [design document](../design-doc/overview)
of the Glacier Protocol for details on the technical design.

## Background

### Glacier vs CryptoGlacier

Let's start by assessing whether Glacier or CryptoGlacier is right for you. Some
advantages of CryptoGlacier include:
* **Storing multiple crypto assets**: Although Bitcoin remains the most popular
cryptocurrency, today we have hundreds of crypto assets which are currently not
supported by the Glacier protocol.
* **BIP39 Mnemonics**: CryptoGlacier allows you to derive keys across
crypto-protocols by storing a 24-word mnemonic. This adds simplicity for key-storage
and supports multiple protocols.
* **Multiple key holders**: CryptoGlacier was designed for multiple key holders and
prevents a single entity from ever having unilateral access to funds. Glacier is
meant for personal storage of Bitcoin where a single individual can always access
funds unilaterally.
* **HD wallets for Bitcoin, Bitcoin Cash and Litecoin**: CryptoGlacier
increases privacy by utilizing HD wallets instead of reusing addresses as the
original Glacier Protocol does.

### Self-Managed Storage vs. Managed by a third party

There is no such thing as perfect security. There are only degrees of security,
and those degrees come at a cost (in time, money, convenience, etc.) So the
first question is: How much security are you willing to invest in?
In the last few years we've seen a rise of 3rd party institutional custody
solutions for crypto assets. Most allow for multiple signatories, estate planning,
etc. The pros and cons of the various 3rd party services are beyond the scope of
this document. Some options are
[BitGo](https://bitgo.com/),
[Coinbase Custody](https://custody.coinbase.com/),
[Ledger Vault](https://www.ledger.com/vault/), and
[Vo1t](https://vo1t.io/).

However, all 3rd party storage services still come with some notable risks
which self-managed storage does not have:

1. **Identity spoofing**: Your account on the service could be hacked (including
through methods such as identity theft, where someone convinces the service they
are you).
2. **Network exposure**: 3rd party services still need to transmit security-critical
information over the Internet, which creates an opportunity for that information
to be stolen. In contrast, self-managed storage can be done with no network
exposure.
3. **Under constant attack**: 3rd party services can be hacked by attackers from
anywhere in the world. People know these services store lots of funds, which
makes them much larger targets. If there's a flaw in their security, it's more
likely to be found and exploited.
4. **Internal theft**: They have to protect against internal theft from a large
group of employees & contractors.
5. **Intentional seizure**: They have the ability (whether of their own volition,
or under pressure from governments) to seize your funds.
There is historical precedent for this, even if funds are not suspected of
criminal involvement. In 2010,
[Cyprus unilaterally seized many bank depositors' funds ](https://www.theguardian.com/world/2013/mar/25/cyprus-bailout-deal-eu-closes-bank)
to cope with an economic crisis. In 1933, the US abruptly
[demanded citizens surrender almost all gold they owned to the government](https://en.wikipedia.org/wiki/Executive_Order_6102).
Regardless of how one views the political desirability of these particular
decisions, there is precedent for governments taking such an action, and one
cannot necessarily predict the reasons they might do so in the future.
Furthermore, Bitcoin still operates in a political and legal gray zone, which
increases these political risks.

Some 3rd party services have insurance to cover losses, although that
insurance doesn't protect against all of these scenarios, and often has limits
on the amount insured.

These risks are not theoretical. Many online services have lost customers' funds
(and not reimbursed them), including
[Mt. Gox](https://www.bloomberg.com/news/articles/2014-02-28/mt-gox-exchange-files-for-bankruptcy),
[Bitfinex](http://www.bbc.com/news/technology-37009319),
and many more.

Many people use online or hybrid solutions to store sizeable amounts of
money. We recommend self-managed storage for large holdings, but ultimately
it's a personal decision based on your risk tolerance and costs you're willing
to pay (in money and time) for security.

CryptoGlacier focuses exclusively on storage managed by different entities
where not a single entity has unilateral control over the funds.

### CryptoGlacier vs. Hardware Wallets

Many people who choose
self-managed storage (as opposed to an online storage service) use "hardware
wallets" such as the
[Trezor](https://trezor.io/),
[Ledger](https://www.ledgerwallet.com/),
and [KeepKey](https://www.keepkey.com/)
to store their crypto. These products can be setup in a way where multi-signature
is required to move funds. While these are great products that provide strong security,
CryptoGlacier is intended to offer an even higher level of protection than today's
hardware wallets can provide.

The primary security consideration is that
all hardware wallets today operate via a physical USB link to a regular
computer. While they employ extensive safeguards to prevent any sensitive
data (such as private keys) from being transmitted over this connection,
it's possible that an undiscovered vulnerability could be exploited by
malware to steal private keys from the device.

For details on this and other security considerations, see the
"No Hardware Wallets" section of the [design document](../design-doc/overview).
As with online multisig vaults, many people do use hardware wallets to store sizeable
amounts of money. We personally recommend CryptoGlacier for large holdings, but
ultimately it's a personal decision based on your risk tolerance and costs you're
willing to pay (in money and time) for security.
