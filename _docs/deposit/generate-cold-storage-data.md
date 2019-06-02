---
title: Generate cold storage data
description: Learn how to generate cold storage data to use with Glacier, the
  step-by-step protocol for storing bitcoins in a highly secure way
redirect_from: /docs/deposit/
---

The Deposit Protocol is used to transfer bitcoins into high-security cold storage. If you have previously used the
Deposit Protocol to deposit funds into cold storage, and want to deposit
additional funds to the same cold storage address, skip to Section IV.

By the end of this section, you will generate the following information.

* The <span class="danger">*N* private keys</span>: These are the keys that will later
be used to unlock your funds. You'll create several private keys, depending on the
multisignature withdrawal policy you chose (e.g. 4 keys for a 2-of-4 withdrawal
policy).

  In this protocol, the total number of private keys you're creating will be
referred to as *N*. Each key will be created in a separate device.
* The <span class="warning">cold storage address</span>: An alphanumeric
string indicating the virtual location of your funds.
* The <span class="warning">redemption script</span>: An additional key
needed to access any funds deposited. There is only one redemption script for
each set of private keys. A copy will be stored with each private key.

**<span style="color: red;">Only quarantined hardware should be used during the execution of the Deposit
Protocol unless explicitly instructed otherwise.</span>**

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
3. Create entropy and private keys to test setup

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
        Quarantined Scratchpads on *all* quarantined computers. Put all rolls on
        the same line to create
        <span class="danger">one line of 62 numbers</span>. (It's fine to add
        spaces for readability.)


    2. Generate computer entropy    
        1. Type "COMPUTER ENTROPY" into all computers' Quarantined Scratchpads.
        (This is a descriptive heading to keep your notes organized and minimize
        risk of error.)
        2. Make sure you are in the `~/glacier folder`:
           ```
           $ cd ~/glacier
           ```
        3. **On the Q1 computer** enter the following command:
           ```
           $ ./glacierscript.py entropy --num-keys 1
           ```
           Example output:

           <pre><span class="danger" style="font-size: 11px;">Computer entropy #1: f8e1 39f4 8dd2 129c 689c 1cb1 1280 79fe db56 573f</span></pre>
        4. Copy-paste the output into the Quarantined Scratchpad.
        5. Manually copy the output into the Quarantined Scratchpad on all the other quarantined computers.


    3. Generate new cold storage data information using your entropy

       **On the Q1 computer:**
        1. Run GlacierScript to generate the private keys.
           ```
           $ ./glacierscript.py create-deposit-data -m 1 -n 1
           ```
        2. GlacierScript will prompt you to enter the 62-number line of dice entropy and the line of computer entropy.
        3. GlacierScript will output your cold storage data:
            * 1 private key
            * A cold storage address
            * A redemption script

           Example output:

           <pre><span class="danger">Private keys:
           Key #1: 5JAwK9bihMRFe9zw32csUUEn7N5MvLvuwXKv5qUnQVjbthZyuwQ</span>

           <span class="warning" style="white-space: pre-wrap;">Cold storage address:
           3Hy6A3rSXKRumyVqURBoiv4QpQLt6vMCzt

           Redemption script:
           51410421167f7dac2a159bc3957e3498bb6a7c2f16874bf1fbbe5b523b3632d2c0c43f1b491f6f2f449ae45c9b0716329c0c2dbe09f3e5d4e9fb6843af083e222a70a441043704eafafd73f1c32fafe10837a69731b93c0179fa268fc325bdc08f3bb3056b002eac4fa58c520cc3f0041a097232afbe002037edd5ebdab2e493f18ef19e9052ae</span>

           QR code for cold storage address in address.png
           QR code for redemption script in redemption.png</pre>

    4. Verify the integrity of the cold storage data.
        1. **On every other computer**, repeat step (c) above.
        2. Verify that the output of GlacierScript shown in the terminal
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
            certainly good as well. And if there are any errors in the redemption script,
            they will be caught during the test deposit & withdrawal process later in the
            protocol; a painstaking manual verification is not required.

        3. **If there are any discrepancies, do not proceed.**
            1. Check whether the entropy in all Quarantined Scratchpads matches
            precisely.
                1. If they are different by 1-3 characters (presumably due to
                transcription errors), manually tweak them to make them match.
                It doesn't matter which scratchpads are tweaked.
                2. If they are different by more than 3 characters, restart the
                Deposit Protocol.
                3. If they are identical, restart the Deposit Protocol.
            2. Seek assistance if discrepancies persist. Your setup might be compromised.
