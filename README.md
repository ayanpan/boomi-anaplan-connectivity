# Connect Anaplan with Boomi using Client Certificate

## Problem Statement:
How to connect Anaplan Workspace with Boomi using Client Certificate

## Pre-requisites:
1. Anaplan Workspace ID
2. Anaplan Public Certificate - .crt and .key files
3. Anaplan Model ID(s)

## Create Private Key Certificate (in MacOS):
1. Go to Launchpad > Terminal.
2. Go to the directory where the .crt and .key files, obtained from Anaplan, are being stored in the computer.
3. Put the following command - ```openssl pkcs12 -export -out anaplandev1.p12 -inkey your_key.key -in your_cert.crt -name "anaplandev1"```, and hit Return.
4. Enter the Export password 2 times, as prompted. This will be required when imporing this certificate in Boomi.
5. The file, anaplandev1.p12, will be stored in the same directory as the .crt and .key files.

## Solution:
1. Select (out of the box) Anaplan Connector in Boomi.
2. Put URL as **https://api.anaplan.com/2/0/**
3. Select "Client Certificate" as the Authentication Type.
4. Put the Workspace ID obtained from Anaplan.
5. In the Certificate, create a new X.509 certificate. Import the anaplandev1.p12 certificate (created in the Step-5 of the previous section). Enter the password as set in the Step-4 of the previous section.
6. Put "anaplandev1" in the Private Key Alias", which is essentially the same value which was set in the Step-3 of the previous section.
7. Test the connection, and it should show as successful.

<img width="577" height="429" alt="image" src="https://github.com/user-attachments/assets/b2fc66d6-bcbe-4b39-98f4-e62aa00e7880" />
