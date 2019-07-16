---
title: Create your Bitcoin, Litecoin, and Bitcoin Cash Multisig Wallets
description: Learn how to create your bitcoin, litecoin, and bitcoin-cash
  multisig wallets using CryptoGlacier, the step-by-step, secure,
  multi-blockchain, multi-signature, cold storage protocol for long-term
  storage of crypto assets based on the popular Glacier Protocol
---

In this section you'll setup the Multisig Wallets for Bitcoin, Litecoin, and
Bitcoin Cash. You will also verify your deposit addresses.

Your Bitcoin, Litecoin, and Bitcoin Cash wallets are derived from your chosen
M-of-N policy and the <span class="warning">Master Public Keys</span> from the
N signatories. The derivation is deterministic, so as long as you keep a copy
of the N <span class="warning">Signatory Information Packets</span> and you
know the chosen M-of-N policy that was chosen, you should be able to derive
your wallets. In order to access your funds, you will need to know the M-of-N
policy that was chosen, N <span class="warning">Master Public Keys</span>, and
at least M signatories should have access to their <span class="danger">BIP39 Mnemonic</span>.

The following process can be done at an internet connected computer and should
be verified across signatories.

1. Derive Wallet Address Using Electrum
  1. Open Electrum
  ```
  $ ~/apps/electrum-3.3.6-x86_64.AppImage
  ```
  2. Select `Auto connect` and click `Next.
  3. Leave the default wallet name and click `Next`.
  4. Select `Multi-signature wallet` and click `Next`.
  5. Select your chosen M-of-N policy. The top bar, `cosigners` is the `N`
  and the lower bar, `Required signatures` is the `M`. Click `Next`.
  6. Select `Use a master key` and click `Next`.
  7. You will be asked to enter your <span class="warning">Bitcoin Master Public Key</span>.
  For Bitcoin, this is marked as **Message B** in your <span class="warning">Signatory Information Packets</span>.
  You can scan the <span class="warning">QR Code</span> or enter it manually.
  Click `Next` twice.
  8. Select `Enter cosigner key` and click `Next`.
  9. You will now need to scan or enter the other N-1 <span class="warning">Bitcoin Master Public Keys</span>.
  These are all marked with **Message B** on your <span class="warning">Signatory Information Packets</span>.
  10. You don't need to enter a password, just click `Next`.
  11. Click on the `Receive` tab. This will show your <span class="warning">receiving address</span>
  which is basically your <span class="warning">bitcoin cold storage address</span>.
2. Verify the <span class="warning">Bitcoin cold storage address</span>
  1. Click on the <span class="warning">QR Code</span>
  2. Use the smartphone's QR code reader to read the <span class="warning">QR Code</span>.
  When the <span class="warning">QR Code</span> is successfully read, the
  smartphone should display the text version of the <span class="warning">bitcoin cold storage address</span>.
  3. Send this address to all your signatories and make sure they have derived
  the same address across their devices.
  4. If the verification fails, seek assistance
3. Repeat steps 1 and 2 for Litecoin and Bitcoin Cash
  1. For Litecoin use the following program and the **Message L** keys:
  ```
  $ ~/apps/electrum-ltc-3.3.6.1-x86_64.AppImage
  ```
  2. For Bitcoin Cash use the following program and the **Message BC** keys:
  ```
  $ ~/apps/Electron-Cash-4.0.6-x86_64.AppImage
  ```
    1. Electron Cash calls `master keys` simply `public or private keys`
