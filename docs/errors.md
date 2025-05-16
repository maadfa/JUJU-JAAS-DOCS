# ❌ Common Juju & JAAS Errors

This page explains the most frequent errors you may face when using **Juju** or **JAAS**, why they happen, and how to fix them—along with example commands.

---

## 🚫 1. ERROR: Cannot connect to API server

**Reason**: The Juju controller is not reachable.

### ✅ Solution:
- Make sure the controller is bootstrapped and running.
- Check your internet connection and firewall settings.

### 🔧 Example:
```bash
juju bootstrap localhost my-controller
juju status
```