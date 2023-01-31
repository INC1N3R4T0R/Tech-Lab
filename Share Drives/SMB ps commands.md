<h3>+ SMB Shares with Powershell</h3>

---
- Check SMB SHARES

    >Get-SmbShare
    >Get-SmbShare -Name "foldername"

- Generate SMB Share

  >$Parameters = @{
    Name = 'foldername'
    Path = 'Local shared folder path'
    FullAccess = 'Domain Name\Groupname', 'Domain Name\Groupname'
   }
   New-SmbShare @Parameters

- Remove SMB Share (Always use this as it gives warning)
 
  >Remove-SmbShare -Name "foldername"

- Check SMB ACL entire

    >(get-acl '\\Servername\foldername').access

- Map share to local (In users account)

  >New-SmbMapping -LocalPath 'X:' -RemotePath '\\Servername\foldername'

- Remove local share (In users account)

  >Remove-smbmapping -LocalPath 'X:'

-------------------------------------------
