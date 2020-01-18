---
title: Create App USBs
description: Learn how to prepare your USB drives for CryptoGlacier,
  the step-by-step, secure, multi-blockchain, multi-signature,
  cold storage protocol for long-term storage of crypto assets
  based on the popular Glacier Protocol
---

Each signatory should do the following:

We will prepare two (2) "Quarantined App USB"
drives with the software needed to execute the remainder of the protocol.
These are the USB drives you labeled "Q1 APP" and "Q2 APP" in Section
III.

1. Boot the SETUP 1 computer off the SETUP 1 BOOT USB if it is not
already. (See the instructions in Section III for details.)
2. Insert the Q1 APP USB into the the SETUP 1 computer.

    1. **The instruction to plug a Quarantined App USB into your Setup computer
    *should* raise a red flag for you, because <span style="color: red;">you should never plug a quarantined
    USB into anything other than the quarantined computer it is designated for!</span>**

       This setup process is the ONE exception.

3. Press Ctrl-Alt-T to open a terminal window.
4. Download the CryptoGlacier protocol document and accompanying scripts
    1. Download the latest full release of CryptoGlacier (*not* just the protocol
    document) at
    [https://github.com/vogelito/CryptoGlacierProtocol/releases](https://github.com/vogelito/CryptoGlacierProtocol/releases).
    2. Unpack the CryptoGlacier ZIP file into a staging area.

        1. When the download starts, Firefox will ask you if you want to open the
        ZIP file with Archive Manager. Click OK.

           When the ZIP file download completes, it will be opened with Archive Manager.

        2. There will be a single entry in a list named
        "CryptoGlacierProtocol-<span class="primary">version-here</span>", where
        <span class="primary">version-here</span> is replaced with
        the current version number (like "v0.02"). Click on that and then click
        the "Extract" button.
        3. The Archive Manager will ask you where you want to extract the ZIP
        file to. Select "Home" on the left panel and then press the extract button.
        4. When the Archive Manager is finished extracting the ZIP archive it
        will ask you what to do next. Click "Show the Files".
        5. Rename the unzipped folder from "CryptoGlacierProtocol-<span class="primary">version-here</span>" to
        "cryptoglacier".

    3. Obtain the CryptoGlacier "public key," used to cryptographically verify the
    CryptoGlacier document and CryptoGlacierScript.

        **If you are ever using CryptoGlacier in the future and notice that this step
        has changed (or that this warning has been removed), there is a
        security risk.** Stop and seek assistance.

        1. Access CryptoGlacier's Keybase profile at [https://keybase.io/vogelito](https://keybase.io/vogelito).
        2. Click the string of letters and numbers next to the key icon.
        3. In the pop-up that appears, locate the link reading "this key".
        4. Right-click the link and select "Save Link As..."
        5. Name the file "cryptoglacier.asc".

    4. Verify the integrity of the CryptoGlacier download.

        1. Import the CryptoGlacier public key into your local GPG installation:
           ```
           $ gpg --import ~/Downloads/cryptoglacier.asc
           ```
        2. Switch to the cryptoglacier folder:
           ```
           $ cd ~/cryptoglacier
           ```
        3. Use the public key to verify that the CryptoGlacier "fingerprint file" is
        legitimate:
           ```
           $ gpg --verify SHA256SUMS.sig SHA256SUMS
           ```
           Expected output (timestamp will vary, but
           e-mail and fingerprint should match):
           <pre>
           <span style="font-size: 10px;">gpg: Signature made Thu Jun 20 18:01:31 2019 CDT
           gpg:                using RSA key 3378240146B53C307FBA4B0D97F10485CCBACA30
           gpg: Good signature from "Daniel Vogel <vogel@bitso.com>" [unknown]
           gpg:                 aka "Daniel Vogel <dvogel@cs.stanford.edu>" [unknown]
           gpg: WARNING: This key is not certified with a trusted signature!
           gpg:          There is no indication that the signature belongs to the owner.
           Primary key fingerprint: 3378 2401 46B5 3C30 7FBA  4B0D 97F1 0485 CCBA CA30
           </span>
           </pre>

           The warning message is expected, and is not cause for alarm.

        4. Verify the fingerprints in the fingerprint file match the fingerprints
        of the downloaded CryptoGlacier files:
           ```
           $ sha256sum -c SHA256SUMS 2>&1
           ```
           Expected output:
           ```
           CryptoGlacier.pdf: OK
           README.md: OK
           mnemonic_entropy.py: OK
           package.json: OK
           package-lock.json: OK
           setup.js: OK
           ```
5. Open the CryptoGlacier protocol document so that it is available for copy-pasting terminal commands.
6. Install the remaining application software on the Q1 APP USB.
    1. Configure our system to enable access to the software we need in Ubuntu's
    "package repository".On Ubuntu 16.04.01  [there is a bug](https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1601971) in Ubuntu's package manager that affects systems
    running off a bootable Ubuntu USB. The commands in steps a and b are a
    workaround.
        1. ```
        $ sudo mv /var/cache/app-info/xapian/default \
        /var/cache/app-info/xapian/default_old
        ```
        2. ```
        $ sudo mv /var/cache/app-info/xapian/default_old \
        /var/cache/app-info/xapian/default
        ```
        3. ```
        $ sudo apt-add-repository universe
        ```
        4. ```
        $ curl -sSL \
        https://deb.nodesource.com/gpgkey/nodesource.gpg.key \
        | sudo apt-key add -
        $ echo "deb https://deb.nodesource.com/node_10.x xenial main" \
        | sudo tee /etc/apt/sources.list.d/nodesource.list
        $ echo "deb-src https://deb.nodesource.com/node_10.x xenial \
        main" | sudo tee -a /etc/apt/sources.list.d/nodesource.list
        ```
        5. ```
        $ sudo apt-get update
        ```
    2. Download and perform integrity verification of software available from Ubuntu's package repository:
        * **libappindicator1** and **libindicator7**: Dependencies for multisigweb (see below)
        * **nodejs** and **npm**: Required to run the cryptoglacierscript
        * **qrencode**: Used for creating QR codes to move data off quarantined
        computers
        * **zbar-tools**: Used for reading QR codes to import data into quarantined
        computers
            ```
            $ sudo apt-get -y install \
            libindicator7=12.10.2+16.04.20151208-0ubuntu1 \
            libappindicator1=12.10.1+16.04.20170215-0ubuntu1 \
            nodejs=10.18.1-1nodesource1 \
            qrencode=3.4.4-1 \
            zbar-tools=0.10+doc-10ubuntu1
            ```
        * **multisigweb**: Used to manage multi-location multisig cold wallets for ETH and ERC20 token
            ```
            $ mkdir ~/dls
            $ cd ~/dls
            $ wget https://github.com/gnosis/MultiSigWallet/releases/download/v1.6.0/multisigweb-1.6.0-amd64.deb.zip
            ```
            Make sure the output of `$ sha256sum multisigweb-1.6.0-amd64.deb.zip` is:
            ```
            607e1e94cb5d4d9deb2b05eb0d9f6aaa6a41eaba531b3333dea5da90e2f29350
            ```
            Unzip:
            ```
            $ unzip multisigweb-1.6.0-amd64.deb.zip
            ```
        * **Electrum**: Used to manage multi-location multisig cold wallets
            ```
            $ wget https://download.electrum.org/3.3.6/electrum-3.3.6-x86_64.AppImage
            $ wget https://download.electrum.org/3.3.6/electrum-3.3.6-x86_64.AppImage.asc
            ```
            Import the signing keys
            ```
            $ wget https://raw.githubusercontent.com/spesmilo/electrum/3.3.6/pubkeys/ThomasV.asc
            $ gpg --import ThomasV.asc
            ```
            Verify the file
            ```
            $ gpg --verify electrum-3.3.6-x86_64.AppImage.asc electrum-3.3.6-x86_64.AppImage
            ```
            You should see something similar to (verify fingerprint matches):
            ```
                gpg: Signature made Thu 16 May 2019 06:14:30 PM UTC using RSA key ID 7F9470E6
                gpg: Good signature from "Thomas Voegtlin (https://electrum.org) <thomasv@electrum.org>"
                gpg:                 aka "ThomasV <thomasv1@gmx.de>"
                gpg:                 aka "Thomas Voegtlin <thomasv1@gmx.de>"
                gpg: WARNING: This key is not certified with a trusted signature!
                gpg:          There is no indication that the signature belongs to the owner.
                Primary key fingerprint: 6694 D8DE 7BE8 EE56 31BE  D950 2BD5 824B 7F94 70E6
            ```
        * **ElectronCash**: Used to manage multi-location multisig cold wallets
            ```
            $ wget https://github.com/Electron-Cash/Electron-Cash/releases/download/4.0.6/Electron-Cash-4.0.6-x86_64.AppImage
            $ wget https://github.com/Electron-Cash/keys-n-hashes/raw/master/sigs-and-sums/4.0.6/win-linux/Electron-Cash-4.0.6-x86_64.AppImage.asc
            $ wget https://github.com/Electron-Cash/keys-n-hashes/raw/master/sigs-and-sums/4.0.6/win-linux/SHA256.Electron-Cash-4.0.6-x64_64.AppImage.txt
            ```
            Import the signing keys
            ```
            $ gpg --import <(curl -L https://raw.githubusercontent.com/fyookball/keys-n-hashes/master/pubkeys/jonaldkey2.txt)
            ```
            Make sure the output of `$ sha256sum -c SHA256.Electron-Cash-4.0.6-x64_64.AppImage.txt` is:
            ```
            Electron-Cash-4.0.6-x86_64.AppImage: OK
            ```
            Verify the signatures
            ```
            $ gpg --verify Electron-Cash-4.0.6-x86_64.AppImage.asc Electron-Cash-4.0.6-x86_64.AppImage
            ```
            You should see something similar to (verify fingerprint matches):
            ```
                gpg: Signature made Thu 06 Jun 2019 02:46:52 PM UTC using DSA key ID EFF1DDE1
                gpg: Good signature from "Jonald Fyookball <jonf@electroncash.org>"
                gpg: WARNING: This key is not certified with a trusted signature!
                gpg:          There is no indication that the signature belongs to the owner.
                Primary key fingerprint: D56C 110F 4555 F371 AEEF  CB25 4FD0 6489 EFF1 DDE1
            ```
        * **Electrum-LTC**: Used to manage multi-location multisig cold wallets
            ```
            $ wget https://electrum-ltc.org/download/electrum-ltc-3.3.6.1-x86_64.AppImage
            $ wget https://electrum-ltc.org/download/electrum-ltc-3.3.6.1-x86_64.AppImage.asc
            ```
            Import signing keys from keyserver
            ```
            $ gpg --keyserver pool.sks-keyservers.net --recv-keys 0x6fc4c9f7f1be8fea 0xfe3348877809386c
            ```
            You should see something similar to
            ```
                gpg: requesting key F1BE8FEA from hkp server pool.sks-keyservers.net
                gpg: requesting key 7809386C from hkp server pool.sks-keyservers.net
                gpg: key F1BE8FEA: public key "pooler <pooler@litecoinpool.org>" imported
                gpg: key 7809386C: public key "Adrian Gallagher <thrasher@addictionsoftware.com>" imported
                gpg: no ultimately trusted keys found
                gpg: Total number processed: 2
                gpg:               imported: 2  (RSA: 2)
            ```
            Verify that the fingerprints are correct
            ```
            $ gpg --fingerprint 0x6fc4c9f7f1be8fea 0xfe3348877809386c
            ```
            You should see:
            ```
                pub   2048R/F1BE8FEA 2013-07-21
                      Key fingerprint = CAE1 092A D355 3FFD 21C0  5DE3 6FC4 C9F7 F1BE 8FEA
                uid                  pooler <pooler@litecoinpool.org>
                sub   2048R/A31415A6 2013-07-21

                pub   2048R/7809386C 2013-06-19
                      Key fingerprint = 59CA F0E9 6F23 F537 4794  5FD4 FE33 4887 7809 386C
                uid                  Adrian Gallagher <thrasher@addictionsoftware.com>
                sub   2048R/6FB978EE 2013-06-19

            ```
            Verify signature of downloaded files
            ```
            $ gpg --verify electrum-ltc-3.3.6.1-x86_64.AppImage.asc electrum-ltc-3.3.6.1-x86_64.AppImage
            ```
            You should see something like:
            ```
                gpg: Signature made Wed 22 May 2019 07:07:53 AM UTC using RSA key ID F1BE8FEA
                gpg: Good signature from "pooler <pooler@litecoinpool.org>"
                gpg: WARNING: This key is not certified with a trusted signature!
                gpg:          There is no indication that the signature belongs to the owner.
                Primary key fingerprint: CAE1 092A D355 3FFD 21C0  5DE3 6FC4 C9F7 F1BE 8FEA
            ```
        * **BIP39**: Used to manage multi-location multisig cold wallets
            ```
            $ wget https://github.com/iancoleman/bip39/releases/download/0.3.11/bip39-standalone.html
            ```
            Make sure the output of `$ sha256sum bip39-standalone.html` is:
            ```
            954691257c7ab59175de365688e3bc7c1112e1392d308c1b97336b23854fe397
            ```

    3. Copy that software to the Q1 APP USB.
        1. Create a folder for the application files that will be moved to the
        USB:
            ```
            $ mkdir ~/apps
            ```
        2. Copy the software into the apps folder:
            ```
            $ cp /var/cache/apt/archives/*.deb ~/apps
            $ cp ~/dls/electrum-3.3.6-x86_64.AppImage ~/apps
            $ cp ~/dls/Electron-Cash-4.0.6-x86_64.AppImage ~/apps
            $ cp ~/dls/electrum-ltc-3.3.6.1-x86_64.AppImage ~/apps
            $ cp ~/dls/bip39-standalone.html ~/apps
            $ cp ~/dls/multisigweb-1.6.0-amd64.deb ~/apps
            ```
        3. Copy the contents of the apps folder to the Q1 APP USB:
            1. Click on the File Manager icon in the launching dock:
            2. Navigate to the "Home" folder.
            3. Click and drag "apps" folder to the icon representing
            the USB drive on the left panel.

7. Install the required packages for the CryptoGlacier scripts and install CryptoGlacier on the Q1 APP USB.
    1. Install the required packages for the node script:
       ```
       $ cd ~/cryptoglacier
       $ npm install
       ```

    2. Copy the cryptoglacier folder to the Q1 APP USB.
        1. Click on the File Manager icon in the launching dock along the left
        side of the screen.
        2. Find the "cryptoglacier" folder under "Home".
        3. Click and drag the cryptoglacier folder to the icon representing the USB
        drive on the left.
        4. You may get errors related to copying `rlp`, `sha.js`, and `uuid`. You can
        safely skip those
        5. If you see a different "Error while copying" pop-up, you may be suffering from
        [this Ubuntu bug](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1021375).
        To fix it, do the following and then retry copying the files:

            1.
                ```
                $ mv ~/.config/nautilus ~/.config/nautilus-bak
                ```
            2. Log out of Ubuntu: Click the power icon in the top right of the
            screen and select "logout" from the drop-down menu.
            3. Login again with user "ubuntu" and leave the password blank.

8. Click on the USB drive icon to verify that it has the correct files. The
contents should look like this
    ```
    apps
    cryptoglacier
    ```

    Click the apps folder. It will have the following content:

    ```
    bip39-standalone.html
    Electron-Cash-4.0.6-x86_64.AppImage
    electrum-3.3.6-x86_64.AppImage
    electrum-ltc-3.3.6.1-x86_64.AppImage
    libappindicator1_12.10.1+16.04.20170215-0ubuntu1_amd64.deb
    libdbusmenu-gtk4_16.04.1+16.04.20160927-0ubuntu1_amd64.deb
    libindicator7_12.10.2+16.04.20151208-0ubuntu1_amd64.deb
    libqrencode3_3.4.4-1_amd64.deb
    libzbar0_0.10+doc-10ubuntu1_amd64.deb
    multisigweb-1.6.0-amd64.deb
    nodejs_10.18.1-1nodesource1_amd64.deb
    qrencode_3.4.4-1_amd64.deb
    zbar-tools_0.10+doc-10ubuntu1_amd64.deb
    ```
    Click the cryptoglacier folder. It will have the following content:
    ```
    node_modiules
    CryptoGlacier.pdf
    LICENSE
    mnemonic_entropy.py
    package.json
    package-lock.json
    README.md
    setup.js
    SHA256SUMS
    SHA256SUMS.sig
    ```
9. Eject and physically remove the Q1 APP USB from the SETUP 1 computer.

    **The Q1 APP USB is now eternally quarantined. It should never again be
    plugged into anything besides the Q1 computer.**

10. Repeat all above steps using the SETUP 2 computer, SETUP 2 BOOT USB, and Q2
APP USB.
11. Find a container in which to store all of your labeled hardware, along
with the CryptoGlacier document hardcopy, when you are finished.
