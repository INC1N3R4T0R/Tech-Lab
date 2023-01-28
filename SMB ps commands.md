<h3>+ SMB Shares with Powershell</h3>

---
- Check SMB SHARES

    >Get-SmbShare
    >Get-SmbShare -Name "foldername"

- Generate SMB Share

  >$Parameters = @{
    Name = 'scriptedFolder'
    Path = 'C:\Shares\Test'
    FullAccess = 'ECORP\Administrator', 'ECORP\Tech Support'
   }
   New-SmbShare @Parameters

- Remove SMB Share (Always use this as it gives warning)
 
  >Remove-SmbShare -Name "scriptedFolder"

- Check SMB ACL entire

    >(get-acl '\\ECORP-ADDS\supportTeam').access

- Map share to local (In users account)

  >New-SmbMapping -LocalPath 'X:' -RemotePath '\\ECORP-ADDS\generalfolder'

- Remove local share (In users account)

  >Remove-smbmapping -LocalPath 'X:'

-------------------------------------------
