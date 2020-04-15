---
title: Funkcje globalne identyfikatora zabezpieczeń
ms.date: 11/04/2016
f1_keywords:
- atlsecurity/ATL::Sids::AccountOps
- atlsecurity/ATL::Sids::Admins
- atlsecurity/ATL::Sids::AnonymousLogon
- atlsecurity/ATL::Sids::AuthenticatedUser
- atlsecurity/ATL::Sids::BackupOps
- atlsecurity/ATL::Sids::Batch
- atlsecurity/ATL::Sids::CreatorGroup
- atlsecurity/ATL::Sids::CreatorGroupServer
- atlsecurity/ATL::Sids::CreatorOwner
- atlsecurity/ATL::Sids::CreatorOwnerServer
- atlsecurity/ATL::Sids::Dialup
- atlsecurity/ATL::Sids::Guests
- atlsecurity/ATL::Sids::Interactive
- atlsecurity/ATL::Sids::Local
- atlsecurity/ATL::Sids::Network
- atlsecurity/ATL::Sids::NetworkService
- atlsecurity/ATL::Sids::Null
- atlsecurity/ATL::Sids::PowerUsers
- atlsecurity/ATL::Sids::PrintOps
- atlsecurity/ATL::Sids::Proxy
- atlsecurity/ATL::Sids::RasServers
- atlsecurity/ATL::Sids::Replicator
- atlsecurity/ATL::Sids::RestrictedCode
- atlsecurity/ATL::Sids::Self
- atlsecurity/ATL::Sids::ServerLogon
- atlsecurity/ATL::Sids::Service
- atlsecurity/ATL::Sids::System
- atlsecurity/ATL::Sids::SystemOps
- atlsecurity/ATL::Sids::TerminalServer
- atlsecurity/ATL::Sids::Users
- atlsecurity/ATL::Sids::World
helpviewer_keywords:
- security IDs [C++]
- SIDs [C++], returning SID objects
ms.assetid: 85404dcb-c59b-4535-ab3d-66cfa37e87de
ms.openlocfilehash: 83326c13de7585806ab841f728f587f1131b5e8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325994"
---
# <a name="security-identifier-global-functions"></a>Funkcje globalne identyfikatora zabezpieczeń

Funkcje te zwracają typowe dobrze znane obiekty SID.

> [!IMPORTANT]
> Funkcji wymienionych w poniższej tabeli nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows.

