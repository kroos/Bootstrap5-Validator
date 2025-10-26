
# 🧩 Bootstrap Validator (Revived for Bootstrap 5)

> A modernized, fully working version of the original **BootstrapValidator.js**
> (originally built for Bootstrap 3 by @nghuuphuoc), now updated and refactored
> to work seamlessly with **Bootstrap 5.3+** — while still remaining compatible
> with legacy Bootstrap 3 markup.

---

## 🚀 Introduction

The original **BootstrapValidator** plugin was one of the most powerful jQuery-based
form validation libraries for Bootstrap 3. Unfortunately, it was deprecated years ago
and replaced by **FormValidation.io**, a paid commercial successor. The open-source
documentation and examples eventually disappeared.

This repository brings it **back to life**, enhanced for **modern web projects**.
It is a **plain-text, human-readable JavaScript version** that:

- ✅ Works with **Bootstrap 5.3+**, **Bootstrap 4**, and **Bootstrap 3**
- ✅ Keeps all the **original built-in validators** (25+ types)
- ✅ Adds Bootstrap 5-style feedback classes (`.is-valid` / `.is-invalid`)
- ✅ Retains legacy `.has-success` / `.has-error` for backward compatibility
- ✅ Moves validation icons **inside** the feedback message for cleaner markup
- ✅ Uses modern `.invalid-feedback` / `.valid-feedback` blocks (no `.help-block`)
- ✅ Remains simple, unminified, and easy to maintain for future Bootstrap updates

---

## 📦 Why This Version?

Most existing validation plugins either:
- require complex setups (FormValidation.io, Parsley.js), or
- dropped Bootstrap-specific integration entirely.

This version provides a **drop-in, backward-compatible** replacement for
developers still using Bootstrap’s form layout — now modernized and simplified.

It’s ideal for:
- legacy projects being upgraded from Bootstrap 3 → 5
- Laravel + Bootstrap form systems
- environments where simplicity and readability matter

---

## 🧰 Key Features

| Feature | Description |
|----------|-------------|
| 🎯 Full Bootstrap 5 support | Adds `.is-valid` / `.is-invalid` automatically |
| 🔁 Backward compatibility | Keeps `.has-error` / `.has-success` for old forms |
| 🧩 25+ validators built-in | Email, regex, dates, numbers, IP, MAC, etc. |
| 💡 Custom validators | Easily extend using `BootstrapValidator.validators.*` |
| ⚡ Live & server validation | Supports live input events and AJAX (`remote`) |
| 🧾 Plain, readable code | No build tools or minifiers required |
| 🛠️ Self-documented | In-file comments and Markdown manuals included |

---

## 📘 Documentation

This repository includes:

- **bootstrapValidator.js** → The main hybrid plugin


---

## 🧱 Example Integration

```html
<form id="loginForm">
  <div class="form-group row">
    <label class="col-sm-3 col-form-label">Username</label>
    <div class="col-sm-6">
      <input type="text" class="form-control" name="username" placeholder="Username">
    </div>
  </div>

  <div class="form-group row">
    <label class="col-sm-3 col-form-label">Password</label>
    <div class="col-sm-6">
      <input type="password" class="form-control" name="password" placeholder="Password">
    </div>
  </div>

  <button type="submit" class="btn btn-primary">Login</button>
</form>

<script>
$('#loginForm').bootstrapValidator({
  fields: {
    username: {
      validators: {
        notEmpty: { message: 'Please insert username' }
      }
    },
    password: {
      validators: {
        notEmpty: { message: 'Please insert password' }
      }
    }
  }
});
</script>
```

---

🧾 License

MIT License — the same as the original BootstrapValidator.

You are free to use, modify, and redistribute this plugin, provided that
the original attribution (Nguyen Huu Phuoc, 2014–2015) and this updated
version’s credits remain intact.

💬 Credits

Original author: Nguyen Huu Phuoc (@nghuuphuoc)

Hybrid rewrite & Bootstrap 5 update: [Your Name] (2025)

Based on BootstrapValidator v0.5.x source with modern compatibility patches

Note: This version is not affiliated with FormValidation.io — it’s an
independent, revived, open-source continuation for community use.

---
## 🔩 Common Configuration Options for Validators

| Option | Description | Example |
|---------|--------------|----------|
| `message` | Error message to display if validation fails | `'This field is required'` |
| `enabled` | Enable or disable a validator dynamically | `true` or `false` |
| `threshold` | Number of characters to wait before validating | `threshold: 5` |
| `trigger` | Validation event(s) (e.g., `keyup`, `blur`) | `'keyup'` or `'blur'` |

---

## 🧱 Built-In Validators (Full List)

### 1️⃣ notEmpty
Ensures the field is not empty.

```js
notEmpty: {
  message: 'This field is required'
}
```

