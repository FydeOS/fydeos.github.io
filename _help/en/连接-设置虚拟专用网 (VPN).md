---
title: Set up a virtual private network (VPN)
help_section: Connection
weight: 2
type: Document
permalink: /help/connection/vpn/
lang: en
---

FydeOS can connect to a private network (such as the network of an organization or school) through a virtual private network (VPN) connection.

## OpenVPN support function

FydeOS provides basic support for OpenVPN servers. OpenVPN connections can use username / password authentication, client certificate authentication, or a combination of both. Follow the steps below:

1. Select the time in the lower right corner.
2. Select the "Settings" icon.
3. Under the "Network" option, select "Add Connection".
4. Select the "Add" icon next to "OpenVPN / L2TP".
5. Fill in the following information in the box that appears.
 - Server host name: You can enter the IP address or the complete server host name.
 - Service name: You can name the connection at will, for example: "Work VPN".
 - Provider type: select "OpenVPN".
 - Username and password: your VPN credentials. If your server only uses client certificate authentication, you can leave this field blank.
 - One-time password: If you have a dynamic password card or VPN token that can generate a dynamic password, please enter the generated password here. In most cases, this field is not required.
 - Server CA certificate: Please select the certificate issued by the installed certificate authority from the list. The system checks the server's certificate to confirm that the certificate is signed by the correct certificate authority (CA). If you encounter problems with the server certificate, you can choose "no check" to skip CA verification; however, doing so will skip important security measures.
 - User certificate: If your VPN server requires client certificate authentication, please select the installed user VPN certificate from the list. To install the certificate, see the instructions below.
6. Click Connect.

## L2TP / IPsec VPN support function

FydeOS has built-in support for L2TP / IPsec VPN. The IPsec layer uses a pre-shared key (PSK) or user certificate to set up a secure channel. The L2TP layer requires a username and password.

1. Select the time in the lower right corner.
2. Select the "Settings" icon.
3. Under the "Network" option, select "Add Connection".
4. Select the "Add" icon next to "OpenVPN / L2TP".
5. Fill in the following information in the box that appears.
 - Server host name: You can enter the IP address or the complete server host name.
 - Service name: You can name the connection at will, for example: "Work VPN".
 - Provider type: select "L2TP / IPsec + pre-shared key" or "L2TP / IPsec + user certificate".
 - User name, password: your L2TP / PPP credentials. Each VPN user should have his own unique username and password.
 - Group name: IPsec identity field of the client. Some VPN servers are used to set up tunnel groups or user realms. If you are not sure what to fill in, please leave this field blank.
 - Pre-shared key: only used for PSK connections. This key is not your personal password, but the password or key used in the IPsec configuration. In the case of typical settings, the PSK used will be the same as long as it is connected to the same VPN server.
 - Server CA certificate: Only applicable to user certificate connection. Please select the certificate issued by the installed certificate authority from the list. The system checks the server's certificate to confirm that the certificate is signed by the correct certificate authority (CA). If you encounter problems with the server certificate, you can choose "no check" to skip CA verification; however, doing so will skip important security measures.
 - User certificate: Only applicable to user certificate connection. Please select the installed user VPN certificate from the list. If no certificate is installed, you will see an error message. To install the certificate, see the instructions below.
6. Click Connect.

## Install Certificate

You may need to use a certificate to connect to a VPN, WPA2 Enterprise network (such as EAP-TLS), or a website that requires mutual TLS authentication. If this is the case, your administrator may require you to visit a special website when you are directly connected to your organization ’s network, or let you directly download and install the relevant certificate yourself.

You need to obtain the following certificates:
- Server certificate for everyone in the organization
- Personal user certificate

To install the server certificate, please refer to the following steps:
1. Follow the steps provided by the administrator to download the server certificate.
2. Open a new tab in the Chromium browser.
3. Enter `chrome://settings/certificates` in the address bar.
4. Click the "Authorization Center" tab.
5. Click Import and select the X.509 certificate file (the file extension is usually .pem, .der, .crt or .p7b).
6. In the box that appears, fill in the appropriate information. You do not need to turn on any of the settings listed here, so it is recommended that you leave these settings unchecked.
7. The certificate will open and install itself on the current FydeOS device.

Please refer to the following steps to install user certificate:
1. Follow the steps provided by the administrator to download the user certificate. The file name of the certificate should end with .pfx or .p12.
2. Open a new tab in the Chromium browser.
3. Enter `chrome://settings/certificates` in the address bar.
4. Click your certificate.
5. Click Import and bind to device.
6. In the dialog box that opens, select the certificate file and click Open.
7. Enter the password of the certificate as prompted by the system. If you do not know the password, please contact your network administrator. If there is no password, click OK.
8. The certificate will open and install itself on the current FydeOS device.

FydeOS only supports authentication of VPN or EAP wireless networks through RSA client certificates, and does not support authentication through ECC client certificates.
