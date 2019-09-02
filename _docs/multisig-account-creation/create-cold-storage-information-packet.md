---
title: Create Cold Storage Information Packet
description: Learn how to create your cold storage information page with
  CryptoGlacier, the step-by-step, secure, multi-blockchain, multi-signature,
  cold storage protocol for long-term storage of crypto assets
  based on the popular Glacier Protocol
---

**Only one signatory needs to execute this section.** You should agree with the
other signatories who will be responsible for creating the <span class="warning">Cold Storage Information Packet</span>.

In this section you will create a <span class="warning">Cold Storage Information Packet</span>
which will replace the **N** <span class="warning">Signatory Information Packets</span>.

1. Open an empty document in any word processing application
2. Put the following information into the document:
    1. On the header:
        * Type today’s date
        * Type the version of CryptoGlacier used (listed on the first page of this document)
        * Write down the chosen M-of-N configuration
    2. In the body of the document, write the following information. Pay
    attention to the order:
        1. **MESSAGE B**
            1. Insert the <span class="warning">Bitcoin Master Public Key QR Code</span>
            2. Insert the <span class="warning">Bitcoin Cold Storage Address</span>
        for all **N** signatories
        2. **MESSAGE L**
            1. Insert the <span class="warning">Litecoin Master Public Key QR Code</span>
            for all **N** signatories
            2. Insert the <span class="warning">Litecoin Cold Storage Address</span>
        3. **MESSAGE BC**
            1. Insert the <span class="warning">Bitcoin Cash Master Public Key QR Code</span>
            for all **N** signatories
            2. Insert the <span class="warning">Bitcoin Cash Cold Storage Address</span>
        4. **MESSAGE E**
            1. Insert the <span class="warning">Ethereum Cold Storage Address</span>
            2. Insert the MultisigWeb Wallet Configuration
        5. **MESSAGE X**
            1. Insert the <span class="warning">Ripple Cold Storage Address</span>
3. gpg encrypt this document (TODO)
4. Send the gpg-encrypted document to all signatories
