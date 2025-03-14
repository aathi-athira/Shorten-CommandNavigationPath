# Shorten-CommandNavigationPath
How to shorten the long navigation path in your terminal by customizing your shell prompt. 

## 🎨 Step 1: Create or Edit Your PowerShell Profile

### 1. Open PowerShell
- Press **Win + X** and select **Windows PowerShell** or **Terminal (PowerShell tab)**.

### 2. Check if a Profile Exists
Run the following command to check if you already have a profile:
```powershell
Test-Path $PROFILE
```
- **True**: A profile already exists.
- **False**: You need to create a new one.

### 3. Create a New Profile (if Needed)
If the profile does not exist, create it using this command:
```powershell
New-Item -Path $PROFILE -ItemType File -Force
```

### 4. Open the Profile for Editing
Edit the profile using Notepad:
```powershell
notepad $PROFILE
```
The file will be located at:
```
C:\Users\<YourUsername>\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
```

---

## 🚀 Step 2: Customize the Prompt

### 1. Add a Custom Prompt
In the opened profile file (`Microsoft.PowerShell_profile.ps1`), paste the following code:
```powershell
function prompt {
    $currentFolder = Split-Path -Leaf (Get-Location)
    "PS $currentFolder> "
}
```

### 2. Save and Close the File

### 3. Reload the Profile
Apply the changes by reloading your profile:
```powershell
. $PROFILE
```

✅ **Result:** Your PowerShell prompt will now show only the current folder name, like this:
```
PS MyProject>
```
instead of the full path:
```
PS C:\Users\YourUsername\Documents\MyProject>
```

