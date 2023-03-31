## This guidance can be used to help update PowerShell scripts that were traditionally run on-premises or from a local machine.

## Why Azure Automation?
Azure Automation is an Azure service that allows PowerShell (and Python) scripts to be run from a cloud Azure subscription. This removes the dependency on a "scripting"
or "utility" server where PowerShell scripts are most often run from at large organizations. 

## Automation Accounts
An Azure Automation Account is a container for Runbooks, which are individuals scripts. Runbooks within an Azure Automation Account can share stored credentials,
certificates, variables, schedules, modules, and a managed identity. 

## Runbooks
Runbooks are the actual scripts that contain your PowerShell code.

## Creating Runbooks

### Runbook type

### Runbook version

### Webhooks
Webhooks allow a Runbook to be triggered through an HTTP request sent to a special URL that is generated when the Webhook is created. This allows the Runbook to be run
on an ad-hoc basis.

### Publishing
Azure Runbooks must be published before they can be run using a schedule, webhook, or the "start" button. 

### Jobs

## Schedules

## Authentication Within Scripts

### Azure Resources

### Other M365 Resources

### Stored Credentials

### Certificates

## Managed Identity

## Hybrid Worker

## Modules

## Variables
