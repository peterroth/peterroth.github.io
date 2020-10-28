---
title: Symmetric and Asymmetric Encryption
tags: security
---
Almost everybody use encryption day by day, but most of us unaware of it. Every time you open a website with HTTPS (the S stand for Secure), (after a host validation) your data is encrypted between your device and the server. But why? And how?  

### The reason
It's very simple. Only you and the other party who you "talk with" should be able to read your messages, nobody else. Every data you send or receive (the text on websites, messages, pictures, videos) go through a lot of network devices until they reach their destination, and unencrypted communication can be breached by any device or person between source and the target. For example, you want to check your bank account. Naturally, you don't want to share those details with the world; this is why every bank's website accessible only with HTTPS (the S stands for Secure) and not pure HTTP; after your browser or application validates you are connected to the machine you really wanted to, it builds up a tunnel where every exchanged bit masked, encrypted.  

### What is what?
Cryptography is the method of using mathematical principles to transmit or store data securely, so only those whom are intended to have access can read and process it. The process that encodes the messages you'll transfer into a format that cannot be understood nor read by any other device between the two parties who communicate called encryption.  
The sender encrypts the date and the receiver must decrypt the message to be able to process it. For the this process, keys are being used. There are different type of keys in cryptography, but now I'll focus how the key is shared between the parties.  

### Symmetric encryption
Imagine you create a password protected ZIP file. Only the one who knows this password will be able to unzip it and access the real data. If you share the file with somebody, you must share the password as well; and everybody who has that secret key is able to decrypt and encrypt. This is why it isn't so widely used on the internet; in case somebody catches the key (the password, in this example), the data isn't protected anymore and if you change the password you must re-share that with everybody. This is the simplest kind of encryption.

### Asymmetric encryption
This cryptography uses 2 related keys, a public and a private key. Anybody can encrypt data with the public key, but only the one with the private key can decrypt that. You must protect only the private key, the public can be shared on a network because one key can be used only to encrypt or decrypt, and only the other can do the opposite. Due to this, asymmetric cryptography is widely used on the internet, especially while browsing websites (pages with HTTPS uses it, for example) or communicating (in privacy aware chat platforms) because every time you initiate a connection with a service, you can share the public key with the other party through the network and even if somebody catches that, cannot decrypt the messages you receive as long as the private key is protected.