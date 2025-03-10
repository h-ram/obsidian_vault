A cmdlet is a lightweight command in PowerShell, (specifically designed for PowerShell).
The term "cmdlet" stands for **Command-let**. ("let" meaning small or lightweight )
All cmdlets are built using the .NET framework.

---
### **Naming Convention**
Cmdlets follow a **verb-noun** naming convention (e.g., `Get-Process`, `Set-Item`, `New-Object`), where:
- **Verb** indicates the action (e.g., `Get`, `Set`, `Remove`...etc).
- **Noun** indicates the object or entity the action is performed on (e.g., `Process`, `Item`, `Object`).
The basic syntax of a cmdlet is:
```
Verb-Noun [-Parameter1 Value1] [-Parameter2 Value2] ...
```
---
