---
title: Generating BIP39 Mnemonic
description: Learn how to generate a BIP39 mnemonic to use with CryptoGlacier,
  the step-by-step, secure, multi-blockchain, multi-signature,
  cold storage protocol for long-term storage of crypto assets
  based on the popular Glacier Protocol
redirect_from: /docs/deposit/
---

The Key Generation Protocol will securely generate a <span class="danger">24-word seed phrase</span> that will
be used to store all your assets.

We will be using the [BIP39](https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki)
standard to create a <span class="danger">24-word mnemonic</span>. We will then derive private keys for each protocol
using this 24-word mnemonic. Each signatory will only need to secure their 24-word phrase
in order to be able to access funds 

By the end of this section, each signatory will generate the following information:

* A <span class="danger">BIP39 Seed Phrase</span>: Each seed phrase is a 24-word combination that will later
be used to unlock your funds across BTC, BCH, LTC, XRP & ETH. Each seed phrase should be created in a different
device by a different signatory. In your M-of-N policy there should be N seed phrases. These phrases should always
be separated and signatories should never see each other seed phrases.
* A <span class="warning">Master public key for Bitcoin</span>: An alphanumeric
string to allow Electrum to generate the public keys for the BTC cold HD wallet
* A <span class="warning">Master public key for Bitcoin Cash</span>: An alphanumeric
string to allow Electron-Cash to generate the public keys for the BCH cold HD wallet
* A <span class="warning">Master public key for Litecoin</span>: An alphanumeric
string to allow Electrum-LTC to generate the public keys for the LTC cold HD wallet
* An <span class="warning">XRP address</span>: Address to give ownership of an
XRP multisign account
* An <span class="warning">ETH address</span>: Address to give ownership of an
ETH multisig contract


**<span style="color: red;">Only quarantined hardware should be used during the execution of the Key Generation
Protocol.</span>**

**<span style="color: red;">Signatories should not be in close proximity of each other when executing the Key Generation
Protocol. Signatory should always use distinct quarantined computers and should never ever share seed phrases.</span>**

1. If this is **not** your first time working with CryptoGlacier:
    1. Use a networked computer to access the latest full release of CryptoGlacier
    ( not just the protocol document) at <https://github.com/vogelito/CryptoGlacierProtocol/releases>.
    2. Open the protocol document (CryptoGlacier.pdf) within the ZIP file.
    3. Check the Release Notes (Appendix E) of the protocol document to see if
    there are any new versions of CryptoGlacier recommended.
    4. Whether or not you decide to upgrade, review the errata for the version
    of CryptoGlacier you are using at <https://github.com/vogelito/GlacierProtocol/releases>.
