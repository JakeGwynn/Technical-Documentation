# Last updated 03/28/2023
# PowerShell Modules and Authentication Methods

| Module | Connect with Client Secret | Connect with Certificate |
| --- | --- | --- |
| AzureAD | N/A | `Connect-AzureAD -TenantId $tenantId -ApplicationId $applicationId -CertificateThumbprint $thumbprint` |
| MSOnline | N/A | N/A |
| ExchangeOnlineManagement | N/A | `Connect-ExchangeOnline -CertificateFilePath $path -AppId $appId -Organization $org` |
| PnP.PowerShell | True* | True | `Connect-PnPOnline -Url $url -ClientId $clientId -ClientSecret $clientSecret` | `Connect-PnPOnline -Url $url -ClientId $clientId -Thumbprint $CertThumbprint` |
| Microsoft.Graph | * `Connect-MgGraph -ClientID $clientId -TenantID $tenantId -ClientSecret $clientSecret` | `Connect-MgGraph -ClientID $clientId -TenantID $tenantId -CertificateThumbprint $thumbprint` |
| Az |`Connect-AzAccount -Credential $credential` | `Connect-AzAccount -ServicePrincipal -TenantId $tenantId -ApplicationId $applicationId -CertificateThumbprint $thumbprint` |
| Microsoft.Online.SharePoint.PowerShell | N/A  (but can use App-Only Token)  | N/A  (but can use App-Only Token) |


# Certificate Authentication

# Client Secret Authentication
