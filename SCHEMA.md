# Philippines Customer Schema v1.0.0

## Overview

The Philippines Customer Schema (v1.0.0) is a JSON Schema specification designed specifically for validating customer records in the Philippines market. It enforces strict validation rules to ensure data consistency and compliance with Philippine standards.

## Schema Definition

### Basic Structure

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "type": "object",
  "title": "Philippines Customer Schema v1.0.0",
  "description": "JSON Schema for Philippines-only customer records",
  "required": ["countryCode", "phoneNumber", "postalCode", "language"],
  "properties": {
    "countryCode": {
      "type": "string",
      "description": "Country code must be Philippines (PH)",
      "enum": ["PH"],
      "example": "PH"
    },
    "phoneNumber": {
      "type": "string",
      "description": "Philippines phone number starting with +63",
      "pattern": "^\\+63[0-9]{7,11}$",
      "example": "+63912345678"
    },
    "postalCode": {
      "type": "string",
      "description": "Philippine postal code (4 digits)",
      "pattern": "^[0-9]{4}$",
      "example": "1234"
    },
    "language": {
      "type": "string",
      "description": "Language must be Pilipino",
      "enum": ["Pilipino"],
      "example": "Pilipino"
    }
  }
}
```

## Validation Rules

### 1. Country Code (`countryCode`)
- **Type**: String
- **Required**: Yes
- **Valid Values**: `"PH"` only
- **Description**: Enforces Philippines-only records
- **Example**: `"PH"`

### 2. Phone Number (`phoneNumber`)
- **Type**: String
- **Required**: Yes
- **Pattern**: `^\\+63[0-9]{7,11}$`
- **Description**: Must start with country code `+63`
- **Format**: +63 followed by 7-11 digits
- **Valid Examples**:
  - `"+63912345678"`
  - `"+639123456789"`
  - `"+6391234567"`

### 3. Postal Code (`postalCode`)
- **Type**: String
- **Required**: Yes
- **Pattern**: `^[0-9]{4}$`
- **Description**: Must be exactly 4 digits
- **Valid Examples**:
  - `"1200"` (Metro Manila)
  - `"1000"` (Rizal)
  - `"6000"` (Cebu)

### 4. Language (`language`)
- **Type**: String
- **Required**: Yes
- **Valid Values**: `"Pilipino"` only
- **Description**: Language preference or display language
- **Example**: `"Pilipino"`

## Usage Examples

### ✅ Valid Customer Record

```json
{
  "countryCode": "PH",
  "phoneNumber": "+639175551234",
  "postalCode": "1200",
  "language": "Pilipino"
}
```

### ❌ Invalid Examples

**Invalid Country Code:**
```json
{
  "countryCode": "US",
  "phoneNumber": "+639175551234",
  "postalCode": "1200",
  "language": "Pilipino"
}
// Error: countryCode must be "PH"
```

**Invalid Phone Number Format:**
```json
{
  "countryCode": "PH",
  "phoneNumber": "+1912345678",
  "postalCode": "1200",
  "language": "Pilipino"
}
// Error: phoneNumber must start with +63
```

**Invalid Postal Code:**
```json
{
  "countryCode": "PH",
  "phoneNumber": "+639175551234",
  "postalCode": "120000",
  "language": "Pilipino"
}
// Error: postalCode must be exactly 4 digits
```

**Invalid Language:**
```json
{
  "countryCode": "PH",
  "phoneNumber": "+639175551234",
  "postalCode": "1200",
  "language": "English"
}
// Error: language must be "Pilipino"
```

## Integration

### Using the Schema in Your Application

**JSON Schema Validation (JavaScript):**
```javascript
const Ajv = require('ajv');
const ajv = new Ajv();

const schema = require('./ph-customer-schema.json');
const validate = ajv.compile(schema);

const customer = {
  countryCode: "PH",
  phoneNumber: "+639175551234",
  postalCode: "1200",
  language: "Pilipino"
};

const valid = validate(customer);
if (!valid) {
  console.log(validate.errors);
}
```

**Python:**
```python
import json
import jsonschema

schema = json.load(open('ph-customer-schema.json'))

customer = {
    "countryCode": "PH",
    "phoneNumber": "+639175551234",
    "postalCode": "1200",
    "language": "Pilipino"
}

try:
    jsonschema.validate(customer, schema)
    print("Valid customer record")
except jsonschema.ValidationError as e:
    print(f"Validation error: {e.message}")
```

## Philippine Context

### About Philippines Phone Numbers
- **Country Code**: +63
- **Area Codes**: Various regional codes
- **Format**: +63 9XX XXXX XXX (typical mobile format)
- **Common Carriers**: Globe, Smart, Dito, Sun Cellular

### About Philippine Postal Codes
- **Structure**: 4-digit system
- **Format**: PXXX (or XXXX where P is region digit)
- **Examples**:
  - Metro Manila: 1000-1299
  - Calabarzon: 4000-4900
  - Visayas: 5000-6299
  - Mindanao: 8000-9300

### About Philippine Language
- **Official Language**: Filipino (Tagalog-based)
- **Local Name**: Pilipino
- **Usage**: Widely spoken across the Philippines
- **Context**: This schema enforces "Pilipino" as the language preference

## Compliance

This schema follows:
- **JSON Schema Draft-07** specification
- **Semantic Versioning** (v1.0.0)
- **Apache License 2.0**

## Support

For issues, questions, or contributions, please refer to:
- [Contributing Guidelines](CONTRIBUTING.md)
- [GitHub Issues](https://github.com/peperizal1133-afk/Philippines-Customer-Schema-v1.0.0/issues)
- [ct-policy@chromium.org](https://groups.google.com/a/chromium.org/forum/#!forum/ct-policy)

## Version History

- **v1.0.0** (2026-09-11) - Initial release with Philippines-specific validation rules

---

**Last Updated**: 2026-09-11  
**Schema Version**: 1.0.0  
**License**: Apache License 2.0