2. Execute [Section VI of the Setup Protocol](../setup/quarantined-workspace.md) to
prepare your quarantined workspace.
3. Create entropy for private keys

    Creating an unguessable private key requires
    *entropy* -- random data. We'll combine two sources of entropy to generate
    our keys. This ensures securely random keys even if *one* entropy source is
    somehow flawed or compromised to be less-than-perfectly random.

    1. Generate dice entropy
        1. Type "DICE ENTROPY" into both Quarantined Scratchpads.
        2. Roll 62 six-sided dice, shaking the dice thoroughly each roll.
        62 dice rolls corresponds to 160 bits of entropy. See the
        [design document](../design-doc/overview.md) for details.
        3. If you are rolling multiple dice at the same time, read the
        dice left-to-right. **This is important.** Humans are
        [horrible at generating random data](http://journals.plos.org/plosone/article?id=10.1371/journal.pone.0041531)
        and great at noticing patterns. Without a consistent heuristic like
        "read the dice left to right", you may subconsciously read them in a
        non-random order (like tending to record lower numbers first).
        This can drastically undermine the randomness of the data, and could be
        exploited to guess your private keys.
        4. Manually enter the <span class="danger">numbers</span> into the
        Quarantined Scratchpad of **<span style="color: red;">ONLY ONE</span>** of the quarantined computers.
        Put all rolls on the same line to create <span class="danger">one line of 62 numbers</span>. (It's fine
        to add spaces for readability.)

    2. Generate BIP39 seed phrase
        1. Make sure you are in the `~/cryptoglacier folder`:
           ```
           $ cd ~/cryptoglacier
           ```
        2. **On the Q1 computer** enter the following command to generate your
        BIP39 seed phrase
           ```
           $ node setup.js --init
           ```
        3. The script will prompt you to enter the 62-number line of dice entropy
        4. The script will output your cold storage data:
          * <span class="danger">Dice entropy</span>
          * <span class="danger">Generated Computer entropy</span>
          * <span class="danger">Final entropy</span>
          * <span class="danger">BIP39 Mnemonic</span>
          * <span class="warning">Bitcoin Master Public Key</span>
          * <span class="warning">Litecoin Master Public Key</span>
          * <span class="warning">Bitcoin Cash Master Public Key</span>
          * <span class="warning">Ethereum Address</span>
          * <span class="warning">Ripple Address</span>

           Example output:
           <pre><span class="danger" style="font-size: 11px;">Dice entropy:                         1111 1111 1111 1111 1111 1111 1111 1111 1111 1111 1111 1111 1111 1111 1111 11
           Generated Computer entropy:           aaaa aaaa aaaa aaaa aaaa aaaa aaaa aaaa aaaa aaaa
           Final entropy:                        ae29155ab1b3f5a1fc0c7cee883cd39457d273b9eb5eb6ac16a309bc7dd4d293
           BIP39 Mnemonic:                       purchase emerge find gloom dismiss special usual moon update draft crunch chunk large degree tray hint repeat gaze potato beach sick tuna engage hand</span>
           <span class="warning" style="font-size: 11px;">Bitcoin Master Public Key (Zpub):     Zpub75EpZYVWcoTQ1WChsnabzLUAm91t379iNBPM647HvyuXg2Pn9DtkyVkLWicg4CJzbLKYcSzYV6B1yLTUbjq5LMqkhrzRDW7ebTEaUvxHhUL
           Litecoin Master Public Key (Zpub):    Zpub75CcoXN1LVH6qE3MNYAAbd8f6c3pgJC8aT1L8crzZTifZQcjrJcJxRxL1o4UxLMHGg4YvBjDN8hHQaHrKsxsSwwApiX7b7goVDRQrpLLmB9
           BitcoinCash Master Public Key (xpub): xpub6BjfaUaRAzkDfaYWKGNDxewXDUpgkJdPTB7jo4hcDfFG5QwX6JqJEEKg1at6FkwMVsFYPKf3KyKBSiK7i3gXdYaBNc8m2TEHNARwfWasdcX
           Ethereum Address:                     0x6bff50edf67a2eae30e9eef7007b31292405ab2d
           Ripple Address:                       rHzjZTF4nD1ta2oPz7EYvYKXx26n8ZKFUv</span></pre>
        5. Type "COMPUTER ENTROPY" into both computers' Quarantined Scratchpads.
        (This is a descriptive heading to keep your notes organized and minimize
        risk of error.)
        6. Copy-paste the <span class="danger">Generated Computer entropy</span>
        into the Quarantined Scratchpad.
        7. Manually enter the <span class="danger">Generated Computer entropy</span>
        into the Quarantined Scratchpad on the other quarantined computer.

    3. Verify the integrity of the cold storage data
        1. **On the Q2 computer** enter the following command:
        ```
        $ node setup.js --check
        ```
        2. The script will prompt you to enter the 62-number dice entropy and
        the Generated computer entropy.
        3. Verify that the output of the script shown in the terminal window is
        identical on both computers:
            1. <span class="danger">BIP39 Mnemonic</span>
            2. <span class="warning">The Master Public Keys for Bitcoin
            Litecoin, and BitcoinCash</span>
            3. <span class="warning">Ethereum and Ripple Addresses</span>

            **For the BIP39 Mnemonic, the Master Public Key of Bitcoin, Litecoin
            BitcoinCash, and the Ethereum and Ripple address, verify every
            character**.

            There are attack vectors which could replace just a portion of private
            keys or a cold storage address, making the private keys easier to brute
            force, so it's important to check them thoroughly.
        4. In any one of the quarantined computers open bip39-standalone.html
           ```
           $ firefox ~/apps/bip39-standalone.html
           ```
        5. Check the `Show entropy details` checkbox
        6. Copy the <span class="danger">Final entropy</span> output of the
        script into the `Entropy` box and verify that the BIP39 seed matches

           Example output in the `BIP39 Mnemonic` section:

           <pre><span class="danger">purchase emerge find gloom dismiss special usual moon update draft crunch chunk large degree tray hint repeat gaze potato beach sick tuna engage hand</span></pre>

           **Verify every word of the BIP39 Mnemonic so it matches the output
           of the scripts on both computers**.

        7. **If there are any discrepancies, do not proceed.**
            1. Check whether the dice and the entropy in both Quarantined Scratchpads matches
            precisely.
                1. If they are different by 1-3 characters (presumably due to
                transcription errors), manually tweak them to make them match.
                It doesn't matter which scratchpad is tweaked.
                2. If they are different by more than 3 characters, restart the
                Key Generation Protocol.
                3. If they are identical, restart the Key Generation Protocol.
            2. Seek assistance if discrepancies persist.
