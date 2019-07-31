---
title: Withdrawing XRP
description: Learn how to withdraw funds using CryptoGlacier,
  the step-by-step, secure, multi-blockchain, multi-signature,
  cold storage protocol for long-term storage of crypto assets
  based on the popular Glacier Protocol
---

In this section, we construct a "signed transaction" in our quarantined
environments, verify it, and then use QR codes to extract it from the
quarantined environment to pass on to additional quarantied environments
for additional signatures and eventually extract it for execution.

# Gather the required information
On any Internet-connected computer:

1. Find your current account's Nonce
    1. Navigate to [etherscan.io](https://etherscan.io) and enter your <span class="warning">Ethereum Public Address</span>
    Also known as **MESSAGE E** on your <span class="warning">Cold Storage Information Packet</span>
    2. Find your last outgoing transaction and click on it, find the `Nonce` value
    and record it. If there are no outgoing transactions, then record the number `0`.
2. TODO: make a QR code with the destination address and the amount that you
wish to withdraw

# Create and sign your transaction

The following steps will need to be done by M signatories:

1. Gather required information
    1. Make sure you have your <span class="danger">Cold Storage Information Packets</span>
    on hand (you'll need the <span class="danger">24-word BIP39 Mnemonic</span>).
        1. You will also need to coordinate with M-1 signatories who will in
        turn need their <span class="danger">Cold Storage Information Packets</span>.
    2. You should print the <span class="warning">QR Code</span> of the destination
    address and amount.
2. Execute [Section VI of the Setup Protocol](../setup/quarantined-workspace.md)
to prepare your quarantined workspace.
3. Create and sign the transaction

   **On the Q1 computer:**
    1. Import all required data
        1. Start the  QR code reader:
        ```
        $ zbarcam
        ```
        A window will appear with your laptop's video feed.
        2. Scan the <span class="warning">Ethereum Cold Wallet Address</span>
        from your <span class="warning">Cold Storage Information Packet</span>.
            1. Hold the QR code up to the webcam
            2. When a green square appears around the QR code on the video feed,
            it has been successfully read.
            3. Verify the decoded QR code is shown in the terminal window. Example:
                <pre>   
                QR-Code:<span class="warning" style="white-space: pre-wrap;">0xe46295248fab5f8749af13eeea7021aec098c4ba</span></pre>
            4. Copy-paste the data into the Quarantined Scratchpad under a
            "WALLET ADDRESS" header
        3. Repeat the step above for the destination address and amount QR code
        with an appropriate header in the Quarantined Scratchpad
    2. Create your ETH account keystore file
        1. Execute the cryptoglacier script
        ```
        $ node ~/cryptoglacier/setup.js --ether
        ```
        2. You will be prompted to enter your <span class="danger">24-word BIP39 Mnemonic</span>
        3. The script will write an `ethereum.json` file to your `~/cryptoglacier` directory
    3. Import your keystore file into multisigweb
        1. Start multisigweb
        ```
        $ multisigweb
        ```
        2. Accept the TOS and Privacy Policy
        3. Select `Light Wallet`
        4. Click on `Accounts` tab
        5. Click on `Import`
        6. Select `Browse` and select the `ethereum.json` file in the
        `cryptoglacier` directory
        7. Enter `cryptoglacier` as your password
        8. Name the account as you wish
        9. Import Account
    4. Import your Wallet Contract into multisigweb
        1. Click on `Wallets` tab
        2. Click on `Add`
        3. Select `Restore deployed wallet` and click `Next`
        4. Enter any name you wish and then copy the <span class="warning">Ethereum Cold Wallet Address</span>
        from your Quarantined Scratchpad and click `Ok`
    5. Create the transaction
        1. Click on the Name of the Wallet
        2. Click on `Add`
        3. Enter the `Destination` and the `Amount` and click `Sign offline`
        4. Enter the Nonce you previously recorded and click `Ok`
        5. Enter `cryptoglacier` as the password and click `Ok`
        6. You will receive the hex code. Select it and click `Copy`
    6. Build the QR Code for the transaction
        ```
        $ qrencode -o tx.png [PASTE USING CTRL+SHIFT+V]
        ```
    7. Display the QR Code
        ```
        $ eog tx.png
        ```
4. Visually hide all critically sensitive data.

    We'll be using a smartphone with a live Internet connection to read QR
    codes from the quarantined computer screens. Any malware (or a malicious
    QR reader app) could steal sensitive data if it is not visually hidden.

    **<span style="color: red;">This step is important. Failing to execute it properly creates a
    substantial security risk.</span>**

    1. Put your <span class="danger">Cold Storage Information Packets</span>
    out of sight -- this prevents a smartphone camera from accidentally seeing
    them.
5. Extract the signed transaction from the quarantined environment.
    1. QR reader setup
        1. Remove a smartphone from the Faraday bag and turn it on.
        2. If the smartphone doesn't already have a QR code reader on it,
        install one.

           Any reader is fine as long as it can read all types of QR
        codes, but here are recommendations we've tested with this protocol:
        [iOS](https://itunes.apple.com/us/app/qr-reader-for-iphone/id368494609?mt=8),
        [Android](https://play.google.com/store/apps/details?id=com.application_4u.qrcode.barcode.scanner.reader.flashlight&hl=en).
    2. Transfer the signed transaction data to a non-quarantined computer.
        1. Use the smartphone's QR code reader to read the QR code.
        2. Take a picture of the <span class="warning">QR code</span> using the
        smartphone and send it to yourself using a messaging app which you can
        access from a laptop.
        
6. Shut down **both** quarantined computers entirely. As a precaution against
side channel attacks, the quarantined computers should not be active except
when they absolutely need to be.
    ```
    $ sudo shutdown now
    ```
    The recommended Acer laptop may require you to hold down the power button
    for several seconds to complete the shutdown.

# Executing and verifying the transaction

On any Internet-connected computer:

1. Open [MyEtherWallet](https://alpha.myetherwallet.com/pushTx)
Access the <span class="warning">QR Code of the fully signed transaction</span> you sent
yourself from your smartphone previously.
2. Open up the watching-only Bitcoin Electrum Wallet
3. Load the transaction
    1. Click on `Tools` -> `Load Transaction` -> `From QR Code`
    2. Scan the <span class="warning">QR Code of the fully signed transaction</span>
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
    2. Copy-paste the <span class="warning">Transaction ID</span>
4. Verify the withdrawal on the public blockchain.
    1. Go to [blockchair](https://www.blockchair.com/) , paste
    the <span class="warning">Transaction ID</span> into the search bar,
    and press Enter.
    2. Within a couple of minutes (and often much faster), you should be able to
    refresh this page and see your transaction listed as "Unconfirmed".
    3. Periodically refresh the page until you see the funds moved from
    "Unconfirmed" to be reflected in "Balance". This generally happens within
    15 minutes; if the Bitcoin network is unusually congested, it may take
    longer.
