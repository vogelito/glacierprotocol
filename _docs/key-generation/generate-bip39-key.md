---
title: Generating Cold Storage Keys
description: Learn how to generate cold storage keys to use with CryptoGlacier,
  the step-by-step, secure, multi-blockchain, multi-signature,
  cold storage protocol for long-term storage of crypto assets
  based on the popular Glacier Protocol
redirect_from: /docs/deposit/
---

The Deposit Protocol is used to transfer bitcoins into high-security cold storage. If you have previously used the
Deposit Protocol to deposit funds into cold storage, and want to deposit
additional funds to the same cold storage address, skip to Section IV.

By the end of this section, you will generate the following information.

* The <span class="danger">*N* BIP39 seeds</span>: Each seed is a 24-word combination that will later
be used to unlock your funds across BTC, BCH, LTC, XRP & ETH. You'll create several private keys on
different devices, depending on the multisignature withdrawal policy you choose (e.g. 4 keys for a 2-of-4 withdrawal
policy).

In this protocol, the total number of private keys you're creating will be
referred to as *N*. Each key will be created in a separate device.
* <span class="warning">*N* master keys for Bitcoin</span>: An alphanumeric
string to allow Electrum to generate the public keys for the BTC cold HD wallet
* <span class="warning">*N* master keys for Bitcoin Cash</span>: An alphanumeric
string to allow Electron-Cash to generate the public keys for the BCH cold HD wallet
* <span class="warning">*N* master keys for Litecoin</span>: An alphanumeric
string to allow Electrum-LTC to generate the public keys for the LTC cold HD wallet
* <span class="warning">*N* addresses for XRP</span>: Addresses to give ownership of an
XRP multisign account
* <span class="warning">*N* addresses for ETH</span>: Addresses to give ownership of an
ETH multisig contract


**<span style="color: red;">Only quarantined hardware should be used during the execution of the Deposit
Protocol.</span>**

**<span style="color: red;">Quarantined computers should not be used in close proximity of other quarantined computers.</span>**

1. If this is **not** your first time working with Glacier:
    1. Use a networked computer to access the latest full release of Glacier
    ( not just the protocol document) at <https://github.com/GlacierProtocol/GlacierProtocol/releases>.
    2. Open the protocol document (Glacier.pdf) within the ZIP file.
    3. Check the Release Notes (Appendix E) of the protocol document to see if
    there are any new versions of Glacier recommended.
    4. Whether or not you decide to upgrade, review the errata for the version
    of Glacier you are using at <https://github.com/GlacierProtocol/GlacierProtocol/releases>.
2. Execute [Section VI of the Setup Protocol](/docs/setup/quarantined-workspace/) to
prepare your quarantined workspace.
3. Create entropy for private keys

    Creating an unguessable private key requires
    *entropy* -- random data. We'll combine two sources of entropy to generate
    our keys. This ensures securely random keys even if *one* entropy source is
    somehow flawed or compromised to be less-than-perfectly random.

    1. Generate dice entropy
        1. Type "DICE ENTROPY" into all Quarantined Scratchpads.
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


    2. Generate BIP39 entropy
      **On the the quarantined computer where the key is to be generated**
        1. Make sure you are in the `~/apps folder`:
           ```
           $ cd ~/apps
           ```
        2. Run the following command to generate private key entropy
           ```
           $ ./mnemonic_entropy.py entropy
        3. The script will prompt you to enter the 62-number line of dice entropy
        4. The script will output your generated BIP39 entropy

           Example output:
           <pre><span class="danger" style="font-size: 11px;">Generated Entropy (copy this string into bip39-standalone.html): 1f5c58f480c19e7bb6a566444f93266aa62e37c97bb28b0658effba47e563bd1</span></pre>

    3. Generate new BIP39 Mnemonic using your entropy

       **On the the quarantined computer where the key is to be generated**
        1. Open bip39-standalone.html
           ```
           $ xdf-open ~/apps/bip39-standalone.html
           ```
        2. Check the `Show entropy details` checkbox
        3. Copy the <span class="danger" style="font-size: 11px;">Generated Entropy</span> into the `Entropy` box

           Example output in the `BIP39 Mnemonic` section:

           <pre><span class="danger">butter tissue diamond account boring differ surround proud dust lady sister stem glass brief chalk iron mention crazy desk warrior elevator climb urban chat</span></pre>
