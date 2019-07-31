---
title: Create your XRP Multisign Account
description: Learn how to create your xrp multisign account using CryptoGlacier,
  the step-by-step, secure, multi-blockchain, multi-signature,
  cold storage protocol for long-term storage of crypto assets
  based on the popular Glacier Protocol
---

In this section you will create a [Ripple Multisign Account](https://xrpl.org/multi-signing.html).

CryptoGlacierScript has automated the process to [set up Multi-Signing](https://xrpl.org/set-up-multi-signing.html).

**As a reminder, this section should only be executed by one agreed upon
signatory.** If you are not that signatory, please skip this section.

1. On an internet enabled computer with CryptoGlacierScript already downloaded,
run the multisign account setup and follow the steps in the screen:
```
$ node setup.js -m
```
2. The script will output the <span class="warning">Ripple Cold Storage Address</span>
3. It will also output the <span class="danger">Ripple Cold Storage Secret</span>.
Even though the secret should be disabled, it is good practice to store it
somewhere in case of an emergency.
4. Send to the <span class="warning">Ripple Cold Storage Address</span> to the other signatories.
