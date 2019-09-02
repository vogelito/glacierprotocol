---
title: Withdrawing Bitcoin, Litecoin or BitcoinCash
description: Learn how to withdraw funds using CryptoGlacier,
  the step-by-step, secure, multi-blockchain, multi-signature,
  cold storage protocol for long-term storage of crypto assets
  based on the popular Glacier Protocol
---

In this section, we first construct a transaction, which we then pass to
a quarantined environment for signature, verify it, and then use QR codes
to extract it from the quarantined environment to pass on to additional
quarantined environments (of the other signatories) for additional signatures
and eventually extract it for execution.

For brevity purposes, we will use Bitcoin and Electrum as an example, but
this should be easily replicable on Litecoin and Electrum-LTC or Bitcoin
Cash and ElectronCash.

## Building the Transaction
On any Internet-connected computer, set-up the **Watch-Only Electrum Wallet**
(this setup can be re-used from previous transactions):
1. Download and install Electrum (see prior steps for information on where to
do it)
2. Open Electrum
3. Select `Auto connect` and click `Next`
4. If you wish name this wallet and click `Next`
5. Select `Multi-signature wallet` and click `Next`
6. Select your `M-of-N` policy. The top bar, `cosigners` is the `N` and the
lower bar, `Required signatures` is the `M`. Click `Next`.
7. Select `Use a master key` and click `Next`
8. Scan your <span class="warning">Bitcoin Master Public Key QR Code</span>
9. Select `Enter cosigner key` and click `Next`
10. Scan the rest of the <span class="warning">Bitcoin Master Public Key QR Codes</span>
11. Do not enter a password, just click `Next`
You should be able to see the balance in your <span class="warning">bitcoin cold storage address</span>
12. Click on `Send`, enter the destination address and the amount
13. Click on `Preview`
14. Click on the `QR Code` icon
15. Print the QR Code. This is the transaction that will need to be signed by
the Quarantined computers of M signatories.

## Signing the transaction

The following steps will need to be done by M signatories:

1. Gather required information
    1. Make sure you have your <span class="danger">Cold Storage Information Packets</span>
    on hand (you'll need the <span class="danger">24-word BIP39 Mnemonic</span>).
        1. You will also need to coordinate with M-1 signatories who will in
        turn need their <span class="danger">Cold Storage Information Packets</span>.
    2. You should print the <span class="warning">QR Code</span> of the transaction
    to be signed.
2. Execute [Section VI of the Setup Protocol](../setup/quarantined-workspace.md)
to prepare your quarantined workspace.
3. Sign the transaction

   **On any of your Quarantined computers:**
    1. Import QR code data
        1. Start Electrum
            ```
            $ ~/apps/electrum-3.3.6-x86_64.AppImage
            ```
        2. Load the wallet and your key
            1. Choose `auto connect` and click `Next`.
            2. Choose whatever name for the wallet and click `Next`
            3. Select `Multi-signature wallet`
            4. Select your `M-of-N` policy. The top bar, `cosigners` is the `N`
            and the lower bar, `Required signatures` is the `M`. Click `Next`.
            5. Select `I already have a seed` and click `Next`
            6. Click on `Options`, select `BIP39 seed` and click `OK`.
            7. Enter your <span class="danger">BIP39 seed phrase</span> and click
            `Next`.
            8. Leave the default settings selected and click `Next`.
            9. Click `Next`
            10. Select `Enter cosigner key`
            11. Use the QR Code reader to read the next signatories'
            <span class="warning">Bitcoin Master Public Key QR Code</span>
            12. Repeat steps 9 to 11 for the other N-2 signatories
            13. Do not enter a password and click `Next`
        3. Sign the Transaction
            1. From the top bar menu, select `Tools` -> `Load Transaction` ->
            `From QR Code`
            2. Scan the printed QR Code of the transaction that needs signing
            3. Verify that the outputs of the transaction make sense
                1. You should see one output for the desired amount and
                destination.
                2. You will likely see a second output going to a change
                address belonging to the same wallet. You can verify that the
                change addresses belong to the wallet in the `Addresses` tab
            4. Click on `Sign`
            5. You should see the `Status` of the transaction, indicating how
            many signatories have signed
4. Visually hide all critically sensitive data.

    We'll be using a smartphone with a live Internet connection to read QR
    codes from the quarantined computer screens. Any malware (or a malicious
    QR reader app) could steal sensitive data if it is not visually hidden.

    **<span style="color: red;">This step is important. Failing to execute it properly creates a
    substantial security risk.</span>**

    1. Put your <span class="danger">Cold Storage Information Packets</span>
    out of sight -- this prevents a smartphone camera from accidentally seeing
    them.
    2. Make sure your <span class="danger">BIP39 Mnemonic</span> is nowhere
    to be seen in your Computer screen or in the physical world.
6. Extract the signed transaction from the quarantined environment.
    1. Remove a smartphone from the Faraday bag and turn it on.
    2. Open your QR Reader App
    3. **On the Quarantined computer**, display the signed transaction QR code
    by clicking the `QR Icon` on the bottom left of the screen.
    4. Use the smartphone's QR code reader to read the QR code.
    5. Take a picture of the QR code using the smartphone.
    6. Send both the text version and the QR Code's picture to the next
    signatory using a messaging app which the signatory will be able to access
    from a laptop. If you are the last signatory, send the contents to yourself
        
7. Shut down **all** quarantined computers entirely. As a precaution against
side channel attacks, the quarantined computers should not be active except
when they absolutely need to be.
    ```
    $ sudo shutdown now
    ```
    The recommended Acer laptop may require you to hold down the power button
    for several seconds to complete the shutdown.
8. Repeat the steps above until M signatories have signed the transaction
    1. The status of Electrum should change to `Signed` once all required
    signatories have signed the transaction

## Verifying and broadcasting the transaction

On any Internet-connected computer, the last signatory should:

1. Access the QR Code of the fully signed transaction she previously sent
herself.
2. Open the watch-only Bitcoin Electrum Wallet
3. Load the transaction
    1. Click on `Tools` -> `Load Transaction` -> `From QR Code`
    2. Scan the QR Code of the fully signed transaction
4. Under "Outputs"
    1. **<span style="color: red;">Verify the destination address is correct.</span>**
    2. Verify the amount going to the destination address is correct.
    3. If you did *not* withdraw all funds from these unspent transactions,
    you'll also see a second output which "sends" the remainder of the
    funds "back" to your <span class="warning">cold storage address</span>.
    This is necessary; it's how Bitcoin is designed to operate.
5. Execute the transaction.
    1. Click on `Broadcast`
    2. You should see a `Payment sent` pop up with the <span class="warning">Transaction ID</span>
    3. Copy-paste the <span class="warning">Transaction ID</span>
4. Verify the withdrawal on the public blockchain.
    1. Go to [blockchair](https://www.blockchair.com/), paste
    the <span class="warning">Transaction ID</span> into the search bar,
    and press Enter.
    2. Within a couple of minutes (and often much faster), you should be able to
    refresh this page and see your transaction listed as "Unconfirmed".
    3. Periodically refresh the page until you see the funds moved from
    "Unconfirmed" to be reflected in "Balance". This generally happens within
    15 minutes; if the Bitcoin network is unusually congested, it may take
    longer.
    4. You should be able to verify this in the Watch-Only Electrum wallet as
    well
