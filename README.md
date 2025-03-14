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

# PowerShell Prompt Customization & Restoration Guide

##  1. Temporarily Restore the Default Prompt

If you want to reset the prompt to show the full path just for the current session, run this command:

```powershell
function prompt { "PS $($pwd.Path)> " }
```

✅ **Result:**  
Your prompt will now display the full path like this:

```
PS C:\Users\YourUsername\Documents\MyProject>
```

This change will **disappear** once you close PowerShell.

---

##  2. Permanently Restore the Default Prompt

If you want the full path to always show:

### 1. Open your PowerShell profile:

```powershell
notepad $PROFILE
```

This will open a file like:

```
C:\Users\<YourUsername>\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
```

### 3. Add the default full path prompt:

```powershell
function prompt { "PS $($pwd.Path)> " }
```

### 4. Save the file and reload your profile:

```powershell
. $PROFILE
```

✅ **Result:** The prompt will always show the full path like:

```
PS C:\Users\YourUsername\Documents\MyProject>
```

---

## 🔀 Add a Toggle Between Short and Full Paths

For flexibility, you can create two commands to switch between short and full paths on demand.

### 1. Open your profile:

```powershell
notepad $PROFILE
```

### 2. Add these toggle functions:

```powershell
# Short path prompt (shows only the current folder)
function ShortPathPrompt {
    function prompt {
        $currentFolder = Split-Path -Leaf (Get-Location)
        "PS $currentFolder> "
    }
}

# Full path prompt (shows the entire path)
function FullPathPrompt {
    function prompt {
        "PS $($pwd.Path)> "
    }
}
```

### 3. Save and reload the profile:

```powershell
. $PROFILE
```

### 4. Switch between prompts using these commands:

- **Short path:**
```powershell
ShortPathPrompt
```

- **Full path:**
```powershell
FullPathPrompt
```

✅ **Example:**  
- **Short path:**  
```
PS MyProject>
```
- **Full path:**  
```
PS C:\Users\YourUsername\Documents\MyProject>
```

---

