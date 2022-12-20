# Adding Default Credentials to Profile

PowerShell has many cmdlets and functions that have parameters with default values and this value can be easily manipulated. One of the most annoying parameters that I come across is the -Credential parameter since every time I need to perform an action on a property a credential is always needed. Why not just have a default credential that's always used so you never have to specify?

```powershell
$variable = Get-Credential -UserName "Your Username" -Message "Enter your admin password"
$PSDefaultParameterValues.Add("*:Credential",$variable)
```