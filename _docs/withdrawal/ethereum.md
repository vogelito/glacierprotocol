---
title: Withdrawing Ethereum & ERC20 Tokens
description: Learn how to withdraw funds using CryptoGlacier,
  the step-by-step, secure, multi-blockchain, multi-signature,
  cold storage protocol for long-term storage of crypto assets
  based on the popular Glacier Protocol
---

In this section, we construct a "signed transaction" in our quarantined
environments, verify it, and then use QR codes to extract it from the
quarantined environment to pass on to additional quarantined environments
for additional signatures and eventually extract it for execution.

This protocol is divided into two sub-protocols: Proposing Transfers and
Confirming Transfers. The flow is one signatory will propose and the rest will
confirm.

## Gather the required information

Every signatory needs to execute this section

1. Make sure you have your <span class="danger">Cold Storage Information Packets</span>
on hand (you'll need the <span class="danger">24-word BIP39 Mnemonic</span>).
    1. You will also need to coordinate with M-1 signatories who will in
    turn need their <span class="danger">Cold Storage Information Packets</span>.

On any Internet-connected computer:

1. Find your current account's Nonce
    1. Navigate to [etherscan.io](https://etherscan.io) and enter your <span class="warning">Ethereum Public Address</span>,
    also known as **MESSAGE E** on your <span class="warning">Cold Storage Information Packet</span>.
    2. Find your last outgoing transaction and click on it, find the `Nonce` value
    and write it down on a piece of paper. If there are no outgoing transactions,
    then record the number `0`.
2. Navigate to [ethgasstation.info](https://ethgasstation.info) and record the
recommended gas price in Gwei on the same piece of paper
3. If you are **Proposing A Transfer**:
    1. Install the required software (on a Mac, only required the first time):
    ```
    $ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
    $ brew install qrencode
    ```
    2. Create and print QR code with the destination address
        1. On terminal
        ```
        $ qrencode -s 5 -o destination.png <ENTER_DESTINATION_ADDRESS>
        ```
        2. Open the QR Code:
        ```
        $ open destination.png
        ```
        3. Print the QR Code
    3. If you are withdrawing from an ERC20 Token, make sure you repeat the step
    above for the ERC20 Token Contract Address. You can find the ERC20 Contract
    Address on etherscan.io **Make sure you also note the Contract Decimals
    (usually 18)** in the piece of paper.
    4. On the same piece of paper carefully write down the amount of ETH or ERC20
    Tokens that you are withdrawing.
4. If you are **Confirming a Transfer**:
    1. Obtain the Transfer ID:
        1. Open multisigweb on an internet connected device
        2. Import the <span class="warning">Ethereum Cold Wallet Address</span>.
        3. Open the Wallet and navigate to the `Multisig Transactions` section
        4. Verify the details (amount + destination) of the Transfer you are
        looking to confirm and write down on the piece of paper the ID (left-most
        column)
5. Finally, remember that each signatory's Ethereum account will be making
transactions on the blockchain, so make sure each account has some ETH balance.

## Proposing Transfers

Only one signatory needs to propose transfers. If a signatory has already
proposed a transfer and you need to confirm it, see section below on
Confirming Transfers

Again, the following steps will need to be done by 1 signatories:

1. Execute [Section VI of the Setup Protocol](../setup/quarantined-workspace.md)
to prepare your quarantined workspace.
2. Create and sign the transaction

   **On the Q1 computer:**
    1. Create your ETH account keystore file
        1. Execute the cryptoglacier script
        ```
        $ node ~/cryptoglacier/setup.js --ether
        ```
        2. You will be prompted to enter your <span class="danger">24-word BIP39 Mnemonic</span>
        3. The script will write an `ethereum.json` file to your `~/cryptoglacier` directory
    2. Set the gas price on multisigweb
        1. Start multisigweb
        ```
        $ multisigweb
        ```
        2. Accept the TOS and Privacy Policy
        3. Select `Light Wallet`
        4. Click on `Settings` tab
        5. Enter the gas price in Wei (multiply by 10^9)
        6. Under `Wallet factory contract` select `Custom contract`
        7. Click `Update settings`
        9. Exit the program (Upper left Menu, Application -> Quit)
    3. Import your keystore file into multisigweb
        1. Start multisigweb
        ```
        $ multisigweb
        ```
        2. Click on `Accounts` tab
        3. Click on `Import`
        4. Select `Browse` and select the `ethereum.json` file in the
        `cryptoglacier` directory
        5. Enter `cryptoglacier` as your password
        6. Name the account as you wish
        7. Import Account
    4. Import required data
        1. Start the  QR code reader
            1. On Terminal, open a new tab with `Ctrl+Shift+T`
            2. Start zbarcam
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
            "CONTRACT ADDRESS" header
        3. Repeat the step above for the destination address QR code
        with a "DESTINATION ADDRESS" header in the Quarantined Scratchpad
        4. If you are withdrawing an ERC20 Token, repeat the step above for the
        ERC20 Token Contract Address QR code with a "TOKEN ADDRESS" header in
        the Quarantined Scratchpad
    5. Import your Wallet Contract into multisigweb
        1. Click on `Wallets` tab
        2. Click on `Add`
        3. Select `Restore deployed wallet` and click `Next`
        4. Enter any name you wish and then copy the <span class="warning">Ethereum Cold Wallet Address</span>
        from your Quarantined Scratchpad and click `Ok`
    6. Create the transaction
        1. Click on the Name of the Wallet
        2. For ETH Transactions
            1. Click on `Add` next to `Execute offline`
            2. Enter the `Destination` (from the Scratchpad) and the `Amount`
            (from the piece of paper) and click `Sign offline`
        3. For ERC20 Transactions
            1. Click the `Add` button in the `Tokens` section
            2. Enter the "TOKEN ADDRESS" in the `Address` field
            3. Enter any `Symbol`
            4. Enter the `Decimals` from the piece of paper and click `Ok`
            5. Scroll through the `Tokens` until you find the `Symbol` you just
            added. Click `Withdraw`
            2. Enter the `Amount` (from the piece of paper) and the
            `Destination` (from the Scratchpad) and click `Sign offline`
        4. Enter the `Nonce` you recorded on the piece of paper and click `Ok`
        5. Enter `cryptoglacier` as the password and click `Ok`
        6. You will receive the hex code. Select it and click `Copy`
    7. Build the QR Code for the transaction
        ```
        $ qrencode -o tx.png [PASTE USING CTRL+SHIFT+V]
        ```
    8. Display the QR Code
        ```
        $ eog tx.png
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
        2. Visually inspect that the hex code is the same and send it to
        yourself using a messaging app which you can access from a laptop.
5. Shut down the quarantined computer entirely. As a precaution against
side channel attacks, the quarantined computers should not be active except
when they absolutely need to be.
    ```
    $ sudo shutdown now
    ```
    The recommended Acer laptop may require you to hold down the power button
    for several seconds to complete the shutdown.

6. Skip to the section "Broadcasting and verifying transactions" below

## Confirming Transfers

M-1 signatories need to confirm transfers. Only Transfers that have been
proposed can be confirmed.

If you are a signatory and are looking to confirm a transfer:

1. Execute [Section VI of the Setup Protocol](../setup/quarantined-workspace.md)
to prepare your quarantined workspace.
2. Sign the confirmation transaction

   **On the Q1 computer:**
    1. Create your ETH account keystore file
        1. Execute the cryptoglacier script
        ```
        $ node ~/cryptoglacier/setup.js --ether
        ```
        2. You will be prompted to enter your <span class="danger">24-word BIP39 Mnemonic</span>
        3. The script will write an `ethereum.json` file to your `~/cryptoglacier` directory
    2. Set the gas price on multisigweb
        1. Start multisigweb
        ```
        $ multisigweb
        ```
        2. Accept the TOS and Privacy Policy
        3. Select `Light Wallet`
        4. Click on `Settings` tab
        5. Enter the gas price in Wei (multiply by 10^9)
        6. Under `Wallet factory contract` select `Custom contract`
        7. Click `Update settings`
        9. Exit the program (Upper left Menu, Application -> Quit)
    3. Import your keystore file into multisigweb
        1. Start multisigweb
        ```
        $ multisigweb
        ```
        2. Click on `Accounts` tab
        3. Click on `Import`
        4. Select `Browse` and select the `ethereum.json` file in the
        `cryptoglacier` directory
        5. Enter `cryptoglacier` as your password
        6. Name the account as you wish
        7. Import Account
    4. Import required data
        1. Start the  QR code reader
            1. On Terminal, open a new tab with `Ctrl+Shift+T`
            2. Start zbarcam
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
            "CONTRACT ADDRESS" header
    5. Import your Wallet Contract into multisigweb
        1. Click on `Wallets` tab
        2. Click on `Add`
        3. Select `Restore deployed wallet` and click `Next`
        4. Enter any name you wish and then copy the <span class="warning">Ethereum Cold Wallet Address</span>
        from your Quarantined Scratchpad and click `Ok`
    6. Confirm the transaction
        1. Click on the Name of the Wallet
        2. Click `Confirm offline`
        3. Enter the `Transaction ID` as written on the piece of paper and click
        `Confirm offline`
        4. Enter the `Nonce` you recorded on the piece of paper and click `Ok`
        5. Enter `cryptoglacier` as the password and click `Ok`
        6. You will receive the hex code. Select it and click `Copy`
    7. Build the QR Code for the transaction
        ```
        $ qrencode -o tx.png [PASTE USING CTRL+SHIFT+V]
        ```
    8. Display the QR Code
        ```
        $ eog tx.png
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
        2. Visually inspect that the hex code is the same and send it to
        yourself using a messaging app which you can access from a laptop.
        
5. Shut down the quarantined computer entirely. As a precaution against
side channel attacks, the quarantined computers should not be active except
when they absolutely need to be.
    ```
    $ sudo shutdown now
    ```
    The recommended Acer laptop may require you to hold down the power button
    for several seconds to complete the shutdown.

6. Follow the section "Broadcasting and verifying transactions" below

## Broadcasting and verifying transactions

On any Internet-connected computer:

1. Send the Transaction
    1. Access the <span class="warning">hex Code of the fully signed transaction</span>
    you sent yourself from your smartphone previously.
    2. Open [alpha.myetherwallet.com/pushTx](https://alpha.myetherwallet.com/pushTx)
    and paste the hex code in the `Signed Transaction` box
    3. Click on `Send Transaction`
    4. Confirm the contents of the transaction and click `Yes, I am sure! Make transaction.`
    5. Wait until the transaction gets into an ethereum block by checking
    [etherscan.io](https://etherscan.io)
2. Verify the transaction status by opening multisigweb on an internet connected
device and importing the <span class="warning">Ethereum Cold Wallet Address</span>
