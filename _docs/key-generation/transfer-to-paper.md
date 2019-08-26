---
title: Transfer cold storage data to paper
description: Learn how to transfer your cold storage data to paper using
  CryptoGlacier, the step-by-step, secure, multi-blockchain,
  multi-signature, cold storage protocol for long-term storage of
  crypto assets based on the popular Glacier Protocol
---

In this section, you'll move the cold storage data you generated in Section I
from the quarantined computing environments onto physical paper. This will be
done using a combination hand transcription and
[QR codes](https://en.wikipedia.org/wiki/QR_code).

Each signatory will need to do the following:

1. Transfer the <span class="danger">BIP39 Mnemonic</span> to paper.
    1. Write the <span class="danger">24-word BIP39 Mnemonic</span> on a piece
    of TerraSlate paper.
        1. Do **not** write anything else on the paper unless specifically
        instructed (such as "Bitcoin", "CryptoGlacier", "private key", etc.) In the
        event the key is seen by someone untrustworthy or stolen by a random
        thief, such clues help them understand the significance of the key and
        give them an incentive to plot further thefts or attacks.
        2. Transcribe **by hand**. Do not use QR codes or any other method to transfer.
        3. Seed phrases **are not** case-sensitive.
        4. **Write clearly**.
            1. Use care to distinguish between "l" (lower-case "L") and "I"
            (upper case "i")
            2. Use care to distinguish between "u" and "v"
            3. Use care to distinguish between "U" and "v"
    2. **Double-check that you transcribed all 24 words in the
    <span class="danger">BIP39 Mnemonic</span> correctly.** If you make a mistake,
    you'll have to redo a lot of work.
    3. Manually count that you have transcribed 24 words.
    4. Label each page with:
        1. Today's date
        2. Your initials
        3. The **version** of CryptoGlacier used (listed on the front page of this document)
        Do not write "CryptoGlacier", simply the version of CryptoGlacier used (e.g. `0.94.1`)
        4. Write down the chosen M-of-N configuration
2. Visually hide all critically sensitive data.

    We'll be using a smartphone with a live Internet connection to read QR
    codes from the quarantined computer screens. Any malware (or a malicious
    QR reader app) could steal sensitive data if it is not visually hidden.

    **<span style="color: red;">This step is important. Failing to execute it properly creates a substantial
    security risk.</span>**

    1. Put your <span class="danger">handwritten BIP39 Mnemonic</span> out of
    sight (don't just turn them face down; paper is not completely opaque).
    This prevents a smartphone camera from accidentally seeing them.
    2. Delete all text from the Quarantined Scratchpad on the **Q1 and Q2**
    computers.
    3. **On the Q1 computer Quarantined Scratchpad:**
        1. Copy-paste the following items from the node script's terminal
        window output:
        * <span class="warning">Bitcoin Master Public Key</span>
        * <span class="warning">Litecoin Master Public Key</span>
        * <span class="warning">Bitcoin Cash Master Public Key</span>
        * <span class="warning">Ethereum Address</span>
        * <span class="warning">Ripple Address</span>
        2. Double check that only the items above are included in the
        Scratchpad.
        3. No really, triple check that.
        4. Enable line wrapping so the entire contents can be seen.
            1. With the Quarantined Scratchpad window active, go to the menu
            bar at the top of the screen.
            2. Select Edit.
            3. Select Preferences.
            4. Select the View tab.
            5. Uncheck "Do not split words over two lines".
    4. **On the Q2 computer** close firefox.
    5. Clear the terminal windows on the **Q1 and Q2** computers.
       ```
       $ clear
       ```
3. QR reader setup
    1. Remove a smartphone from the Faraday bag and turn it on.
    2. If the smartphone doesn't already have a QR code reader on it, install one.

    Any reader is fine as long as it can read all types of QR codes, but
    here are recommendations we've tested with Glacier:
    [iOS](https://itunes.apple.com/us/app/qr-reader-for-iphone/id368494609?mt=8),
    [Android](https://play.google.com/store/apps/details?id=com.application_4u.qrcode.barcode.scanner.reader.flashlight&hl=en).

4. Transfer the <span class="warning">Bitcoin Master Public Key</span> to a
non-quarantined computer.
    1. **On the Q1 computer**, display the
    <span class="warning">Bitcoin Master Public Key</span> as a
    <span class="warning">QR code</span> on the screen:
       ```
       $ cd ~/cryptoglacier
       $ eog bitcoin_master_public_key.png
       ```
    2. Use the smartphone's QR code reader to read the <span class="warning">QR
    code</span>. When the <span class="warning">QR code</span> is
    successfully read, the smartphone should display the text version of the
    <span class="warning">Bitcoin Master Public Key</span>.
    3. Verify the <span class="warning">Bitcoin Master Public Key</span> address on the
    smartphone matches the <span class="warning">Bitcoin Master Public Key</span> in the Quarantined Scratchpad.

        **If it does not match, do not proceed**. Try using a different QR reader application or restarting the Deposit Protocol. Seek
        assistance if discrepancies persist.

    4. Use the smartphone to send the
    <span class="warning">Bitcoin Master Public Key</span> to yourself using a
    messaging app which you'll be able to access from a laptop (e.g. Whatsapp, Slack, etc..).
    When sending the message, add **"B"** as an **identifier** to the message. This is an indication
    that the <span class="warning">Public Key</span> belongs to Bitcoin.
    (E-mail is not recommended for security reasons.)
    5. Take a picture of the QR Code
    6. Use the smartphone to send the
    <span class="warning">QR Code</span> picture to yourself using a
    messaging app which you'll be able to access from a laptop. Also use the **identifier "B"**.
    (E-mail is not recommended for security reasons.)
    7. Close the program displaying the QR code (click on the top left `x`)

5. Repeat the previous step for the following:
* <span class="warning">Litecoin Master Public Key</span>, stored in
"litecoin_master_public_key.png", with **identifier "L"**.
* <span class="warning">Bitcoin Cash Master Public Key</span>, stored in
"bitcoin_cash_master_public_key.png", with **identifier "BC"**.
* <span class="warning">Ethereum Address</span>, stored in
"ethereum_address.png", with **identifier "E"**.
* <span class="warning">Ripple Address</span>, stored in "ripple_address.png",
with **identifier "X"**

6. Power down the smartphone and return it to the Faraday bag.
7. Shut down **both** quarantined computers entirely. As a precaution against
side channel attacks, the quarantined computers should not be active except
when they absolutely need to be.
    ```
    $ sudo shutdown now
    ```
    The recommended Acer laptop may require you to hold down the power button for
    several seconds to complete the shutdown.
8. Create your <span class="warning">Signatory Information Packet</span>.

   **Using your setup (Internet-connected) computer:**
    1. Access the material you sent yourself from your smartphone previously.
    In total you should have 10 pieces of information:
    * <span class="warning">Bitcoin Master Public Key</span> (message "B")
    * <span class="warning">Bitcoin Master Public Key QR Code</span> (message "B")
    * <span class="warning">Litecoin Master Public Key</span> (message "L")
    * <span class="warning">Litecoin Master Public Key QR Code</span> (message "L")
    * <span class="warning">Bitcoin Cash Master Public Key</span> (message "BC")
    * <span class="warning">Bitcoin Cash Master Public Key QR Code</span> (message "BC")
    * <span class="warning">Ethereum Address</span> (message "E")
    * <span class="warning">Ethereum Address QR Code</span> (message "E")
    * <span class="warning">Ripple Address</span> (message "X")
    * <span class="warning">Ripple Address QR Code</span> (message "X")
    2. Open an empty document in any word processing application (Word, Pages, etc...) This will be used
    to create the <span class="warning">Signatory Information Packet</span>.
    3. Put the following information into the document:
        1. Paste each message code followed by its corresponding QR-code and
        clear-text version
        2. On the header:
        * Type today's date
        * Your initials
        * Type the version of CryptoGlacier used (listed on the first page of this document)
        * Write down the chosen M-of-N configuration
    4. Do **not** put anything else in the document (such as "Bitcoin",
        "CryptoGlacier", "private key", etc.)
    5. Print a copy of the
        <span class="warning">Signatory Information Packet</span>.
    6. Share the contents of the <span class="warning">Signatory Information Packet</span>:
        1. Save the document as a <span class="warning">PDF</span>.
        2. GPG encrypt the <span class="warning">PDF file</span> using your keys
        and the keys of every other signatory (TODO: expand this).
        3. Electronically send the gpg-encrypted file to the other signatories
        4. You can also save an electronic copy of the <span class="warning">PDF</span>
        in a "conventionally secure" location of your choosing. Most password
        managers include a way to securely store files. Because the
        <span class="warning">Signatory Information Packet</span> contains
        moderately-sensitive data, there are some privacy considerations with
        keeping an electronic copy of it. See the Sensitive Data subsection for
        details.
        5. Delete the unencrypted <span class="warning">PDF</span> from your
        computer
    8. Shut down the computer. (It has a camera, and you will be working with
        critically sensitive data in a moment.)
9. Prepare the *temporary* version of your <span class="danger">Cold Storage Information Packet</span>:
    1. Put the <span class="danger">handwritten BIP39 Mnemonic page</span> along
    with one <span class="warning">Signatory Information Packet</span> in its own
    opaque envelope. While this obviously won't deter a determined
    thief, it makes it quite difficult for a thief to steal a key without leaving
    evidence they have done so -- and noticing theft of a single key gives you a
    chance to move your funds away before the thief can steal a second key.
    2. Your <span class="danger">Cold Storage Information Packet</span> is incomplete
    because you still need to go through the Multisig Account Creation Protocol
    3. Once complete, each set of pages will be referred to as a
    <span class="danger">Cold Storage Information Packet</span>.
10. Immediate storage of <span class="danger">Cold Storage Information Packet</span>:
    1. While the other signatories finish the Key Generation Protocol, we need
    to temporarily store the <span class="danger">Cold Storage Information Packet</span>
    2. Double-check to make sure the envelope contains a <span class="danger">handwritten BIP39 Mnemonic page</span>
    and your <span class="warning">Signatory Information Packet</span>.
    3. Seal the envelope
    4. Use tamper-resistant seals in addition to the envelope's normal
    adhesive to seal it.
    5. **Immediately** put the <span class="danger">Cold Storage Information Packet</span>
    in the safest possible location in your home or office that is immediately accessible.
    6. No, really. Like right now. That's basically one of the keys to a huge pile of
    cash you have just sitting there in envelopes on your desk.
11. Hardware storage
    1. Put tamper-resistant seals on the ends of all USB drives.
    2. Close the quarantined laptops, and seal the screen shut with a
    tamper-resistant seal.
    3. Store the hardware somewhere where it is unlikely to be used by accident.
12. It's crucial that only a small amount of time goes by (e.g. a few days)
    between the execution of the Key Generation Protocol and the Multisig
    Account Creation Protocol. Each of the signatory's
    <span class="danger">Cold Storage Information Packet</span> will go into
    long-term storage after the Multisig Account Creation Protocol is executed.
