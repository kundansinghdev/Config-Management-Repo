
# **🚨 Problem: npm Execution Policy Error**

When running npm commands (e.g., `npm i`), you might encounter this error in PowerShell:

```
npm : File C:\Program Files\nodejs\npm.ps1 cannot be loaded because running scripts is disabled on this system.
For more information, see about_Execution_Policies at https:/go.microsoft.com/fwlink/?LinkID=135170.
```

### ⚠️ **Cause**:
This error occurs because PowerShell has a default execution policy that blocks the running of scripts.

---

## **✅ Solution: Change Execution Policy**

### 1. **🔓 Open PowerShell as Administrator**  
- Press `Win + X` → Select **Windows PowerShell (Admin)**.

### 2. **🔍 Check Current Execution Policy (Optional)**  
Run this command to see your current policy:

```powershell
Get-ExecutionPolicy
```

It will likely be `Restricted` or `AllSigned`.

### 3. **⚙️ Change Execution Policy to Allow Scripts**

Run the following command:

```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```

- **RemoteSigned**: Allows locally created scripts, but requires downloaded ones to be signed.
- **-Scope CurrentUser**: Only affects the current user.

Confirm with **Y** when prompted.

### 4. **✅ Verify the Change (Optional)**

Confirm the execution policy has been updated:

```powershell
Get-ExecutionPolicy
```

It should return `RemoteSigned`.

### 5. **🔄 Run npm Command**

Now, try running your npm command again:

```bash
npm install
```

It should work without the execution policy error.

---

## **🔄 Alternative: Use Command Prompt**

If PowerShell still doesn’t work, you can run the command from the **Command Prompt**:

1. Press `Win + R`, type `cmd`, and press **Enter**.
2. Navigate to your project folder and run:

```bash
npm install
```
