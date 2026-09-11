# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2026-09-11

### ✨ Added - Initial Release

#### Features
- **Philippines-Only Customer JSON Schema** - First official release
- **Country Code Enforcement** - Enforces `countryCode = PH` for all customer records
- **Phone Number Validation** - Phone numbers must start with `+63` (Philippines country code)
- **Postal Code Validation** - Postal codes must be exactly 4 digits
- **Language Requirement** - Language field must be set to `"Pilipino"` (Filipino)

#### Documentation
- Comprehensive Certificate Transparency (CT) policies
- Chrome CT Policy documentation
- CT Log Policy and requirements
- CT Log Lifecycle and states documentation
- Enterprise Certificate Transparency guide
- Site operators guide
- Contribution guidelines

#### Technical Assets
- JSON Schema for CT log inclusion requests
- Merge Delay Monitor Root certificate
- Jekyll configuration for documentation site
- HTML layouts and CSS styling
- Apache 2.0 License

### 📋 Schema Specifications

**Customer Record Structure:**
```json
{
  "countryCode": "PH",
  "phoneNumber": "+63XXXXXXXXX",
  "postalCode": "1234",
  "language": "Pilipino"
}
```

**Validation Rules:**
- `countryCode`: Must exactly equal "PH"
- `phoneNumber`: Must match pattern `^\+63\d+$`
- `postalCode`: Must match pattern `^\d{4}$`
- `language`: Must exactly equal "Pilipino"

### 🔗 Resources

- [Certificate Transparency Overview](https://certificate.transparency.dev/)
- [RFC 6962 - CT Protocol](https://tools.ietf.org/html/rfc6962)
- [Static CT API v1.0.0](https://c2sp.org/static-ct-api)
- [Chrome CT Policy](ct_policy.md)
- [CT Log Policy](log_policy.md)

### 👥 Contributors

- Jose Protascio Mercado Carreon (@peperizal1133-afk)

---

**Note:** This is the first official release of the Philippines Customer Schema. All subsequent versions will follow semantic versioning principles.