### 2️⃣ stringLength
Checks min and max character count.

```js
stringLength: {
  min: 6,
  max: 30,
  message: 'Must be between 6 and 30 characters'
}
```

### 3️⃣ regexp
Validates using a regular expression.

```js
regexp: {
  regexp: /^[a-zA-Z0-9_]+$/,
  message: 'Letters, numbers and underscores only'
}
```

### 4️⃣ emailAddress
Validates email format.

```js
emailAddress: {
  message: 'Invalid email address'
}
```

### 5️⃣ identical
Matches another field’s value.

```js
identical: {
  field: 'password',
  message: 'Passwords must match'
}
```

### 6️⃣ different
Ensures different value from another field.

```js
different: {
  field: 'username',
  message: 'Must not match username'
}
```

### 7️⃣ digits
Digits only.

```js
digits: { message: 'Digits only' }
```

### 8️⃣ integer
Valid integer (optional +/- sign).

```js
integer: { message: 'Enter a valid integer' }
```

### 9️⃣ numeric
Allows integers or decimals.

```js
numeric: { message: 'Enter a valid number' }
```

### 🔟 greaterThan
Greater than comparison.

```js
greaterThan: {
  value: 18,
  message: 'Must be 18 or older'
}
```

### 11️⃣ lessThan
Less than comparison.

```js
lessThan: {
  value: 100,
  message: 'Must be less than or equal to 100'
}
```

### 12️⃣ between
Range check.

```js
between: {
  min: 1,
  max: 10,
  message: 'Between 1 and 10 only'
}
```

### 13️⃣ date
Checks valid date.

```js
date: {
  format: 'YYYY-MM-DD',
  message: 'Date is not valid'
}
```

### 14️⃣ creditCard
Validates credit card via Luhn algorithm.

```js
creditCard: { message: 'Invalid card number' }
```

### 15️⃣ phone
Phone number validation (country-based).

```js
phone: {
  country: 'US',
  message: 'Invalid phone number'
}
```

### 16️⃣ zipCode
Postal/ZIP validation.

```js
zipCode: {
  country: 'US',
  message: 'Invalid ZIP code'
}
```

### 17️⃣ choice
Checks min/max checkbox/radio selections.

```js
choice: {
  min: 1,
  max: 3,
  message: 'Select between 1 and 3 options'
}
```

### 18️⃣ remote
AJAX server validation.

```js
remote: {
  url: '/api/check',
  type: 'POST',
  message: 'Invalid data'
}
```

### 19️⃣ callback
Custom JavaScript validation logic.

```js
callback: {
  message: 'Custom validation failed',
  callback: function(value) {
    return value !== 'admin';
  }
}
```

### 20️⃣ file
Validates file inputs (extension, type, size).

```js
file: {
  extension: 'jpg,png',
  type: 'image/jpeg,image/png',
  maxSize: 2097152,
  message: 'Only JPG/PNG files under 2MB'
}
```

### 21️⃣ uri
Validates URLs.

```js
uri: { message: 'Invalid URL' }
```

### 22️⃣ ip
Validates IPv4/IPv6.

```js
ip: { message: 'Invalid IP address' }
```

### 23️⃣ mac
Validates MAC address format.

```js
mac: { message: 'Invalid MAC address' }
```

### 24️⃣ hexColor
Validates hex color.

```js
hexColor: { message: 'Invalid hex color' }
```

### 25️⃣ base64
Validates Base64 string.

```js
base64: { message: 'Invalid Base64 data' }
```

---

## 🧠 Custom Validator Example

```js
BootstrapValidator.validators.containsWord = {
  validate: function(validator, $field, options) {
    var value = $field.val();
    return value && value.includes(options.word);
  }
};

$('#form').bootstrapValidator({
  fields: {
    comment: {
      validators: {
        containsWord: {
          word: 'Laravel',
          message: 'Your comment must include "Laravel"'
        }
      }
    }
  }
});
```

---

## 🧾 Summary Table

| Validator | Description |
|------------|-------------|
| notEmpty | Field cannot be empty |
| stringLength | Validates length |
| regexp | Matches regex |
| emailAddress | Email format |
| identical | Match another field |
| different | Must differ from another field |
| digits | Digits only |
| integer | Integer only |
| numeric | Integer or decimal |
| greaterThan | Greater than comparison |
| lessThan | Less than comparison |
| between | Range check |
| date | Valid date |
| creditCard | Credit card number |
| phone | Phone number |
| zipCode | Postal code |
| choice | Checkbox/radio count |
| remote | AJAX validation |
| callback | Custom JS validation |
| file | File validation |
| uri | URL validation |
| ip | IP address |
| mac | MAC address |
| hexColor | Hex color |
| base64 | Base64 string |
