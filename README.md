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

## Boomi Anaplan Operation - Export and Download:
1. Set Model Id and Export Id, as per the below screenshots, in the Set Properties Shape.
<img width="562" height="467" alt="image" src="https://github.com/user-attachments/assets/f6530a82-9873-4423-befc-ab06963b1401" />

<img width="562" height="467" alt="image" src="https://github.com/user-attachments/assets/597d4828-8bbc-4c08-87f8-9f69604d5d5e" />

<img width="125" height="97" alt="image" src="https://github.com/user-attachments/assets/8efd145e-9806-4f0d-83b8-99ff8e919d56" />

2. Select Anaplan Connector and set the Action as "Export".
3. Import "Dynamic" object in the Anaplan Operation. The objective is to dynamically call the Anaplan Model from multiple Anaplan instances, as the names and IDs are usually different in different Anaplan instances.
4. Set File Id, as per the below screenshots, in the Set Properties Shape. The File Id value is essentially the "objectId" value obtained from the previous Operation.
<img width="562" height="467" alt="image" src="https://github.com/user-attachments/assets/dea5c4c6-be86-4ed6-9c91-b0f6fbc20f5d" />

<img width="543" height="469" alt="image" src="https://github.com/user-attachments/assets/ea9a1d99-5a06-407e-ae77-8d1846b757e8" />

5. Select Anaplan Connector and set the Action as "Download".
6. Import "Dynamic" object in the Anaplan Operation. The objective is to dynamically call the Anaplan Model's File Id, from multiple Anaplan instances, as the names and IDs are usually different in different Anaplan instances.
7. A CSV file will be received from the previous step, which can be extracted and imported into a Flat File Profile Element.
