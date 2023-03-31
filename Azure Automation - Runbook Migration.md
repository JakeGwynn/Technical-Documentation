# Azure Automation Account - PowerShell Runbook Guidance
#### This guidance can be used to help update PowerShell scripts that were traditionally run on-premises or from a local machine.

## Why Azure Automation?
Azure Automation is an Azure service that allows PowerShell (and Python) scripts to be run from a cloud Azure subscription. This removes the dependency on a "scripting"
or "utility" server where PowerShell scripts are most often run from at large organizations. 

## Automation Accounts
An Azure Automation Account is a container for Runbooks, which are individuals scripts. Runbooks within an Azure Automation Account can share stored credentials,
certificates, variables, schedules, modules, and a managed identity. 

### Runbooks
Runbooks are the actual scripts that contain your PowerShell code.

## Creating Runbooks
### Runbook type
I recommend choosing "PowerShell" as the Runbook type. "PowerShell Workflow" can be used if parallel processing is needed within foreach statements. 

### Runbook version
I recommend choosing "5.1" as the Runtime version because some of the M365 scripting modules are not yet compatible with PowerShell 7.x.

### Webhooks
Webhooks allow a Runbook to be triggered through an HTTP request sent to a special URL that is generated when the Webhook is created. This allows the Runbook to be run
on an ad-hoc basis.

### Publishing
Azure Runbooks must be published before they can be run using a schedule, webhook, or the "start" button. When a script is being edited, the 'Authoring Status' property of the runbook switches to "In edit", and the script can not be run until it is published again (except for in the Test pane).

### Queueing
When a script is run, it will initially be "queued", and it will stay in that state until Azure has allocated resources to run the script. The Runbook will usually be in the queued state for less than 10 seconds, but there are times where it can take up to a few minutes for the script to run. Although Runbooks can be scheduled to run at a specific time, if a script must be run at an exact time with no variation, Runbooks are not recommended due to the queueing process.  

### Test pane
When editing a Runbook, there is a "Test pane" option that allows for testing of the script before publishing. 

### Jobs
A Job refers to an individual run of a Runbook. A unique Job is created each time the Runbook is run. From within a Job, you can see the status of the script run, along with any output from the script. To see all output from a script, including errors, select the "All Logs" tab from within a Job. 

## Schedules
Schedules are created at the Automation Account level, then linked to individual Runbooks. Schedules can be created for individual runs or recurring runs of Runbooks. 

## Authentication Within Scripts

### Credentials
The 'Credentials' section of an Azure Automation Account allow for storing of a username/password combination. This can also be used to store an application ID and client secret combination. The password will be encrypted and can only be accessed/decrypted within a Runbook under the Automation Account. 

A Credential object can be accessed within a script using the following command:

Get-AutomationPSCredential -Name <Credential Name>
  
#### Example:
  
$SpoCred = Get-AutomationPSCredential -Name "SpoAppRegistration"
Connect-PnPOnline -Url $SiteUrl -ClientId $SpoCred.UserName -ClientSecret $SpoCred.GetNetworkCredential().Password
  
### Certificates
Like Credentials, the "Certificates" section can be used to upload certificates that can be used to authenticate to resources that require certificate authentication. The certificate thumbprint can be referenced within the script directly as though the certificate was stored in a local certificate store on a Windows server. 
  
#### Example:
  
Connect-ExchangeOnline -CertificateThumbPrint "5F5420CE49C87C4073E519825E97F73536604AA5" -AppID "36ee4c6c-0812-40a2-b820-b22ebd11cce3" -Organization "contosoelectronics.onmicrosoft.com"
  
### Managed Identity

### Azure Resources

### Other M365 Resources

## Modules

## Variables

## Unique Properties of Runbooks
Write-Host/Write-Output

## Security
  
## Hybrid Worker
