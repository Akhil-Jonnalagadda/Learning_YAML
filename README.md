
---

## **README — YAML Interview Q\&A (Simple Answers)**

### **1. What is YAML?**

YAML stands for **"YAML Ain’t Markup Language"**.
It’s a **human-readable data serialization format** used for configuration files and data exchange.

---

### **2. Why use YAML instead of JSON or XML?**

* Easier to read and write (indentation-based)
* Supports comments (`#`)
* No extra braces `{}` or quotes required
* Widely used in DevOps tools like Kubernetes, Ansible, Docker Compose

---

### **3. File extension for YAML?**

`.yaml` or `.yml` — both are valid.

---

### **4. Basic syntax rules?**

* Use **spaces**, never tabs
* Indentation defines structure (usually 2 spaces)
* Key-value format: `key: value`
* Case-sensitive
* Comments start with `#`

---

### **5. Data types in YAML?**

* **String**: `"Hello"` or `Hello`
* **Number**: `25`, `3.14`
* **Boolean**: `true`, `false`
* **Null**: `null` or `~`
* **List (Sequence)**:

  ```yaml
  fruits:
    - apple
    - banana
  ```
* **Dictionary (Mapping)**:

  ```yaml
  person:
    name: Akhil
    age: 25
  ```

---

### **6. Multi-line strings in YAML?**

* **Literal (`|`)** → keeps newlines
* **Folded (`>`)** → folds into one line

```yaml
literal: |
  Line1
  Line2
folded: >
  This becomes a single line.
```

---

### **7. What are anchors and aliases in YAML?**

* **Anchor (`&`)** defines reusable content
* **Alias (`*`)** reuses it
* **Merge (`<<`)** copies mapping values

```yaml
defaults: &default
  retries: 3
  timeout: 30

service1:
  <<: *default
  name: auth
```

---

### **8. How to represent environment variables in YAML?**

```yaml
database:
  host: ${DB_HOST}
  user: ${DB_USER}
```

*(Support depends on the tool — Kubernetes, Docker Compose, etc.)*

---

### **9. How to start and end a YAML document?**

* Start: `---`
* End: `...` (optional)

```yaml
---
key: value
...
```

---

### **10. YAML vs JSON (key differences)?**

| Feature     | YAML        | JSON              |
| ----------- | ----------- | ----------------- |
| Readability | Easy        | Harder            |
| Comments    | ✅ Yes       | ❌ No              |
| Syntax      | Indentation | Braces & brackets |
| File size   | Smaller     | Larger            |

---

### **11. Common YAML errors?**

* Using **tabs** instead of spaces
* Wrong indentation
* Mixing list and dictionary at the same level
* Forgetting quotes for strings starting with `:`, `-`, `?`, or `#`

---

### **12. Where is YAML used in DevOps?**

* **Kubernetes**: Pod/Deployment definitions
* **Ansible**: Playbooks
* **Docker Compose**: Multi-container configs
* **GitHub Actions**: Workflow files

---

### **13. How to validate a YAML file?**

* Online validator: yamlvalidator.com
* CLI:

```bash
yamllint file.yaml
```

* Python:

```python
import yaml
yaml.safe_load(open('file.yaml'))
```

---

### **14. How to write multiple YAML documents in one file?**

```yaml
---
name: Akhil
---
name: Ravi
```

---

### **15. What is the difference between `|` and `>` in YAML?**

* `|` → preserves newlines exactly
* `>` → folds newlines into spaces

---

### **16. How to write a list of dictionaries in YAML?**

```yaml
users:
  - name: Akhil
    role: DevOps
  - name: Ravi
    role: Developer
```

---

### **17. How to represent null values in YAML?**

```yaml
value1: null
value2: ~
```

---

### **18. What is the merge key (`<<`) in YAML?**

It copies mapping values from another key or alias.

```yaml
defaults: &def
  retries: 3
  timeout: 30

service:
  <<: *def
  name: auth
```

---

### **19. Does YAML support comments?**

Yes, starting with `#`.

```yaml
# This is a comment
name: Akhil
```

---

### **20. How to check if a YAML file is valid before running it in Kubernetes/Docker?**

```bash
kubectl apply -f file.yaml --dry-run=client
docker compose config
```

---


