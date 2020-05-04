---
title: Connect to Wi-Fi
help_section: Connection
weight: 4
type: Document
permalink: /help/connection/wifi/
lang: en
---

To connect to the Internet, use a Wi-Fi network supported by the device.

## Turn on Wi-Fi

1. Select the time in the lower right corner.
2. Select the "Not Connected" icon. Note that if you see the Wi-Fi network name and signal strength, it means you are connected to the Wi-Fi network.
3. Turn on Wi-Fi.
4. FydeOS will automatically find available networks and display them in a list.

## Choose a network and connect

- Connect to an open network: Select the "Wi-Fi Network" icon. Please note that other users on this network may see your information.
- Connect to a secure network: Select the "secure Wi-Fi network" icon. Enter the network password. Select "Connect".
- Connect to unlisted networks: Administrators may hide some networks, so only certain users can use these networks. To connect to an unlisted network, select the "Add to other network" icon, enter the relevant network information in the dialog box that appears, and select "Connect". The system will automatically save information about this network so that you can automatically connect to this network in the future.

## Connect to WPA2 Enterprise network

First, check whether your certificate has been installed:
1. Open the Chromium browser.
2. Enter `chrome://settings/certificates` in the address bar, and then press the `Enter` key.
3. Select "Authorization Center".
4. Find your server certificate in the list based on the information provided by the administrator. If you have not installed the server certificate, the administrator may ask you to install the server certificate. Click "Import" and select the X.509 certificate file (the file extension is usually .pem, .der, .crt or .p7b). In the box that appears, fill in the appropriate information. The certificate will open and install itself on the device.

Then, connect to the network:
1. Select the time in the lower right corner.
2. Select the "Settings" icon.
3. Under the "Network" option, select "Add Connection" - "Add Wi-Fi" - "Advanced".
4. Enter your network information. If you have installed a server certificate, please select the default in the "Server CA Certificate" field.
5. Select "Connect".

## View MAC address or IP address

Some administrators restrict network access to prevent outsiders from accessing private information on the network. You may need to provide the administrator with a MAC address or IP address to use the network. To view the MAC address or IP address:

1. If you have not logged in to FydeOS, please log in first.
2. Select the time in the lower right corner.
3. Select the "Wi-Fi Network" icon.
4. Select the "Information" icon at the top of the box.
5. You will see the IP address, IPv6 address and Wi-Fi of the current device. Among them, Wi-Fi is your MAC address.

## Wi-Fi network supported by FydeOS

- Open network without password
- Secure network set up using WEP, dynamic WEP, WPA-PSK, WPA-Enterprise or WPA2-Enterprise
- Standard network: 802.11 a/b/g/n and 802.11ac
