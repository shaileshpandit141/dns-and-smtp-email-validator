# 📧 DNS and SMTP Email Validator

**DNS and SMTP Email Validator** is a robust Python library designed to validate email addresses at multiple levels. It checks the format, domain, and MX records, and even communicates with the mail server to confirm the existence of the recipient's email address.

---

## 🚀 Features

- **Email Format Validation**: Ensure the email address matches a valid format.
- **Domain Validation**: Validate email domains against a customizable allowlist.
- **MX Record Lookup**: Check for valid mail exchange (MX) records for the domain.
- **SMTP Communication**: Optionally verify the existence of the recipient email address via the SMTP protocol.
- **Customizable Error Handling**: Choose to raise exceptions or store errors for later inspection.

---

## 🔧 Installation

Install the package via pip:

```bash
pip install dns-smtp-email-validator
```

---

## 🛠️ Usage

### **Basic Example**

```python
from dns_smtp_email_validator import DNSSMTPEmailValidator

# Instantiate the validator
validator = DNSSMTPEmailValidator(email="test@example.com")

# Validate the email
if validator.is_valid():
    print("✅ Email is valid!")
else:
    print("❌ Invalid email!")
    print("Errors:", validator.errors)
```

### **Custom Sender Email and Error Handling**

```python
validator = DNSSMTPEmailValidator(
    email="test@example.com",
    sender_email="mycustomsender@domain.com",
    raise_exception=True
)

if validator.is_valid():
    print("✅ Email is valid!")
else:
    print("❌ Email validation failed!")
```

---

## ⚙️ Configuration

You can configure allowed email domains through environment variables. Use a `.env` file or system-level configuration.

### **Example `.env` File**

```env
ALLOWED_EMAIL_DOMAINS=gmail.com,yahoo.com,outlook.com
```

### **Default Allowed Domains**

If `ALLOWED_EMAIL_DOMAINS` is not provided, the library uses the following defaults:

```
ALLOWED_EMAIL_DOMAINS = [
    "aol.com",
    "gmail.com",
    "hotmail.com",
    "icloud.com",
    "outlook.com",
    "yahoo.com",
    "zoho.com"
]
```

---

## ✅ Validation Workflow

1. **Email Format Check**:
   Confirms the email follows standard formatting rules (e.g., `user@domain.com`).

2. **Domain Allowlist Check**:
   Validates that the email domain is in the allowed list.

3. **MX Record Lookup**:
   Retrieves the mail exchange (MX) records for the email domain.

4. **SMTP Communication** *(Optional)*:
   Connects to the mail server and verifies the recipient's address.

---

## 🧪 Running Tests

To ensure the library is working correctly, run the test suite:

```bash
pytest tests/
```

---

## 🛡️ Error Handling

The library offers two approaches to handle errors:

1. **Raise Exceptions**: Enable `raise_exception=True` to raise exceptions for validation errors.
2. **Collect Errors**: Store errors in the `errors` attribute for later inspection.

---

## 🏗️ Contributing

Contributions are welcome! If you'd like to enhance the functionality or fix an issue, feel free to open a pull request.

### **Steps to Contribute**:
1. Fork the repository.
2. Create a feature branch.
3. Commit your changes.
4. Submit a pull request.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

## 📞 Support

For any issues or feature requests, please [open an issue](https://github.com/shaileshpandit141/dns-smtp-email-validator.git/issues).

---

Happy Validating! 🎉
