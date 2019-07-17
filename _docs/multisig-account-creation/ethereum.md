---
title: Create your Ethereum Multisig Contract
description: Learn how to create your ethereum multisig contract using CryptoGlacier,
  the step-by-step, secure, multi-blockchain, multi-signature,
  cold storage protocol for long-term storage of crypto assets
  based on the popular Glacier Protocol
---

In this section you will deploy an Ethereum Multisig Smart Contract based on the
[Gnosis Multisignature Wallet Contract](https://github.com/gnosis/MultiSigWallet).

**As a reminder, this section should only be executed by one agreed upon
signatory.** If you are not that signatory, please skip this section.

# Deploying the Contract
1. Download Multisigweb
  1. On an internet enabled computer, dowload and install [Gnosis Multisignature Wallet](https://github.com/gnosis/MultiSigWallet/releases).
  2. Please make sure you verify the SHA256 checksums. At the time of writing, v1.6.0 was the latest version
2. Create a new Ethereum Account that will be used to deploy the contract
  1. Open multisigweb
  2. Agree to the `Terms of Use` and `Privacy Policy`
  3. Select `Light Wallet`
  4. Click on `Accounts`
  5. Click on `Add`
  6. Choose and confirm a password
  7. Choose a name for the account (can be anything)
  8. Click `Create Account`
3. Send funds to the account that was just created
  1. Check the current gas prices at [ethgasstation](https://ethgasstation.info/)
  2. Multiply the gas price by `2,057,168` and divide by `10^18` to see how much
  ETH you will need to deploy the contract. We recommend you send twice the
  amount from the calculation.
  3. Click the `Copy` button next to the address created in the step above
  4. Send the ETH (beyond the scope of this protocol) to the address above
  5. Wait for the transaction to be confirmed, you should see the new balance
  on the top right section of the screen, next to the account address.
4. Deploy new Multisig Wallet
  1. Go the the `Wallets` tab
  2. Click on `Add`
  3. Select `Create new wallet`
  4. Select a wallet name (can be anything)
  5. Enter **M** (for your chosen M-of-N policy)
  6. Leave daily limit at 0
  7. Click on `Remove` so the address that deployed the contract does not have
  signatory rights over the contract
  8. Enter the <span class="warning">Ethereum Addresses</span> of the **N** signatories.
  **You should have N Owners**.
  9. Click on `Deploy with factory`
  10. You can check [ethgasstation](https://ethgasstation.info/) to validate the
  gas price. Leave all the other fields to their default.
5. Monitor Contract Deployment
  1. Go to the `Transactions` tab
  2. Wait for the transaction to be mined
  3. If you go to the `Wallets` tab, you should now see your Multisig contract
6. Share your <span class="warning">Ethereum Cold Wallet Address</span> with
the other signatories
  1. Go to the `Wallets` tab
  2. Click on `Copy` on the `Address` Column
  3. Send to the <span class="warning">Ethereum Cold Wallet Address</span> to
  the other signatories.
