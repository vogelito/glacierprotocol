---
title: Setup Integrity Verification Protocol
description: Learn how to verify the integrity of the setup with Glacier, the
  step-by-step protocol for storing bitcoins in a highly secure way
---

The Setup Integrity Verification Protocol is used to make sure that the setup was not compromised. This step
must take place before the actual private keys for the devices are generated.

**<span style="color: red;">Only quarantined hardware should be used during the execution of the Setup
Integrity Verification.</span>**

1. Execute [Section VI of the Setup Protocol](../setup/quarantined-workspace.md) to
prepare your quarantined workspace.
2. Test setup of quarantined hardware

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
        4. Manually enter the **numbers** into the
        Quarantined Scratchpads on *all* quarantined computers. Put all rolls on
        the same line to create **one line of 62 numbers**. (It's fine to add
        spaces for readability.)


    2. Generate test BIP39 entropy
        1. Type "COMPUTER ENTROPY" into all computers' Quarantined Scratchpads.
        (This is a descriptive heading to keep your notes organized and minimize
        risk of error.)

       **On the Q1 computer**
        2. Make sure you are in the `~/apps folder`:
           ```
           $ cd ~/apps
           ```
        3. Enter the following command:
           ```
           $ ./mnemonic_entropy.py entropy
           ```
        4. The script will prompt you to enter the 62-number line of dice entropy. It will output:
            * Computer Entropy
            * BIP39 Entropy

           Example output:

           <pre>Making a random data string....
           If strings don't appear right away, please continually move your mouse cursor. These movements generate entropy which is used to create random data.

           Generated Computer entropy: f324 12a2 03fd ad07 60a5 6edd d6d9 0617 78d8 e680

           Generated Entropy (copy this string into bip39-standalone.html): b09b3eff97116351dbd9b2c93105c077a7cbe2d14bee0746b2ddb3005c7cb150</pre>
        5. Manually copy the `Generated Computer entropy` output into the Quarantined Scratchpad on all the other quarantined computers
        6. Open bip39-standalone.html
           ```
           $ xdf-open ~/apps/bip39-standalone.html
           ```
        7. Check the `Show entropy details` checkbox
        8. Copy the output of `Generated Entropy (copy this string into bip39-standalone.html)` from the script into the `Entropy` box


    3. Generate BIP39 mnemonic verification data information using your generated entropy

       **On every other computer except Q1:**
        1. Make sure you are in the `~/apps folder`:
           ```
           $ cd ~/apps
           ```
        2. Enter the following command:
           ```
           $ ./mnemonic_entropy.py entropy --integrity
           ```
        3. The script will prompt you to enter the 62-number line of dice entropy and the `Generated Computer entropy` previously manually copied
        to all other computer's Quarantined Scratchpad under `COMPUTER ENTROPY`
        3. The escript will output your setup verification data:
            * Computer Entropy
            * BIP39 Entropy

           Example output:

           <pre>Generated Entropy (copy this string into bip39-standalone.html): b09b3eff97116351dbd9b2c93105c077a7cbe2d14bee0746b2ddb3005c7cb150</pre>
        4. Open bip39-standalone.html
           ```
           $ xdf-open ~/apps/bip39-standalone.html
           ```
        5. Check the `Show entropy details` checkbox
        6. Copy the output of `Generated Entropy (copy this string into bip39-standalone.html)` from the script into the `Entropy` box
        7. Verify that the 24 words generated in the `BIP39 Mnemonic` section is identical across computers
        8. **If there are any discrepancies, do not proceed.**
            1. Check whether the numbers and the entropy in all Quarantined Scratchpads matches
            precisely.
                1. If they are different by 1-3 characters (presumably due to
                transcription errors), manually tweak them to make them match.
                It doesn't matter which scratchpads are tweaked.
                2. If they are different by more than 3 characters, restart the
                Deposit Protocol.
                3. If they are identical, restart the Setup Integrity Verification Protocol.
            2. Seek assistance if discrepancies persist. Your setup might be compromised.

    4. Verify private keys
        1. The following steps must be made **on every computer**
        2. **<span style="color: red;">TODO:</span>** missing xrp, btc, bch, ltc, and eth keys. Verify that the output of GlacierScript shown in the terminal
        window is identical on all computers:
            1. <span class="danger">All private keys</span>
            2. <span class="warning">Cold storage address</span>
            3. <span class="warning">Redemption script</span>

            **For the private keys and cold storage address, verify every
            character**. For the redemption script, it's sufficient to check
            the first 8 characters, last 8 characters, and a few somewhere in
            the middle.

            There are attack vectors which could replace just a portion of private
            keys or a cold storage address, making the private keys easier to brute
            force, so it's important to check them thoroughly. If we know the private keys
            and cold storage address are good, then the redemption script is almost
            certainly good as well; a painstaking manual verification is not required.

        3. **If there are any discrepancies, do not proceed.**
            1. Check whether the entropy in all Quarantined Scratchpads matches
            precisely.
                1. If they are different by 1-3 characters (presumably due to
                transcription errors), manually tweak them to make them match.
                It doesn't matter which scratchpads are tweaked.
                2. If they are different by more than 3 characters, restart the
                Deposit Protocol.
                3. If they are identical, restart the Setup Integrity Verification Protocol.
            2. Seek assistance if discrepancies persist. Your setup might be compromised.

        4. **<span style="color: red;">TODO: This is missing BIP39, Electrum, Electrum-LTC, Electron-Cash and Multisigweb's verification.</span>**

    5. Begin multi-device protocol
        1. Delete the contents of the Quarantined Scratchpads on each computer
        2. **<span style="color: red;">Quarantined hardware should never be allowed to be
        turned on in close proximity to one another.</span>**

