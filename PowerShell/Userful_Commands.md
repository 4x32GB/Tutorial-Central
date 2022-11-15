# Useful PowerShell Commands Everyone Should Know

PowerShell is a hefty language that has mountains upon mountains of cmdlets, functions, methods, properties, and many more. Learning how to easily manipulate these features is what seperates a novice PowerShell developer from the expert PowerShell developer.

## CTRL + Space

In PowerShell, we're used to constantly pressing tab after we enter the - after a cmdlet trying to see every possible parameter that is accepted. Usually we continue pressing tab or we search the help files, luckily, there's a easier way, just press ctrl + space and you'll get a list of all possible paramters and you can use your arrows keys to navigate and select. 

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

## Credit

[The Lazy Admin](https://lazyadmin.nl/)