|||
|-|-|
|[Sids::AccountOps](#accountops)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_ACCOUNT_OPS.|
|[Sids::Administratorzy](#admins)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_ADMINS.|
|[Sids::AnonymousLogon](#anonymouslogon)|Zwraca identyfikator SID SECURITY_ANONYMOUS_LOGON_RID.|
|[Sids::Uwierzytelnionyużycie](#authenticateduser)|Zwraca identyfikator SID SECURITY_AUTHENTICATED_USER_RID.|
|[Sids::BackupOps](#backupops)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_BACKUP_OPS.|
|[Sids::Partia](#batch)|Zwraca identyfikator SID SECURITY_BATCH_RID.|
|[Sids::Grupa twórców](#creatorgroup)|Zwraca identyfikator SID SECURITY_CREATOR_GROUP_RID.|
|[Sids::CreatorGroupServer](#creatorgroupserver)|Zwraca identyfikator SID SECURITY_CREATOR_GROUP_SERVER_RID.|
|[Sids::CreatorOwner](#creatorowner)|Zwraca identyfikator SID SECURITY_CREATOR_OWNER_RID.|
|[Sids::CreatorOwnerServer](#creatorownerserver)|Zwraca identyfikator SID SECURITY_CREATOR_OWNER_SERVER_RID.|
|[Sids::Dialup](#dialup)|Zwraca identyfikator SID SECURITY_DIALUP_RID.|
|[Sids::Goście](#guests)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_GUESTS.|
|[Sids::Interaktywne](#interactive)|Zwraca identyfikator SID SECURITY_INTERACTIVE_RID.|
|[Sids::Lokalny](#local)|Zwraca identyfikator SID SECURITY_LOCAL_RID.|
|[Sids::Sieć](#network)|Zwraca identyfikator SID SECURITY_NETWORK_RID.|
|[Sids::Usługa sieciowa](#networkservice)|Zwraca identyfikator SID SECURITY_NETWORK_SERVICE_RID.|
|[Sids::Null](#null)|Zwraca identyfikator SID SECURITY_NULL_RID.|
|[Sids::PreW2KAccess](#prew2kaccess)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_PREW2KCOMPACCESS.|
|[Sids::PowerUżytnicy](#powerusers)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_POWER_USERS.|
|[Sids::PrintOps](#printops)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_PRINT_OPS.|
|[Sids::Proxy](#proxy)|Zwraca identyfikator SID SECURITY_PROXY_RID.|
|[Sids::RasServers](#rasservers)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_RAS_SERVERS.|
|[Sids::Replikator](#replicator)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_REPLICATOR.|
|[Sids::RestrictedCode](#restrictedcode)|Zwraca identyfikator SID SECURITY_RESTRICTED_CODE_RID.|
|[Sids::Self](#self)|Zwraca identyfikator SID SECURITY_PRINCIPAL_SELF_RID.|
|[Sids::ServerLogon](#serverlogon)|Zwraca identyfikator SID SECURITY_SERVER_LOGON_RID.|
|[Sids::Usługa](#service)|Zwraca identyfikator SID SECURITY_SERVICE_RID.|
|[Sids::System](#system)|Zwraca identyfikator SID SECURITY_LOCAL_SYSTEM_RID.|
|[Sids::SystemOps](#systemops)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_SYSTEM_OPS.|
|[Sids::TerminalServer](#terminalserver)|Zwraca identyfikator SID SECURITY_TERMINAL_SERVER_RID.|
|[Sids::Użytkownicy](#users)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_USERS.|
|[Sids::Świat](#world)|Zwraca identyfikator SID SECURITY_WORLD_RID.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

## <a name="sidsaccountops"></a><a name="accountops"></a>Sids::AccountOps

Zwraca identyfikator SID DOMAIN_ALIAS_RID_ACCOUNT_OPS.

```
CSid AccountOps() throw(...);
```

## <a name="sidsadmins"></a><a name="admins"></a>Sids::Administratorzy

Zwraca identyfikator SID DOMAIN_ALIAS_RID_ADMINS.

```
CSid Admins() throw(...);
```

## <a name="sidsanonymouslogon"></a><a name="anonymouslogon"></a>Sids::AnonymousLogon

Zwraca identyfikator SID SECURITY_ANONYMOUS_LOGON_RID.

```
CSid AnonymousLogon() throw(...);
```

## <a name="sidsauthenticateduser"></a><a name="authenticateduser"></a>Sids::Uwierzytelnionyużycie

Zwraca identyfikator SID SECURITY_AUTHENTICATED_USER_RID.

```
CSid AuthenticatedUser() throw(...);
```

## <a name="sidsbackupops"></a><a name="backupops"></a>Sids::BackupOps

Zwraca identyfikator SID DOMAIN_ALIAS_RID_BACKUP_OPS.

```
CSid BackupOps() throw(...);
```

## <a name="sidsbatch"></a><a name="batch"></a>Sids::Partia

Zwraca identyfikator SID SECURITY_BATCH_RID.

```
CSid Batch() throw(...);
```

## <a name="sidscreatorgroup"></a><a name="creatorgroup"></a>Sids::Grupa twórców

Zwraca identyfikator SID SECURITY_CREATOR_GROUP_RID.

```
CSid CreatorGroup() throw(...);
```

## <a name="sidscreatorgroupserver"></a><a name="creatorgroupserver"></a>Sids::CreatorGroupServer

Zwraca identyfikator SID SECURITY_CREATOR_GROUP_SERVER_RID.

```
CSid CreatorGroupServer() throw(...);
```

## <a name="sidscreatorowner"></a><a name="creatorowner"></a>Sids::CreatorOwner

Zwraca identyfikator SID SECURITY_CREATOR_OWNER_RID.

```
CSid CreatorOwner() throw(...);
```

## <a name="sidscreatorownerserver"></a><a name="creatorownerserver"></a>Sids::CreatorOwnerServer

Zwraca identyfikator SID SECURITY_CREATOR_OWNER_SERVER_RID.

```
CSid CreatorOwnerServer() throw(...);
```

## <a name="sidsdialup"></a><a name="dialup"></a>Sids::Dialup

Zwraca identyfikator SID SECURITY_DIALUP_RID.

```
CSid Dialup() throw(...);
```

## <a name="sidsguests"></a><a name="guests"></a>Sids::Goście

Zwraca identyfikator SID DOMAIN_ALIAS_RID_GUESTS.

```
CSid Guests() throw(...);
```

## <a name="sidsinteractive"></a><a name="interactive"></a>Sids::Interaktywne

Zwraca identyfikator SID SECURITY_INTERACTIVE_RID.

```
CSid Interactive() throw(...);
```

## <a name="sidslocal"></a><a name="local"></a>Sids::Lokalny

Zwraca identyfikator SID SECURITY_LOCAL_RID.

```
CSid Local() throw(...);
```

## <a name="sidsnetwork"></a><a name="network"></a>Sids::Sieć

Zwraca identyfikator SID SECURITY_NETWORK_RID.

```
CSid Network() throw(...);
```

## <a name="sidsnetworkservice"></a><a name="networkservice"></a>Sids::Usługa sieciowa

Zwraca identyfikator SID SECURITY_NETWORK_SERVICE_RID.

```
CSid NetworkService() throw(...);
```

### <a name="remarks"></a>Uwagi

Użyj usługi NetworkService, aby włączyć użytkownika usługi NT AUTHORITY\NetworkService do odczytu obiektu zabezpieczeń CPerfMon. Usługa NetworkService dodaje atrybut SecurityAttribute do kodu ATLServer, który umożliwia biblioteki DLL zalogowanie się pod kontem NetworkService w systemie Windows XP Home Edition, Windows XP Professional, Windows Server 2003 i większym systemie operacyjnym.

Gdy niestandardowe liczniki dziennika są tworzone za pomocą klasy ATLServer CPerfMon w programie MmC Perfmon, liczniki mogą nie być wyświetlane podczas wyświetlania pliku dziennika, chociaż będą wyświetlane poprawnie w widoku w czasie rzeczywistym. Niestandardowe liczniki wydajności CPerfMon nie mają uprawnień niezbędnych do uruchamiania w ramach usługi "Dzienniki wydajności i alerty" (smlogsvc.exe) w systemach operacyjnych Windows XP Home Edition, Windows XP Professional, Windows Server 2003 (lub nowszych). Ta usługa jest uruchamiana na koncie "NT AUTHORITY\NetworkService".

## <a name="sidsnull"></a><a name="null"></a>Sids::Null

Zwraca identyfikator SID SECURITY_NULL_RID.

```
CSid Null() throw(...);
```

## <a name="sidsprew2kaccess"></a><a name="prew2kaccess"></a>Sids::PreW2KAccess

Zwraca identyfikator SID DOMAIN_ALIAS_RID_PREW2KCOMPACCESS.

```
CSid PreW2KAccess() throw(...);
```

## <a name="sidspowerusers"></a><a name="powerusers"></a>Sids::PowerUżytnicy

Zwraca identyfikator SID DOMAIN_ALIAS_RID_POWER_USERS.

```
CSid PowerUsers() throw(...);
```

## <a name="sidsprintops"></a><a name="printops"></a>Sids::PrintOps

Zwraca identyfikator SID DOMAIN_ALIAS_RID_PRINT_OPS.

```
CSid PrintOps() throw(...);
```

## <a name="sidsproxy"></a><a name="proxy"></a>Sids::Proxy

Zwraca identyfikator SID SECURITY_PROXY_RID.

```
CSid Proxy() throw(...);
```

## <a name="sidsrasservers"></a><a name="rasservers"></a>Sids::RasServers

Zwraca identyfikator SID DOMAIN_ALIAS_RID_RAS_SERVERS.

```
CSid RasServers() throw(...);
```

## <a name="sidsreplicator"></a><a name="replicator"></a>Sids::Replikator

Zwraca identyfikator SID DOMAIN_ALIAS_RID_REPLICATOR.

```
CSid Replicator() throw(...);
```

## <a name="sidsrestrictedcode"></a><a name="restrictedcode"></a>Sids::RestrictedCode

Zwraca identyfikator SID SECURITY_RESTRICTED_CODE_RID.

```
CSid RestrictedCode() throw(...);
```

## <a name="sidsself"></a><a name="self"></a>Sids::Self

Zwraca identyfikator SID SECURITY_PRINCIPAL_SELF_RID.

```
CSid Self() throw(...);
```

## <a name="sidsserverlogon"></a><a name="serverlogon"></a>Sids::ServerLogon

Zwraca identyfikator SID SECURITY_SERVER_LOGON_RID.

```
CSid ServerLogon() throw(...);
```

## <a name="sidsservice"></a><a name="service"></a>Sids::Usługa

Zwraca identyfikator SID SECURITY_SERVICE_RID.

```
CSid Service() throw(...);
```

## <a name="sidssystem"></a><a name="system"></a>Sids::System

Zwraca identyfikator SID SECURITY_LOCAL_SYSTEM_RID.

```
CSid System() throw(...);
```

## <a name="sidssystemops"></a><a name="systemops"></a>Sids::SystemOps

Zwraca identyfikator SID DOMAIN_ALIAS_RID_SYSTEM_OPS.

```
CSid SystemOps() throw(...);
```

## <a name="sidsterminalserver"></a><a name="terminalserver"></a>Sids::TerminalServer

Zwraca identyfikator SID SECURITY_TERMINAL_SERVER_RID.

```
CSid TerminalServer() throw(...);
```

## <a name="sidsusers"></a><a name="users"></a>Sids::Użytkownicy

Zwraca identyfikator SID DOMAIN_ALIAS_RID_USERS.

```
CSid Users() throw(...);
```

## <a name="sidsworld"></a><a name="world"></a>Sids::Świat

Zwraca identyfikator SID SECURITY_WORLD_RID.

```
CSid World() throw(...);
```

## <a name="see-also"></a>Zobacz też

[Funkcje](../../atl/reference/atl-functions.md)
