---
title: Withdrawing XRP
description: Learn how to withdraw funds using CryptoGlacier,
  the step-by-step, secure, multi-blockchain, multi-signature,
  cold storage protocol for long-term storage of crypto assets
  based on the popular Glacier Protocol
---

In this section, we construct a "signed transaction" in our quarantined
environments, verify it, and then use QR codes to extract it from the
quarantined environment to pass on to additional quarantined environments
for additional signatures and eventually extract it for execution.

This protocol requires one signatory to **Create a transaction** and then M-1
signatories to **Sign a transaction**.

## Gather the required information

1. Make sure you have your <span class="danger">Cold Storage Information Packets</span>
on hand (you'll need the <span class="danger">24-word BIP39 Mnemonic</span>).
    1. You will also need to coordinate with M-1 signatories who will in
    turn need their <span class="danger">Cold Storage Information Packets</span>.
2. If you are the first signatory and will **Create a transaction**, then on
any Internet-connected computer:
    1. Find your address' sequence number
        1. Navigate to [https://xrpl.org/xrp-ledger-rpc-tool.html](https://xrpl.org/xrp-ledger-rpc-tool.html),
        enter your <span class="warning">Ripple Cold Storage Address</span> and
        click `Get info`.
        2. On the `Result` section, expand the `account_data` information and record
        the `Sequence` number on a piece of paper
    2. On the same piece of paper carefully write down the amount of XRP that
    you are withdrawing.
    3. Create and print the QR codes with the <span class="warning">Ripple Cold Storage Address</span> and the destination address
        1. Install the required software (on a Mac, only required the first time). On terminal:
        ```
        $ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
        $ brew install qrencode
        ```
        2. Create the QR Code for the <span class="warning">Ripple Cold Storage Address</span>
        ```
        $ qrencode -s 5 -o source.png <PASTE_RIPPLE_COLD_STORAGE_ADDRESS>
        ```
        3. Open the QR Code and paste it in a word-editing doc under the header "SOURCE"
        ```
        $ open source.png
        ```
        4. Create the QR Code for the destination address
        ```
        $ qrencode -s 5 -o destination.png <PASTE_DESTINATION_ADDRESS>
        ```
        5. Open the QR Code and paste it in a word-editing doc under the header "DESTINATION"
        ```
        $ open destination.png
        ```
        6. Print the word editing doc
    4. If the transfer requires a Destination Tag, please write it down
    carefully on the piece of paper

4. If you are a signatory that will **Sign a transaction**, please make
sure you write down on a piece of paper
    1. The Destination Address
    2. The Destination TAG
    3. The Transaction amount

## Create a new Transaction

Only one signatory needs to create a new transaction. If another signatory has
already created a transaction and you need to sign over it, see section below on
Sign a Transaction

Again, the following steps will need to be done by 1 signatories:

1. Execute [Section VI of the Setup Protocol](../setup/quarantined-workspace.md)
to prepare your quarantined workspace.
2. Create and sign the transaction

   **On the Q1 computer:**
    1. Import required data
        1. Start zbarcam
        ```
        $ zbarcam
        ```
        A window will appear with your laptop's video feed.
        2. Scan the destination address QR code
            1. Hold the QR code up to the webcam
            2. When a green square appears around the QR code on the video feed,
            it has been successfully read.
            3. Verify the decoded QR code is shown in the terminal window. Example:
                <pre>   
                QR-Code:<span class="warning" style="white-space: pre-wrap;">r8HgVGenRTAiNSM5iqt9PX2D2EczFZhZr</span></pre>
            4. Copy-paste the data into the Quarantined Scratchpad under a
            "DESTINATION ADDRESS" header
    2. Create Transaction
        1. Execute the cryptoglacier script
        ```
        $ cd ~/cryptoglacier/
        $ node setup.js --xrp
        ```
        2. You will be prompted to enter your <span class="danger">24-word BIP39 Mnemonic</span>
        3. The script will ask you a few questions and write a `ripple_tx.png`
        file to your `~/cryptoglacier` directory
    3. Display the QR Code
        ```
        $ eog ripple_tx.png
        ```
3. Visually hide all critically sensitive data.

    We'll be using a smartphone with a live Internet connection to read QR
    codes from the quarantined computer screens. Any malware (or a malicious
    QR reader app) could steal sensitive data if it is not visually hidden.

    **<span style="color: red;">This step is important. Failing to execute it properly creates a
    substantial security risk.</span>**

    1. Put your <span class="danger">Cold Storage Information Packets</span>
    out of sight -- this prevents a smartphone camera from accidentally seeing
    them.
4. Extract the signed transaction from the quarantined environment.
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
        2. Visually inspect that the json is the same
        3. Take a picture of the QR code and send it to the next signatory
        using a messaging app which they can access from a laptop.
5. Shut down the quarantined computer entirely. As a precaution against
side channel attacks, the quarantined computers should not be active except
when they absolutely need to be.
    ```
    $ sudo shutdown now
    ```
    The recommended Acer laptop may require you to hold down the power button
    for several seconds to complete the shutdown.



## Sign a Transaction

M-1 signatories need to sign the transaction.

If you are a signatory and are looking to sign a transfer:

1. Execute [Section VI of the Setup Protocol](../setup/quarantined-workspace.md)
to prepare your quarantined workspace.
2. Sign the confirmation transaction

   **On the Q1 computer:**
    1. Import required data
        1. Start zbarcam
        ```
        $ zbarcam
        ```
        A window will appear with your laptop's video feed.
        2. Scan the QR code you received from the prior signatory
            1. Hold the QR code up to the webcam
            2. When a green square appears around the QR code on the video feed,
            it has been successfully read.
            3. Verify the decoded QR code is shown in the terminal window. Example:
                <pre>
                QR-Code:<span class="warning" style="white-space: pre-wrap;">{"Account":"rp3rEms99VB7uMyU8GnGyPmo6uejJ4XbEV","Destination":"rp3rEms99VB7uMyU8GnGyPmo6uejJ4XbEV","DestinationTag":5,"Amount":"600000000","Sequence":40,"TransactionType":"Payment","Fee":"100","SigningPubKey":"","Signers":[{"Signer":{"Account":"rp3rEms99VB7uMyU8GnGyPmo6uejJ4XbEV","SigningPubKey":"0368C9DEE202196D3FFEA2A81F7BBAE8673775F54B286379F8E7C3AB31B53B4666","TxnSignature":"304502FB6C45A46912E522100E346752EF9E816D55F63F3F7FC010D80CFD1B0CEFD2672ACD7D562B575125094E602200B6243B4575D044984A10020A9B26BDE2347E7AB8B7E076"}}]}</span></pre>
            4. Copy-paste the data into the Quarantined Scratchpad under a
            "TX TO SIGN" header
            5. Inspect the transaction and make sure the following details are
            correct:
            * **Destination Tag**
            * **Destination Address**
            * **Amount**
    1. Execute the cryptoglacier script
        ```
        $ cd ~/cryptoglacier/
        $ node setup.js --xrp
        ```
        2. You will be prompted to enter your <span class="danger">24-word BIP39 Mnemonic</span>
        3. The script will ask you a few questions, including to paste the
        "TX TO SIGN" and the script will write a new `ripple_tx.png` file to
        your `~/cryptoglacier` directory
    3. Display the QR Code
        ```
        $ eog ripple_tx.png
        ```
3. Visually hide all critically sensitive data.

    We'll be using a smartphone with a live Internet connection to read QR
    codes from the quarantined computer screens. Any malware (or a malicious
    QR reader app) could steal sensitive data if it is not visually hidden.

    **<span style="color: red;">This step is important. Failing to execute it properly creates a
    substantial security risk.</span>**

    1. Put your <span class="danger">Cold Storage Information Packets</span>
    out of sight -- this prevents a smartphone camera from accidentally seeing
    them.
4. Extract the signed transaction from the quarantined environment.
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
        2. Visually inspect that the json is the same
        3. Take a picture of the QR code and send it to the next signatory
        using a messaging app which they can access from a laptop. If you are
        the last signatory, send the json **contents** to yourself using a
        messaging app that you can access from a laptop.
5. Shut down the quarantined computer entirely. As a precaution against
side channel attacks, the quarantined computers should not be active except
when they absolutely need to be.
    ```
    $ sudo shutdown now
    ```
    The recommended Acer laptop may require you to hold down the power button
    for several seconds to complete the shutdown.


## Broadcasting the transactions

On any Internet-connected computer:

1. Send the Transaction
    1. Access the final JSON of the fully signed transaction you sent yourself
    from your smartphone previously.
    2. Open [xrpl.org/websocket-api-tool.html](https://xrpl.org/websocket-api-tool.html)
    and paste the json string in the `Request` box
    3. Click on `Send request`
2. Verify the transaction
    1. You can check the result of your transaction by visiting
    [bithomp](https://bithomp.com/explorer/)
