---
anchor: experimental-tpm-fallback
weight: 601
lang: en
---
The Trusted Platform Module(TPM) is usually a chip inside a computer to provide a root of trust for the computer. In order to ensure overall security, many features of FydeOS rely on the functions provided by a TPM chip. There are many different TPM chips and corresponding specifications on the market. Sometimes due to incompatibility, FydeOS for PC cannot initialise the TPM on your device, which will cause the following features to be unavailable:

 - <chrome://flags> shows blank
 - Unable to import custom certificate to Chromium browser
 - "About FydeOS" - "Additional details" - "Change channel" button is greyed out

If you experience the above issues, you can enable this "Bypass TPM checks" as a workaround to make your FydeOS a little bit more permissive and those features should then work.