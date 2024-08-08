# End-to-end encryption (E2EE)

## How does end-to-end encryption work?

End-to-end encryption (E2EE) protects your messages and files from being accessed and manipulated by other people other than those you send them to.

𝗛𝗼𝘄 𝗶𝘁 𝘄𝗼𝗿𝗸𝘀:

𝟭) 𝗞𝗲𝘆𝘀 𝗴𝗲𝗻𝗲𝗿𝗮𝘁𝗲𝗱
In each app, every account has two keys: one is public and can be shared with anyone; the other should be kept secret. Although these keys are mathematically related, it's impossible to determine someone's private key from their public key.

𝟮) 𝗣𝘂𝗯𝗹𝗶𝗰 𝗸𝗲𝘆 𝗲𝘅𝗰𝗵𝗮𝗻𝗴𝗲
When two people begin a conversation, they exchange their public keys. Since public keys don't have to be kept secret, this can occur through any type of communication channel.

𝟯) 𝗘𝗻𝗰𝗿𝘆𝗽𝘁𝗶𝗼𝗻
When a user wants to send a message, it is protected using symmetric and asymmetric encryption. In asymmetric encryption, the public key is used for encryption, and the private key for decryption. Whereas symmetric encryption uses a single session key for both. In E2EE, the sender generates a unique session key and encrypts the data with it. Then, they encrypt the session key itself with the recipient's public key.

𝟰) 𝗗𝗮𝘁𝗮 𝘁𝗿𝗮𝗻𝘀𝗺𝗶𝘀𝘀𝗶𝗼𝗻
The encrypted message and session key are then sent over the internet. The encryption makes sure that only the sender and receiver can read the data, even if someone intercepts it during transmission.

𝟱) 𝗗𝗲𝗰𝗿𝘆𝗽𝘁𝗶𝗼𝗻
When an encrypted message is received, the receiver uses their private key to unlock the session key; which they then use to decrypt the message.

End-to-end encryption is only as powerful as the cryptographic algorithms used, and how well they are implemented. When done right, E2EE boosts the security of digital communications, protecting them from eavesdropping and tampering.

![End-to-end encryption (E2EE)](./img/Security/E2EE.jpg)


## End-to-end encryption (E2EE)
End-to-end encryption (E2EE) is a method of secure communication that prevents third-parties from accessing data while it's transferred from one end system or device to another. In simpler terms, it ensures that only the sender and the intended recipient can read the messages or data, and even the service provider facilitating the communication cannot access the plaintext data.

Here's a basic overview of how end-to-end encryption typically works:

1. **Key Generation**: Each user generates a pair of cryptographic keys – a public key and a private key. The public key is shared with others, while the private key is kept secret.

2. **Message Encryption**: When User A wants to send a message to User B, User A's device uses User B's public key to encrypt the message. This means only User B's private key can decrypt the message.

3. **Message Transmission**: The encrypted message is then sent over the communication channel, whether it's a messaging app, email service, or another platform.

4. **Message Decryption**: When User B receives the message, their device uses their private key to decrypt the message, making it readable.

5. **Security Assurance**: Since only the intended recipient has the private key necessary for decryption, even if the communication is intercepted by a malicious third-party, they would only see encrypted data, which is essentially indecipherable without the private key.

End-to-end encryption is widely used in various communication platforms such as messaging apps (like Signal and WhatsApp) and email services (like ProtonMail). It ensures privacy and security by making it extremely difficult for anyone other than the intended recipient to access the content of the communication.
```mermaid
%% graph TD;
flowchart LR; 
    A[Key Generation] --> B[Message Encryption];
    B --> C[Message Transmission];
    C --> D[Message Decryption];
    D --> E[Readable Message];
        style A fill:#9acd32, stroke:#333, stroke-width:2px;
    style B fill:#87ceeb, stroke:#333, stroke-width:2px;
    style C fill:#ffa07a, stroke:#333, stroke-width:2px;
    style D fill:#87ceeb, stroke:#333, stroke-width:2px;
    style E fill:#9acd32, stroke:#333, stroke-width:2px;
```

## References
1. https://twitter.com/ChrisStaud/status/1702686681902797097?t=X1sAt_mfU-XcCGvzNTf3WQ&s=08
