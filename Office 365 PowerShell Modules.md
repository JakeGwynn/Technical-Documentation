# Last updated 03/28/2023
# PowerShell Modules and Authentication Methods
| Module | Client Secret | Certificate | Connect with Client Secret | Connect with Certificate |
| --- | --- | --- | --- | --- |
| AzureAD                                 | False          | True        | N/A                     | `Connect-AzureAD -TenantId <TenantId> -ApplicationId <ClientId> -CertificateThumbprint <Thumbprint>`               |
| MSOnline | False | False | N/A | N/A |
| ExchangeOnlineManagement                | False          | True        | N/A | `Connect-ExchangeOnline -ClientId <ClientId> -TenantId <TenantId> -CertificateThumbprint <Thumbprint>`            |
| PnP.PowerShell                          | True          | True        | `Connect-PnPOnline -Url <SiteUrl> -ClientId <ClientId> -ClientSecret <ClientSecret> -Tenant <TenantId>`          | `Connect-PnPOnline -Url <SiteUrl> -ClientId <ClientId> -CertificatePath <CertPath> -Tenant <TenantId> -Thumbprint <Thumbprint>` |
| Microsoft.Graph                         | True          | True        | `Connect-Graph -ClientId <ClientId> -TenantId <TenantId> -ClientSecret <ClientSecret>`                            | `Connect-Graph -ClientId <ClientId> -TenantId <TenantId> -CertificateThumbprint <Thumbprint> -CertificatePath <CertPath>` |
| Az                                      | True          | True        | `Connect-AzAccount -ServicePrincipal -Tenant <TenantId> -ApplicationId <ClientId> -Credential (New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList "<ClientId>", (ConvertTo-SecureString -String "<ClientSecret>" -AsPlainText -Force))` | `Connect-AzAccount -ServicePrincipal -Tenant <TenantId> -ApplicationId <ClientId> -CertificateThumbprint <Thumbprint>` |
| AzureADPreview                          | True          | True        | `Connect-AzureAD -TenantId <TenantId> -ApplicationId <ClientId> -ClientSecret <ClientSecret>`                     | `Connect-AzureAD -TenantId <TenantId> -ApplicationId <ClientId> -CertificateThumbprint <Thumbprint>`               |
| Microsoft.Online.SharePoint.PowerShell  | True          | True        | `Connect-SPOService -Url <AdminSiteUrl> -ClientId <ClientId> -ClientSecret <ClientSecret>`


| Module | Client Secret | Certificate | Connect with Client Secret | Connect with Certificate |
| --- | --- | --- | --- | --- |
| AzureAD | False | True | N/A | `Connect-AzureAD -TenantId $tenantId -ApplicationId $applicationId -CertificateThumbprint $thumbprint` |
| MSOnline | False | False | N/A | N/A |
| ExchangeOnlineManagement | False | True | N/A | `Connect-ExchangeOnline -CertificateFilePath $path -AppId $appId -Organization $org` |
| PnP.PowerShell | True* | True | `Connect-PnPOnline -Url $url -ClientId $clientId -ClientSecret $clientSecret` | `Connect-PnPOnline -Url $url -ClientId $clientId -Thumbprint $CertThumbprint` |
| Microsoft.Graph | True* | True | `Connect-MgGraph -ClientID $clientId -TenantID $tenantId -ClientSecret $clientSecret` | `Connect-MgGraph -ClientID $clientId -TenantID $tenantId -CertificateThumbprint $thumbprint` |
| Az | True | True | `Connect-AzAccount -Credential $credential` | `Connect-AzAccount -ServicePrincipal -TenantId $tenantId -ApplicationId $applicationId -CertificateThumbprint $thumbprint` |
| AzureADPreview | True | True | `Connect-AzureAD -Credential $credential`  (same as AzureAD)  | `Connect-AzureAD -TenantId $tenantId -ApplicationId $applicationId -CertificateThumbprint $thumbprint` (same as AzureAD) |
| Microsoft.Online.SharePoint.PowerShell | False | False  (but can use App-Only Token)  | N/A  (but can use App-Only Token)  | N/A  (but can use App-Only Token) |


# Certificate Authentication

#CLient Secret Authentication
