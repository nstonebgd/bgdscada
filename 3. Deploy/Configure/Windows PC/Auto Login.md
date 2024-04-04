# Windows PowerShell Guide for Auto-Login Setup

This guide details how to configure an automatic login for a user account on Windows 10 and Windows 11 using Windows PowerShell.

## Steps for Setting Up Auto-Login

### 1. Open PowerShell as Administrator

- Right-click on the Start menu.
- Choose `Windows PowerShell (Admin)`.

### 2. Check Current Auto-Login Configuration

- To check if auto-login is already configured, run:

  ```powershell
  Get-ItemProperty -Path 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon'
  ```

### 3. Set Auto-Login Registry Keys

- Replace `YourUsername` with your actual username and `YourPassword` with your actual password.

- Execute the following commands:

  ```powershell
  Set-ItemProperty -Path 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon' -Name 'AutoAdminLogon' -Value '1'
  Set-ItemProperty -Path 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon' -Name 'DefaultUsername' -Value 'YourUsername'
  Set-ItemProperty -Path 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon' -Name 'DefaultPassword' -Value 'YourPassword'
  ```

### 4. Verify Auto-Login Setup

- To confirm the settings are correctly applied, re-run the check command:

  ```powershell
  Get-ItemProperty -Path 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon'
  ```

### 5. Restart Your Computer

- After setting these registry keys, restart your computer.
- The system should now auto-login to the specified account.

## Disable Auto-Login

If you need to disable auto-login in the future, follow these steps:

- Open PowerShell as Administrator.

- Run the following command:

  ```powershell
  Set-ItemProperty -Path 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon' -Name 'AutoAdminLogon' -Value '0'
  ```

------

## Additional Notes

- This method works for both Windows 10 and Windows 11.
- Remember that using auto-login can pose a security risk, especially on shared or easily accessible computers.
- Always ensure you have a backup of your registry before making changes.