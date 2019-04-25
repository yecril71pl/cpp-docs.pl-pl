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
ms.openlocfilehash: ab5d743c7c6abf7ee3a849a28916ebd32788ef40
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274948"
---
# <a name="security-identifier-global-functions"></a>Funkcje globalne identyfikatora zabezpieczeń

Te funkcje zwracają wspólnej znaną wartością identyfikatora SID obiektów.

> [!IMPORTANT]
>  Funkcje wymienione w poniższej tabeli nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

|||
|-|-|
|[Sids::AccountOps](#accountops)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_ACCOUNT_OPS.|
|[Sids::Admins](#admins)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_ADMINS.|
|[Sids::AnonymousLogon](#anonymouslogon)|Zwraca identyfikator SID SECURITY_ANONYMOUS_LOGON_RID.|
|[Sids::AuthenticatedUser](#authenticateduser)|Zwraca identyfikator SID SECURITY_AUTHENTICATED_USER_RID.|
|[Sids::BackupOps](#backupops)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_BACKUP_OPS.|
|[Sids::Batch](#batch)|Zwraca identyfikator SID SECURITY_BATCH_RID.|
|[Sids::CreatorGroup](#creatorgroup)|Zwraca identyfikator SID SECURITY_CREATOR_GROUP_RID.|
|[Sids::CreatorGroupServer](#creatorgroupserver)|Zwraca identyfikator SID SECURITY_CREATOR_GROUP_SERVER_RID.|
|[Sids::CreatorOwner](#creatorowner)|Zwraca identyfikator SID SECURITY_CREATOR_OWNER_RID.|
|[Sids::CreatorOwnerServer](#creatorownerserver)|Zwraca identyfikator SID SECURITY_CREATOR_OWNER_SERVER_RID.|
|[Sids::Dialup](#dialup)|Zwraca identyfikator SID SECURITY_DIALUP_RID.|
|[Sids::Guests](#guests)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_GUESTS.|
|[Sids::Interactive](#interactive)|Zwraca identyfikator SID SECURITY_INTERACTIVE_RID.|
|[Sids::Local](#local)|Zwraca identyfikator SID SECURITY_LOCAL_RID.|
|[Sids::Network](#network)|Zwraca identyfikator SID SECURITY_NETWORK_RID.|
|[Sids::NetworkService](#networkservice)|Zwraca identyfikator SID SECURITY_NETWORK_SERVICE_RID.|
|[Sids::Null](#null)|Zwraca identyfikator SID SECURITY_NULL_RID.|
|[Sids::PreW2KAccess](#prew2kaccess)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_PREW2KCOMPACCESS.|
|[Sids::PowerUsers](#powerusers)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_POWER_USERS.|
|[Sids::PrintOps](#printops)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_PRINT_OPS.|
|[Sids::proxy](#proxy)|Zwraca identyfikator SID SECURITY_PROXY_RID.|
|[Sids::RasServers](#rasservers)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_RAS_SERVERS.|
|[Sids::Replicator](#replicator)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_REPLICATOR.|
|[Sids::RestrictedCode](#restrictedcode)|Zwraca identyfikator SID SECURITY_RESTRICTED_CODE_RID.|
|[Sids::Self](#self)|Zwraca identyfikator SID SECURITY_PRINCIPAL_SELF_RID.|
|[Sids::ServerLogon](#serverlogon)|Zwraca identyfikator SID SECURITY_SERVER_LOGON_RID.|
|[Sids::Service](#service)|Zwraca identyfikator SID SECURITY_SERVICE_RID.|
|[Sids::System](#system)|Zwraca identyfikator SID SECURITY_LOCAL_SYSTEM_RID.|
|[Sids::SystemOps](#systemops)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_SYSTEM_OPS.|
|[Sids::TerminalServer](#terminalserver)|Zwraca identyfikator SID SECURITY_TERMINAL_SERVER_RID.|
|[Sids::Users](#users)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_USERS.|
|[Sids::World](#world)|Zwraca identyfikator SID SECURITY_WORLD_RID.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

##  <a name="accountops"></a>  Sids::AccountOps

Zwraca identyfikator SID DOMAIN_ALIAS_RID_ACCOUNT_OPS.

```
CSid AccountOps() throw(...);
```

##  <a name="admins"></a>  Sids::Admins

Zwraca identyfikator SID DOMAIN_ALIAS_RID_ADMINS.

```
CSid Admins() throw(...);
```

##  <a name="anonymouslogon"></a>  Sids::AnonymousLogon

Zwraca identyfikator SID SECURITY_ANONYMOUS_LOGON_RID.

```
CSid AnonymousLogon() throw(...);
```

##  <a name="authenticateduser"></a>  Sids::AuthenticatedUser

Zwraca identyfikator SID SECURITY_AUTHENTICATED_USER_RID.

```
CSid AuthenticatedUser() throw(...);
```

##  <a name="backupops"></a>  Sids::BackupOps

Zwraca identyfikator SID DOMAIN_ALIAS_RID_BACKUP_OPS.

```
CSid BackupOps() throw(...);
```

##  <a name="batch"></a>  Sids::Batch

Zwraca identyfikator SID SECURITY_BATCH_RID.

```
CSid Batch() throw(...);
```

##  <a name="creatorgroup"></a>  Sids::CreatorGroup

Zwraca identyfikator SID SECURITY_CREATOR_GROUP_RID.

```
CSid CreatorGroup() throw(...);
```

##  <a name="creatorgroupserver"></a>  Sids::CreatorGroupServer

Zwraca identyfikator SID SECURITY_CREATOR_GROUP_SERVER_RID.

```
CSid CreatorGroupServer() throw(...);
```

##  <a name="creatorowner"></a>  Sids::CreatorOwner

Zwraca identyfikator SID SECURITY_CREATOR_OWNER_RID.

```
CSid CreatorOwner() throw(...);
```

##  <a name="creatorownerserver"></a>  Sids::CreatorOwnerServer

Zwraca identyfikator SID SECURITY_CREATOR_OWNER_SERVER_RID.

```
CSid CreatorOwnerServer() throw(...);
```

##  <a name="dialup"></a>  Sids::Dialup

Zwraca identyfikator SID SECURITY_DIALUP_RID.

```
CSid Dialup() throw(...);
```

##  <a name="guests"></a>  Sids::Guests

Zwraca identyfikator SID DOMAIN_ALIAS_RID_GUESTS.

```
CSid Guests() throw(...);
```

##  <a name="interactive"></a>  Sids::Interactive

Zwraca identyfikator SID SECURITY_INTERACTIVE_RID.

```
CSid Interactive() throw(...);
```

##  <a name="local"></a>  Sids::Local

Zwraca identyfikator SID SECURITY_LOCAL_RID.

```
CSid Local() throw(...);
```

##  <a name="network"></a>  Sids::Network

Zwraca identyfikator SID SECURITY_NETWORK_RID.

```
CSid Network() throw(...);
```

##  <a name="networkservice"></a>  Sids::NetworkService

Zwraca identyfikator SID SECURITY_NETWORK_SERVICE_RID.

```
CSid NetworkService() throw(...);
```

### <a name="remarks"></a>Uwagi

Użyj usługi sieciowej, aby włączyć NT\Usługa użytkownikowi odczyt CPerfMon obiektu zabezpieczeń. Usługa sieciowa dodaje SecurityAttribute kodowi ATLServer, co umożliwi użytkownikom biblioteki DLL do logowania na koncie Usługa sieciowa na Windows XP Home Edition, Windows XP Professional, Windows Server 2003 i większa systemu operacyjnego.

Po utworzeniu dzienników niestandardowych liczników za pomocą klasy ATLServer CPerfMon w przystawce MMC monitora wydajności liczniki nie może występować podczas wyświetlania pliku dziennika, mimo że zostaną poprawnie wyświetlone w widoku w czasie rzeczywistym. CPerfMon niestandardowych liczników wydajności nie ma wystarczających uprawnień do uruchamiania w obszarze "Dzienniki wydajności i alerty" service (smlogsvc.exe) w systemie Windows XP Home Edition, Windows XP Professional, Windows Server 2003 (lub nowszego) systemów operacyjnych. Ta usługa działa na koncie "NT\Usługa".

##  <a name="null"></a>  Sids::NULL

Zwraca identyfikator SID SECURITY_NULL_RID.

```
CSid Null() throw(...);
```

##  <a name="prew2kaccess"></a>  Sids::PreW2KAccess

Zwraca identyfikator SID DOMAIN_ALIAS_RID_PREW2KCOMPACCESS.

```
CSid PreW2KAccess() throw(...);
```

##  <a name="powerusers"></a>  Sids::PowerUsers

Zwraca identyfikator SID DOMAIN_ALIAS_RID_POWER_USERS.

```
CSid PowerUsers() throw(...);
```

##  <a name="printops"></a>  Sids::PrintOps

Zwraca identyfikator SID DOMAIN_ALIAS_RID_PRINT_OPS.

```
CSid PrintOps() throw(...);
```

##  <a name="proxy"></a>  Sids::proxy

Zwraca identyfikator SID SECURITY_PROXY_RID.

```
CSid Proxy() throw(...);
```

##  <a name="rasservers"></a>  Sids::RasServers

Zwraca identyfikator SID DOMAIN_ALIAS_RID_RAS_SERVERS.

```
CSid RasServers() throw(...);
```

##  <a name="replicator"></a>  Sids::Replicator

Zwraca identyfikator SID DOMAIN_ALIAS_RID_REPLICATOR.

```
CSid Replicator() throw(...);
```

##  <a name="restrictedcode"></a>  Sids::RestrictedCode

Zwraca identyfikator SID SECURITY_RESTRICTED_CODE_RID.

```
CSid RestrictedCode() throw(...);
```

##  <a name="self"></a>  Sids::Self

Zwraca identyfikator SID SECURITY_PRINCIPAL_SELF_RID.

```
CSid Self() throw(...);
```

##  <a name="serverlogon"></a>  Sids::ServerLogon

Zwraca identyfikator SID SECURITY_SERVER_LOGON_RID.

```
CSid ServerLogon() throw(...);
```

##  <a name="service"></a>  Sids::Service

Zwraca identyfikator SID SECURITY_SERVICE_RID.

```
CSid Service() throw(...);
```

##  <a name="system"></a>  Sids::System

Zwraca identyfikator SID SECURITY_LOCAL_SYSTEM_RID.

```
CSid System() throw(...);
```

##  <a name="systemops"></a>  Sids::SystemOps

Zwraca identyfikator SID DOMAIN_ALIAS_RID_SYSTEM_OPS.

```
CSid SystemOps() throw(...);
```

##  <a name="terminalserver"></a>  Sids::TerminalServer

Zwraca identyfikator SID SECURITY_TERMINAL_SERVER_RID.

```
CSid TerminalServer() throw(...);
```

##  <a name="users"></a>  Sids::Users

Zwraca identyfikator SID DOMAIN_ALIAS_RID_USERS.

```
CSid Users() throw(...);
```

##  <a name="world"></a>  Sids::World

Zwraca identyfikator SID SECURITY_WORLD_RID.

```
CSid World() throw(...);
```

## <a name="see-also"></a>Zobacz także

[Funkcje](../../atl/reference/atl-functions.md)
