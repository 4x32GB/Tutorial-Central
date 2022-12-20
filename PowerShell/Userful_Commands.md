# Useful PowerShell Commands Everyone Should Know

PowerShell is a hefty language that has mountains upon mountains of cmdlets, functions, methods, properties, and many more. Learning how to easily manipulate these features is what separates a novice PowerShell developer from the expert PowerShell developer.

## CTRL + Space

In PowerShell, we're used to constantly pressing tab after we enter the - after a cmdlet trying to see every possible parameter that is accepted. Usually we continue pressing tab or we search the help files, luckily, there's a easier way, just press ctrl + space and you'll get a list of all possible parameters and you can use your arrows keys to navigate and select. 

```PowerShell
  E:\DEV\PowerShell   Get-EXOMailbox -Anr
  Anr                        PublicFolder               ErrorAction
  Filter                     GroupMailbox               WarningAction
  OrganizationalUnit         Migration                  InformationAction
  Properties                 Async                      ErrorVariable
  PropertySets               Identity                   WarningVariable
  SoftDeletedMailbox         ExternalDirectoryObjectId  InformationVariable
  InactiveMailboxOnly        UserPrincipalName          OutVariable
  Archive                    PrimarySmtpAddress         OutBuffer
  IncludeInactiveMailbox     ResultSize                 PipelineVariable
  MailboxPlan                Verbose
  RecipientTypeDetails       Debug

  [string] Anr
```

## Enter-PSSession

If you're used to remoting onto a server to change a setting or configure Active Directory, there is an easier way. Although you can access AD remotely utilizing the AD module, what Enter-PSSession is useful for is running PowerShell commands on that server specifically, instead of running commands against it. Take note that if you utilize an admin username instead of your normal login, you'll want to utilize the -Credential parameter to specify the credentials to be used to login.

```PowerShell
  # Without credential parameter
  Enter-PSSession -ComputerName DJX1230KE

  # Result (Example)
  # [DJX1230KE]: PS C:\>

  # If you need to specify credentials
  Enter-PSSession -ComputerName DJX1230KE -Credential <username>
```

## Credit

[The Lazy Admin](https://lazyadmin.nl/)
