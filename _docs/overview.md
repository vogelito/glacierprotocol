---
title: About CryptoGlacier
description: CryptoGlacier is a step-by-step protocol for long-term storage of
  various cryptocurrencies, in an offline and secure way.
redirect_from:
  - /docs/
---

CryptoGlacier is based on [Glacier](https://glacierprotocol.org/), the step-by-step
protocol for storing bitcoins in a highly secure manner.

There are two main differences between CryptoGlacier and Glacier:
* CryptoGlacier adds support for other cryptocurrencies
* CryptoGlacier is not intended for personal storage, but situations where
various, distinct, keyholders must agree with each other to access funds
* CryptoGlacier **does not address institutional security**
needs such as internal controls, and transparent auditing. It **does prevent**
access to funds by a single individual.

Just as Glacier, CryptoGlacier is also intended for:

* **Large amounts of money ($100,000+)**: CryptoGlacier thoroughly considers corner
cases such as obscure vectors for malware infection, personal estate
planning, human error resulting in loss of funds, and so on.
Even if your crypto holdings are more modest, it's worth considering using
CryptoGlacier. If Bitcoin proves successful as a global currency, it will appreciate
10x (or much more) in the coming years. Security will become increasingly
important if your holdings appreciate and Bitcoin becomes a more attractive
target for thieves.
The "Protocol Overview" section also describes some lower-security, lower-cost
approaches to self-managed storage that may be more appropriate for smaller
amounts of funds.
* **Long-term storage**: CryptoGlacier not only considers the crypto security
landscape today, but also a future world where crypto is much more valuable
and attracts many more security threats.
* **Infrequently-accessed funds**: Accessing highly secure funds is
cumbersome and introduces security risk through the possibility of human
error, so it is best done infrequently.
* **Technically unskilled users**: Although the CryptoGlacier protocol is long, it is
clear and straightforward to follow. No technical expertise is required.

The CryptoGlacier protocol covers crypto storage, not procurement. It assumes you
already possess bitcoins and wish to store them more securely.

If you are already familiar with crypto security concepts and are certain that
you want high security cold storage, you may prefer to read
[Trusting This Protocol](#trusting-this-protocol) and then skip to the section
[Choosing a Multisignature Withdrawal Policy](../overview/multi-signature-security#choosing-a-multisignature-withdrawal-policy).

## Supported Cryptocurrencies

This document currently support Bitcoin, Litecoin, XRP, BitcoinCash, Ether
and ERC20 tokens on top of the Ethereum protocol

## Trusting this protocol

Funds secured using CryptoGlacier can only be as secure as its design.
As previously mentioned, CryptoGlacier is based on the Glacier protocol but
has some important distinctions and at the time of writting it hasn't yet
attracted widespread Expert Advisory or Community Review.

Just as Glacier, CryptoGlacier is **Open source**: CryptoGlacierScript, the
CryptoGlacier companion software, is open source. The code is straightforward
and well-commented to facilitate easy review for flaws or vulnerabilities.
[View it on Github](https://github.com/vogelito/CryptoGlacierScript).

All documentation and code related to this protocol is under open licenses
(Creative Commons for the document, MIT license for the code), enabling others
to publish their own revisions. Inferior alternatives will tend to lose
popularity over time.

If you like, you may review the [design document](../design-doc/overview.md)
for details on the technical design.

## Background

### Self-Managed Storage vs. Online

Let's start by assessing whether CryptoGlacier is right for you.

There is no such thing as perfect security. There are only degrees of security,
and those degrees come at a cost (in time, money, convenience, etc.) So the
first question is: How much security are you willing to invest in?
For most people, most of the time, the authors recommend storing crypto using a
high-quality online storage service. The pros and cons of the various online
services are beyond the scope of this document, but most popular ones are fairly
secure and easy to use. Some popular options are
[Blockchain](https://blockchain.info/),
[Bitso](https://bitso.com/),
[Coinbase](https://www.coinbase.com/),
[Gemini](https://gemini.com/),
and [Kraken](https://www.kraken.com/).

However, all online storage services still come with some notable risks
which self-managed storage does not have:

1. **Identity spoofing**: Your account on the service could be hacked (including
through methods such as identity theft, where someone convinces the service they
are you).
2. **Network exposure**: Online services still need to transmit security-critical
information over the Internet, which creates an opportunity for that information
to be stolen. In contrast, self-managed storage can be done with no network
exposure.
3. **Under constant attack**: Online services can be hacked by attackers from
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
Furthermore,Bitcoin still operates in a political and legal grey zone, which
increases these political risks.

Some online wallet services have insurance to cover losses, although that
insurance doesn't protect against all of these scenarios, and often has limits
on the amount insured.

These risks are not theoretical. Many online services have lost customers' funds
(and not reimbursed them), including
[Mt. Gox](https://www.bloomberg.com/news/articles/2014-02-28/mt-gox-exchange-files-for-bankruptcy),
[Bitfinex](http://www.bbc.com/news/technology-37009319),
and many more.

Recently, some providers are rolling out services which are a hybrid
of an online service and self-managed storage. Examples include
[Coinbase's multisig vault](https://www.coinbase.com/vault)
and [Green Address](https://greenaddress.it/en/).
The design of these services
significantly reduces (though does not eliminate) the risks described above.

However, they also require some care and technical competence to securely
manage the electronic "keys" which provide access to funds.

Many people do use online or hybrid solutions to store sizeable amounts of
money. We recommend self-managed storage for large investments, but ultimately
it's a personal decision based on your risk tolerance and costs you're willing
to pay (in money and time) for security.

CryptoGlacier focuses exclusively on storage managed by different entities
where not a single entity has unilateral control over the funds

### CryptoGlacier vs. Hardware Wallets

Many people who choose
self-managed storage (as opposed to an online storage service) use "hardware
wallets" such as the
[Trezor](https://trezor.io/),
[Ledger](https://www.ledgerwallet.com/),
and [KeepKey](https://www.keepkey.com/)
to store their crypto. While these are great products that provide strong security,
CryptoGlacier is intended to offer an even higher level of protection than today's
hardware wallets can provide.

The primary security consideration is that
all hardware wallets today operate via a physical USB link to a regular
computer. While they employ extensive safeguards to prevent any sensitive
data (such as private keys) from being transmitted over this connection,
it's possible that an undiscovered vulnerability could be exploited by
malware to steal private keys from the device.

For details on this and other security considerations, see the
"No Hardware Wallets" section of the [design document](../design-doc/overview.md)
As with online multisig
vaults, many people do use hardware wallets to store sizeable amounts of
money. We personally recommend CryptoGlacier for large investments, but ultimately
it's a personal decision based on your risk tolerance and costs you're
willing to pay (in money and time) for security.
