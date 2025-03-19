# AD Scans
One-liners to get information from Active Directory environments
# PowerShell
- Dump usernames to file
  - ```
    Get-ADUser -Filter * | Format-Table SamAccountName >> AD.list
    ```
