# @subu1979/xml-crypto

A secure XML digital signature and encryption library for Node.js with enhanced security features and modern Node.js compatibility.

## Overview

This package is a fork of the original `xml-crypto` library with the following improvements:

- **Enhanced Security**: Updated dependencies to eliminate security vulnerabilities
- **Modern Node.js Support**: Compatible with Node.js 18+ and includes fixes for deprecated methods
- **TypeScript Support**: Full TypeScript support with modern type definitions
- **Improved Testing**: Enhanced test coverage and modern testing frameworks
- **Security Best Practices**: Built-in security features and deprecation warnings

## Installation

```bash
npm install @subu1979/xml-crypto
```

## Features

### XML Digital Signatures
- **XMLDSIG Support**: Full implementation of XML Digital Signature standards
- **Multiple Algorithms**: Support for RSA, DSA, HMAC, and ECDSA signatures
- **Canonicalization**: Exclusive and inclusive canonicalization methods
- **Transform Support**: XPath, XSLT, and enveloped signature transforms
- **Key Management**: X.509 certificate and key info support

### XML Encryption
- **XMLENC Support**: XML Encryption standards implementation
- **Symmetric Encryption**: AES-128, AES-256, and Triple DES support
- **Asymmetric Encryption**: RSA encryption with OAEP padding
- **Key Transport**: Secure key exchange mechanisms

### Security Features
- **Vulnerability-Free**: All known security vulnerabilities eliminated
- **Modern Crypto**: Updated to use latest secure cryptographic methods
- **Deprecation Warnings**: Built-in warnings for deprecated algorithms
- **Input Validation**: Enhanced input validation and error handling

## Usage

### Basic XML Signing

```typescript
import { SignedXml } from '@subu1979/xml-crypto';

// Create a new signed XML document
const sig = new SignedXml();

// Add a reference to sign
sig.addReference(
  "//*[local-name(.)='X']",
  [
    "http://www.w3.org/2000/09/xmldsig#enveloped-signature",
    "http://www.w3.org/2001/10/xml-exc-c14n#"
  ],
  "http://www.w3.org/2001/04/xmlenc#sha256"
);

// Sign the document
sig.signingKey = privateKey;
sig.computeSignature(xml, {
  prefix: "ds",
  location: { reference: "//*[local-name(.)='X']", action: "after" }
});

console.log(sig.getSignedXml());
```

### XML Signature Verification

```typescript
import { SignedXml } from '@subu1979/xml-crypto';

// Load the signed XML
const doc = new DOMParser().parseFromString(signedXml);

// Create verifier
const sig = new SignedXml();
sig.loadSignature(doc);

// Verify the signature
const result = sig.checkSignature(publicKey);
console.log('Signature valid:', result);
```

### XML Encryption

```typescript
import { EncryptedXml } from '@subu1979/xml-crypto';

// Encrypt XML content
const encrypted = new EncryptedXml();
encrypted.encrypt(xmlContent, {
  algorithm: 'http://www.w3.org/2001/04/xmlenc#aes256-cbc',
  key: symmetricKey
});

// Decrypt XML content
const decrypted = encrypted.decrypt(encryptedXml, {
  key: symmetricKey
});
```

## Configuration

### Security Options

- **Algorithm Validation**: Automatic validation of cryptographic algorithms
- **Key Strength**: Minimum key length requirements
- **Deprecation Warnings**: Warnings for deprecated algorithms and methods

### Performance Options

- **Caching**: Optional caching for improved performance
- **Async Operations**: Support for asynchronous cryptographic operations
- **Memory Management**: Efficient memory usage for large documents

## Supported Algorithms

### Signature Algorithms
- **RSA**: RSA-SHA1, RSA-SHA256, RSA-SHA512
- **DSA**: DSA-SHA1, DSA-SHA256
- **HMAC**: HMAC-SHA1, HMAC-SHA256, HMAC-SHA512
- **ECDSA**: ECDSA-SHA1, ECDSA-SHA256, ECDSA-SHA512

### Encryption Algorithms
- **Symmetric**: AES-128-CBC, AES-256-CBC, Triple DES
- **Asymmetric**: RSA-OAEP, RSA-PKCS1
- **Key Derivation**: PBKDF2, HKDF

### Hash Algorithms
- **SHA-1**: Legacy support (deprecated)
- **SHA-256**: Recommended for new implementations
- **SHA-512**: High-security applications

## Breaking Changes from Original

- **Package Name**: Changed to `@subu1979/xml-crypto`
- **Minimum Node.js**: Version 18.0.0 or higher
- **Dependencies**: Updated to latest secure versions
- **TypeScript**: Modern TypeScript support with strict types

## Migration Guide

If you're upgrading from the original `xml-crypto` package:

1. **Update your package.json**:
   ```json
   {
     "dependencies": {
       "@subu1979/xml-crypto": "^6.0.0"
     }
   }
   ```

2. **Update your import statements**:
   ```typescript
   // Old
   import { SignedXml } from 'xml-crypto';
   
   // New
   import { SignedXml } from '@subu1979/xml-crypto';
   ```

3. **Check for deprecated methods**:
   ```typescript
   // Old (deprecated)
   const node = ref.getValidatedNode();
   
   // New (recommended)
   const node = ref.signedReference;
   ```

## Testing

```bash
# Run all tests
npm test

# Run tests with coverage
npm run test:coverage

# Run linting
npm run lint

# Fix linting issues
npm run lint:fix
```

## Security

This package includes several security improvements:

- **Dependency Updates**: All dependencies updated to eliminate known vulnerabilities
- **Algorithm Validation**: Built-in validation for cryptographic algorithms
- **Input Sanitization**: Enhanced input validation and sanitization
- **Memory Safety**: Improved memory management and leak prevention

## Contributing

This is a maintained fork focused on security and modern Node.js compatibility. For original package issues, please refer to the upstream repository.

## License

MIT License - see LICENSE file for details.

## Support

For security issues, please report them responsibly. This package includes:

- Regular dependency updates
- Security vulnerability scanning
- Modern crypto method support
- Enhanced error handling and validation
