# 5. Certificates

One of the most common forms of cryptography today is _public-key_ cryptography. Public-key cryptography utilizes a _public key_ and a _private key_. The system works by _encrypting_ information using the public key. The information can then only be _decrypted_ using the private key.

A common use for public-key cryptography is encrypting application traffic using a Secure Socket Layer (SSL) or Transport Layer Security (TLS) connection. One example: configuring Apache to provide _HTTPS_, the HTTP protocol over SSL. This allows a way to encrypt traffic using a protocol that does not itself provide encryption.

A _Certificate_ is a method used to distribute a _public key_ and other information about a server and the organization who is responsible for it. Certificates can be digitally signed by a _Certification Authority_, or CA. A CA is a trusted third party that has confirmed that the information contained in the certificate is accurate.

## 5.1. Types of Certificates

To set up a secure server using public-key cryptography, in most cases, you send your certificate request (including your public key), proof of your company's identity, and payment to a CA. The CA verifies the certificate request and your identity, and then sends back a certificate for your secure server. Alternatively, you can create your own _self-signed_ certificate.

> Note that self-signed certificates should not be used in most production environments.

Continuing the HTTPS example, a CA-signed certificate provides two important capabilities that a self-signed certifacte does not:
- Browsers (usually) automatically recognize the certificate and allow a secure connection to be made without prompting the user.
- When a CA issues a signed certificate, it is guaranteeing the identity of the organization that is providing the web pages to the browser.

Most Web browsers, and computers, that support SSL have a list of CAs whose certificates they automatically accept. If a browser encounters a certificate whose authorizing CA is not in the list, the browser asks the user to either accept or decline the connection. Also, other applications may generate an error message when using a self-signed certificate.

The process of getting a certificate from a CA is fairly easy. A quick overview is a follows:
1. Create a private and public encryption key pair.
1. Create a certificate request based on the public key. The certificate request contains information about your server and the company hosting it.
1. Send the certificate request, along with documents providing your identity, to a CA. We cannot tell you which certificate authority to choose. Your decision may be based on your past experiences, or on the experiences of your friends or colleagues, or purely on monetary factors. Once you have decided upon a CA, you need to follow the instructions they provide on how to obtain a certificate from them.
1. When the CA is satisfied that you are indeed who you claim to be, they send you a digital certificate.
1. Install this certificate on your secure server, and configure the appropriate applications to use the certificate.
