---
title: Multi-signature security
description: CryptoGlacier uses multiple keys to protect your funds. This makes it
  harder for someone to steal your funds, and gives the protocol redundance in case
  of accidental key loss.
---

Central to our security protocol is
a technique called "multisignature security." You'll need a quick primer on
this topic to understand the CryptoGlacier protocol.

## Regular Private Keys are Risky

Remember that anybody with access to your private key can access your
funds. And if you lose your private key, you cannot access your money; it is
lost forever. There is no mechanism for reversal, and nobody to appeal
to.

This makes it difficult to keep funds highly secure. For example, you
might store a private key on paper in a safe deposit box at a bank, and feel
fairly safe. But even this is not the most robust solution. The box could be
destroyed in a disaster, or be robbed (perhaps via identity theft), or
[intentionally seized](http://abcnews.go.com/GMA/story?id=4832471).

You can try to mitigate these risks by storing the key yourself, perhaps in a
fireproof home safe (as opposed to a bank). But this introduces new risks. A
determined thief (perhaps a professional who brings safe-drilling tools on their
burglary jobs, or who somehow got wind of the fact that you have a $100,000
slip of paper sitting in a safe) might break into the safe and steal the wallet.

Or a major natural disaster might prevent you from returning home for an
extended period, during which time your safe is looted.

## What is Multisignature Security?

To address these issues, most cryptocurrency protocols provide a way to
secure funds with a set of private keys, such that some of the keys (but
not necessarily all) are required to withdraw funds. For example, you might
secure your funds with 3 keys but only need any 2 of those keys to withdraw
funds. (This example is known as a "2-of-3" withdrawal policy.)

The keys are generated and controlled by different entities in different
locations so someone who gets access to one key will not automatically
have access to the others. Key custodians are called "signatories."

This approach of using multiple
keys is known as "multisignature security." The "signature" part of
"multisignature" comes from the process of using a private key to access
funds, which is referred to as "signing a transaction." Multisignature
security is analogous to a bank requiring signatures from multiple people
(for example, any 2 of a company's 3 designated officers) to access funds in
an account.

## How Does Multisignature Security Help?

Multisignature security protects against the following scenarios:

* **Theft**: Even if somebody physically breaks into a safe, any one key is not
enough to steal the money.
* **Loss**: If a key is destroyed or simply misplaced, you can recover your money
using the remaining keys.
* **Key-man risk**:
By having multiple signatories you significantly reduce the risk of loss of funds
in case a signatory dies or becomes incapacitated. In the case of duress,
a single-signatory is unable to access funds.
* **Unilateral access**: With multisignature security, signatories with a key
will not be able to move funds (unless they steal additional key(s), or collude
with additional signatories). This allows for more institutional decision-making.

## Choosing a Multisignature Withdrawal Policy

An M-of-N Multisignature Withdrawal Policy will provide a way to enforce multi-person
control over fund access. N signatories will generate a key each so that M < N of them
(M of N) are needed in order to access funds, but no smaller group up to M -1 can do so.

For example, in a 1-of-2 setup, there would be two signatories and any one of them would
be able to spend funds. In a 2-of-3 setup, there would be three signatories and at least
two will be required to spend funds.

By choosiing M < N, you give up control but gain redundancy in the event of key loss.

Depending on your use case, you will need to optimize choosing your M-of-N policy. You will
need to select a policy before beginning the protocol.

## Signatory responsibilities

Each signatory is responsible for securing their key in a safe deposit box.
Signatories should make legal arrangements in advance so their key can be
accessed in case of death or incapacitation.

The most failsafe way to ensure a signatory's agent will have access to a
signatory's safe deposit box is to check with the bank. Standard estate
planning legal documents should allow a signatory's agent to access the box
upon a signatory's death or incapacitation. But banks can be fussy and
sometimes prefer their own forms.

## Choosing signatories

Consider the following when choosing signatories:

* **Availability**: If your signatory lives in a rural area, there may not be
many vaults or safe deposit boxes that are practical to get to.
* **Privacy**: Signatories will have the ability to see account balances.
* **Signatory collusion**: Although possessing one key won't allow a signatory
to access your funds, signatories might collude with each other to steal funds.
* **Signatory reliability**: A signatory may fail to store the key securely, or
they may lose it.
* **Geography risk**: Signatories should be located in different physical
locations to reduce the risk of loss of funds due to events that could affect wide
geographical areas, like natural disasters or power losses which could
potentially affect all your signatories' capability to sign transactions.
* **Jurisdiction risk**: Signatories should be located in different
jurisdictions to reduce the risk of a coordinated fund seizure attack.
* **Signatory safety**: Giving your signatories custody of a valuable key may
expose them to the risk of targeted physical theft.
* **Kidnapping risk**: If your signatories anticipate traveling in
[high-crime areas with kidnapping risk](http://www.nytimes.com/2012/05/03/business/kidnapping-becomes-a-growing-travel-risk.html),
funds will be at greater risk because a signatory will have the ability to
access them remotely (by contacting other signatories and asking for their
keys). Financially-motivated kidnapping hinges on a signatory's ability to
access funds to give to the kidnappers. If a signatory is literally unable to
access additional funds (because there are duress protocols in place or
signatories do not know of each other or don't have a way of contacting each
other), kidnappers will have no incentive to hold a signatory.
