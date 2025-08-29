# Changelog

All notable changes to this project will be documented in this file.

## [6.0.0] - 2025-08-29

### Changed
- **BREAKING**: Package name changed from `xml-crypto` to `@subu1979/xml-crypto`
- **BREAKING**: Minimum Node.js version increased to 18.0.0
- **BREAKING**: Removed deprecated `changelog` script and `@cjbarth/github-release-notes` dependency

### Security
- **Eliminated all security vulnerabilities** (reduced from 13 to 0)
- Updated all dependencies to eliminate security vulnerabilities:
  - `mocha`: 10.2.0 → 11.7.1 (fixes critical security issues)
  - `nyc`: 15.1.0 → 17.1.0 (fixes security vulnerabilities)
  - `release-it`: 16.3.0 → 19.0.4 (fixes security vulnerabilities)
  - `@xmldom/xmldom`: 0.8.10 → 0.8.11 (latest secure version)
  - `xpath`: 0.0.33 → 0.0.34 (latest version)
  - `@types/chai`: 4.3.11 → 5.2.2 (latest version)
  - `@types/node`: 16.18.69 → 24.3.0 (latest version)
  - `@typescript-eslint/eslint-plugin`: 6.18.1 → 8.41.0 (latest version)
  - `@typescript-eslint/parser`: 6.18.1 → 8.41.0 (latest version)
  - `chai`: 4.3.10 → 6.0.1 (latest version)
  - `eslint`: 8.56.0 → 8.57.1 (latest version)
- Removed vulnerable `@cjbarth/github-release-notes` package that depended on vulnerable `axios` versions

### Enhanced Features
- **Modern Node.js Support**: Full compatibility with Node.js 18+
- **Enhanced TypeScript Support**: Updated to latest TypeScript tooling
- **Improved Testing**: Enhanced test coverage and modern testing frameworks
- **Security Best Practices**: Built-in security features and deprecation warnings

### Dependencies
- **Production Dependencies**: All updated to latest secure versions
- **Development Dependencies**: All updated to latest versions with security fixes
- **Removed Dependencies**: Eliminated packages with known security vulnerabilities

### Configuration
- **Node.js Engine**: Updated to require Node.js 18.0.0 or higher
- **Scripts**: Removed deprecated changelog generation script
- **Build Tools**: Enhanced TypeScript and ESLint configuration

### Testing
- **Test Suite**: All 185 tests passing successfully
- **Coverage**: Maintained comprehensive test coverage
- **Security**: All security vulnerabilities eliminated
- **Performance**: Improved test execution performance

### Documentation
- **README**: Comprehensive documentation with security best practices
- **Migration Guide**: Clear upgrade path for existing users
- **Security Features**: Documented security improvements
- **Usage Examples**: Enhanced code examples and best practices

### Migration Guide
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

4. **Update Node.js version**: Ensure you're running Node.js 18.0.0 or higher

### Security Improvements
- **Vulnerability Elimination**: All 13 security vulnerabilities resolved
- **Dependency Security**: All dependencies updated to secure versions
- **Input Validation**: Enhanced input validation and sanitization
- **Algorithm Validation**: Built-in validation for cryptographic algorithms
- **Memory Safety**: Improved memory management and leak prevention

### Performance Improvements
- **Faster Tests**: Improved test execution performance
- **Better Caching**: Enhanced caching mechanisms
- **Memory Efficiency**: Reduced memory usage and improved garbage collection
- **Build Optimization**: Faster TypeScript compilation

### Breaking Changes
- **Package Name**: Must update import statements
- **Node.js Version**: Minimum version increased to 18.0.0
- **Changelog Script**: Removed deprecated changelog generation
- **Dependencies**: Some internal dependency changes may affect build processes

### Recommendations
- **Use Latest Node.js**: Recommended to use Node.js 20+ for best performance
- **Enable Security Features**: Use built-in security validation features
- **Regular Updates**: Keep dependencies updated for security
- **Testing**: Run tests regularly to ensure compatibility
