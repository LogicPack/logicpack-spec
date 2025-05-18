# LogicPack Specification

**LogicPack** is a portable, declarative format to define and execute business logic, decisions, and rules — outside of code.

This repository defines the **official structure, schema, and philosophy** of LogicPack.

## ✅ Why LogicPack?

* Human-readable (YAML / JSON)
* Declarative & portable
* Works across languages
* Testable with examples
* Editable by non-devs

## 📦 Folder Structure

* `spec.md` – Format structure and design philosophy
* `schema.yaml` – Formal schema for validation and tooling
* `examples/` – Real-world reference LogicPacks
* `tests/` – Test cases to validate runner implementations

## 🔍 Examples

### 1. Discount Rule

```yaml
inputs: [user_type, purchase_amount]

logic:
  if: "user_type == 'vip' and purchase_amount > 1000"
  then: "return 'discount-20%'"
  else: "return 'no-discount'"

examples:
  - input: {user_type: "vip", purchase_amount: 1200}
    output: "discount-20%"
  - input: {user_type: "guest", purchase_amount: 900}
    output: "no-discount"
```

### 2. Access Control

```yaml
inputs: [role, region]

logic:
  if: "role == 'admin'"
  then: "return 'allow'"
  elif: "role == 'staff' and region == 'EU'"
  then: "return 'allow'"
  else: "return 'deny'"

examples:
  - input: {role: "admin", region: "US"}
    output: "allow"
  - input: {role: "staff", region: "EU"}
    output: "allow"
  - input: {role: "staff", region: "ASIA"}
    output: "deny"
```

## 🧠 LogicPack Format Summary

```yaml
name: string
inputs: [var1, var2, ...]
vars: { key: expression }
logic: { if / then / elif / else }
examples: [ {input/output} ]
```

## 📄 Spec Highlights

* **Inputs**: Variables expected from outside
* **Vars**: Computed intermediate values (optional)
* **Logic**: Core decision tree using simple expressions
* **Examples**: Input/output test cases for clarity and validation

## 🌍 Learn More

Website: [https://logicpack.org](https://logicpack.org)
