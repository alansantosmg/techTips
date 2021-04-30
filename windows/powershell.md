# PowerShell

## Connect to Exchange online

```powershell

// install modules
 Import-Module ExchangeOnlineManagement
 Import-Module ExchangeOnlineManagement
 Set-ExecutionPolicy RemoteSigned
 Install-Module -Name ExchangeOnlineManagement

// connect
 Connect-ExchangeOnline -UserPrincipalName alan.santos@acotel.com.br -ShowProgress $true

 //disconnect
 Disconnect-ExchangeOnline


```
## Meeting Room O365 Setup

```powershell

//Create room
Set-Place -Identity "sala_apoio_tr01" -City "Três Rios" -Building "Prédio 2" -Capacity 8 -Floor 1 -FloorLabel "Terreo" -Label "Sala de apoio TR01" -PostalCode "25804-250" -State "Rio de Janeiro" -Street "Rua Isaltino Silveira, 768"

//Get room
Get-Place -Identity "sala_apoio_tr01"

// Set time
Set-MailboxCalendarConfiguration -Identity "sala_apoio_tr01" -WorkingHoursTimeZone "E. South America Standard Time"

// Get time
Get-MailboxCalendarConfiguration -Identity "sala_apoio_tr01"

```

### Create New Room list 0365

```powershell

//add group
New-DistributionGroup Salas -Roomlist

// add room as group member
Add-DistributionGroupMember salas -Member sala1@acotel.com.br

// list group members
Get-DistributionGroupMember -Identity salas

```

## Setup Outlook Spaces (Experimental)

```powershell

 Import-Module ExchangeOnlineManagement
 Import-Module ExchangeOnlineManagement
 Set-ExecutionPolicy RemoteSigned
 Install-Module -Name ExchangeOnlineManagement
 Connect-ExchangeOnline
 Get-OwaMailboxPolicy | fl name, *moca*
 Set-OwaMailboxPolicy OwaMailboxPolicy-Default -ProjectMocaEnabled $true
 Get-OwaMailboxPolicy | fl name, *moca*
 Get-CASMailbox alan.santos@acotel.com.br | fl *owa*
 Disconnect-ExchangeOnline

```