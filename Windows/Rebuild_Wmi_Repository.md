# Rebuilding the WMI Repository

Due to either user or a system error, there may come a time where you try to call a class within the Wmi repository, but it fails with a message such as the one below:

```powershell
ERROR: Get-WmiObject : Invalid class "Win32_UserProfile"
```

Luckily the steps to rebuild the repository are actually fairly straight-forward and no damage to the system has occured.

## Resolution Steps

1. Pause and stop the Windows Management Instrumentation service

    * Service Name: Winmgmt
    * Display Name: Windows Management Instrumentation
    * Startup Type: Automatic

2. Navigate to the following path *C:\Windows\System32\wbem* and _.OLD_ the directory *Repository*

3. Start the Windows Management Instrumentation service

4. You should see the repository folder reappear with the same files within it

5. Attempt to run the same command that displayed an error