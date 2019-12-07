---
title: Different SSL Cert Format
catalog: true
date: 2019-12-07 20:32:36
updateDate: 2019-12-07 20:32:36
subtitle:
header-img: "norway_18.jpg"
tags:
---

In the world of Public Key Infrastructure (PKI) there are many different file formats. The following are the major ones.

* x509/PEM
* pkcs#7/P7B
* pkcs#12/PFX/P12

#### x509/PEM Format
The PEM format is the most common format that **Certificate Authorities (CA)** issue certificates in. PEM certificates usually have extentions such as **.pem, .crt, .cer, and .key**. They are Base64 encoded ASCII files and contain “—–BEGIN CERTIFICATE—–” and “—–END CERTIFICATE—–” statements. Server certificates, intermediate certificates, and private keys can all be put into the PEM format. But Typically the private key will contain the following “—–BEGIN RSA PRIVATE KEY—–” and “—–END RSA PRIVATE KEY —–” Statements.

Apache and other similar servers use PEM format certificates. Several PEM certificates, and even the private key, can be included in one file with each individual certificate sandwiched on top of each other, one below the other, but most platforms, such as Apache, expect the certificates and private key to be in separate files.

#### PKCS#7/P7B Format
The PKCS#7 or P7B format is usually stored in **Base64** encoded ASCII format and has a file extension of **.p7b** or **.p7c. P7B** certificates usually contain the following “—–BEGIN PKCS7—–” and “—–END PKCS7—–” statements as header and footers. A P7B file only contains certificates and chain certificates, not the private key. Several platforms support P7B files including **Microsoft Windows** and **Java Tomcat**.

#### PKCS#12/PFX Format
The PKCS#12 or PFX format is a binary format for storing the server certificate, any intermediate certificates, and the private key in one encryptable file. PFX files usually have extensions such as .pfx and .p12. PFX files are typically used on Windows machines to import and export certificates and private keys.

#### PKCS#10 Format
The PKCS#10 is an actual **certificate signing request** (also **CSR** or **certification request**) This is a message sent from an applicant to a certificate authority in order to apply for a digital identity certificate. It usually contains the public key for which the certificate should be issued, identifying information (such as a domain/common name).

**The more you know:** Before creating a CSR, the applicant first generates a key pair, keeping the private key secret during its creation. Once the CSR has been submitted to a certificate authority an SSL Certificate will be born/issued that will only work with the private key created during CSR keypair creation.

#### DER Format
The DER format is simply a binary form of a certificate instead of the ASCII PEM format. It sometimes has a file extension of **.der** but it often has a file extension of **.cer** so the only way to tell the difference between a DER .cer file and a PEM .cer file is to open it in a text editor you will see a bunch of hexadecimal gibberish. All types of certificates and private keys can be encoded in DER format but is very rarely used. DER is typically used with **Java platforms**.