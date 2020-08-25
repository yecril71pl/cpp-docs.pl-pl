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
ms.openlocfilehash: e040cbb76e851bd323360f4f5ae602f9c73651d1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834482"
---
# <a name="security-identifier-global-functions"></a>Funkcje globalne identyfikatora zabezpieczeń

Te funkcje zwracają typowe dobrze znane obiekty SID.

> [!IMPORTANT]
> Funkcje wymienione w poniższej tabeli nie mogą być używane w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

|Nazwa|Opis|
|-|-|
|[Identyfikatory SID:: AccountOps](#accountops)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_ACCOUNT_OPS.|
|[SID:: Administratorzy](#admins)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_ADMINS.|
|[Identyfikatory SID:: AnonymousLogon](#anonymouslogon)|Zwraca identyfikator SID SECURITY_ANONYMOUS_LOGON_RID.|
|[Identyfikatory SID:: AuthenticatedUser](#authenticateduser)|Zwraca identyfikator SID SECURITY_AUTHENTICATED_USER_RID.|
|[Identyfikatory SID:: BackupOps](#backupops)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_BACKUP_OPS.|
|[Identyfikatory SID:: Batch](#batch)|Zwraca identyfikator SID SECURITY_BATCH_RID.|
|[Identyfikatory SID:: Creator](#creatorgroup)|Zwraca identyfikator SID SECURITY_CREATOR_GROUP_RID.|
|[Identyfikatory SID:: CreatorGroupServer](#creatorgroupserver)|Zwraca identyfikator SID SECURITY_CREATOR_GROUP_SERVER_RID.|
|[Identyfikatory SID:: CreatorOwner](#creatorowner)|Zwraca identyfikator SID SECURITY_CREATOR_OWNER_RID.|
|[Identyfikatory SID:: CreatorOwnerServer](#creatorownerserver)|Zwraca identyfikator SID SECURITY_CREATOR_OWNER_SERVER_RID.|
|[Identyfikatory SID::D ialup](#dialup)|Zwraca identyfikator SID SECURITY_DIALUP_RID.|
|[Identyfikatory SID:: Goście](#guests)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_GUESTS.|
|[Identyfikatory SID:: Interactive](#interactive)|Zwraca identyfikator SID SECURITY_INTERACTIVE_RID.|
|[Identyfikatory SID:: local](#local)|Zwraca identyfikator SID SECURITY_LOCAL_RID.|
|[Identyfikatory SID:: Network](#network)|Zwraca identyfikator SID SECURITY_NETWORK_RID.|
|[Identyfikatory SID:: NetworkService](#networkservice)|Zwraca identyfikator SID SECURITY_NETWORK_SERVICE_RID.|
|[Identyfikatory SID:: null](#null)|Zwraca identyfikator SID SECURITY_NULL_RID.|
|[Identyfikatory SID::P reW2KAccess](#prew2kaccess)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_PREW2KCOMPACCESS.|
|[Identyfikatory SID::P owerUsers](#powerusers)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_POWER_USERS.|
|[Identyfikatory SID::P rintOps](#printops)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_PRINT_OPS.|
|[Identyfikatory SID::P Roxy](#proxy)|Zwraca identyfikator SID SECURITY_PROXY_RID.|
|[Identyfikatory SID:: RasServers](#rasservers)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_RAS_SERVERS.|
|[SID:: Replikator](#replicator)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_REPLICATOR.|
|[Identyfikatory SID:: RestrictedCode](#restrictedcode)|Zwraca identyfikator SID SECURITY_RESTRICTED_CODE_RID.|
|[Identyfikatory SID:: własne](#self)|Zwraca identyfikator SID SECURITY_PRINCIPAL_SELF_RID.|
|[Identyfikatory SID:: ServerLogon](#serverlogon)|Zwraca identyfikator SID SECURITY_SERVER_LOGON_RID.|
|[SID:: Service](#service)|Zwraca identyfikator SID SECURITY_SERVICE_RID.|
|[SID:: system](#system)|Zwraca identyfikator SID SECURITY_LOCAL_SYSTEM_RID.|
|[Identyfikatory SID:: SystemOps](#systemops)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_SYSTEM_OPS.|
|[Identyfikatory SID:: TerminalServer](#terminalserver)|Zwraca identyfikator SID SECURITY_TERMINAL_SERVER_RID.|
|[Identyfikatory SID:: users](#users)|Zwraca identyfikator SID DOMAIN_ALIAS_RID_USERS.|
|[Identyfikatory SID:: World](#world)|Zwraca identyfikator SID SECURITY_WORLD_RID.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity. h

## <a name="sidsaccountops"></a><a name="accountops"></a> Identyfikatory SID:: AccountOps

Zwraca identyfikator SID DOMAIN_ALIAS_RID_ACCOUNT_OPS.

```
CSid AccountOps() throw(...);
```

## <a name="sidsadmins"></a><a name="admins"></a> SID:: Administratorzy

Zwraca identyfikator SID DOMAIN_ALIAS_RID_ADMINS.

```
CSid Admins() throw(...);
```

## <a name="sidsanonymouslogon"></a><a name="anonymouslogon"></a> Identyfikatory SID:: AnonymousLogon

Zwraca identyfikator SID SECURITY_ANONYMOUS_LOGON_RID.

```
CSid AnonymousLogon() throw(...);
```

## <a name="sidsauthenticateduser"></a><a name="authenticateduser"></a> Identyfikatory SID:: AuthenticatedUser

Zwraca identyfikator SID SECURITY_AUTHENTICATED_USER_RID.

```
CSid AuthenticatedUser() throw(...);
```

## <a name="sidsbackupops"></a><a name="backupops"></a> Identyfikatory SID:: BackupOps

Zwraca identyfikator SID DOMAIN_ALIAS_RID_BACKUP_OPS.

```
CSid BackupOps() throw(...);
```

## <a name="sidsbatch"></a><a name="batch"></a> Identyfikatory SID:: Batch

Zwraca identyfikator SID SECURITY_BATCH_RID.

```
CSid Batch() throw(...);
```

## <a name="sidscreatorgroup"></a><a name="creatorgroup"></a> Identyfikatory SID:: Creator

Zwraca identyfikator SID SECURITY_CREATOR_GROUP_RID.

```
CSid CreatorGroup() throw(...);
```

## <a name="sidscreatorgroupserver"></a><a name="creatorgroupserver"></a> Identyfikatory SID:: CreatorGroupServer

Zwraca identyfikator SID SECURITY_CREATOR_GROUP_SERVER_RID.

```
CSid CreatorGroupServer() throw(...);
```

## <a name="sidscreatorowner"></a><a name="creatorowner"></a> Identyfikatory SID:: CreatorOwner

Zwraca identyfikator SID SECURITY_CREATOR_OWNER_RID.

```
CSid CreatorOwner() throw(...);
```

## <a name="sidscreatorownerserver"></a><a name="creatorownerserver"></a> Identyfikatory SID:: CreatorOwnerServer

Zwraca identyfikator SID SECURITY_CREATOR_OWNER_SERVER_RID.

```
CSid CreatorOwnerServer() throw(...);
```

## <a name="sidsdialup"></a><a name="dialup"></a> Identyfikatory SID::D ialup

Zwraca identyfikator SID SECURITY_DIALUP_RID.

```
CSid Dialup() throw(...);
```

## <a name="sidsguests"></a><a name="guests"></a> Identyfikatory SID:: Goście

Zwraca identyfikator SID DOMAIN_ALIAS_RID_GUESTS.

```
CSid Guests() throw(...);
```

## <a name="sidsinteractive"></a><a name="interactive"></a> Identyfikatory SID:: Interactive

Zwraca identyfikator SID SECURITY_INTERACTIVE_RID.

```
CSid Interactive() throw(...);
```

## <a name="sidslocal"></a><a name="local"></a> Identyfikatory SID:: local

Zwraca identyfikator SID SECURITY_LOCAL_RID.

```
CSid Local() throw(...);
```

## <a name="sidsnetwork"></a><a name="network"></a> Identyfikatory SID:: Network

Zwraca identyfikator SID SECURITY_NETWORK_RID.

```
CSid Network() throw(...);
```

## <a name="sidsnetworkservice"></a><a name="networkservice"></a> Identyfikatory SID:: NetworkService

Zwraca identyfikator SID SECURITY_NETWORK_SERVICE_RID.

```
CSid NetworkService() throw(...);
```

### <a name="remarks"></a>Uwagi

Użyj sieci NetworkService, aby umożliwić użytkownikowi NT AUTHORITY\NetworkService odczytywanie obiektu zabezpieczeń CPerfMon. Usługa sieciowa dodaje element SecurityAttribute do kodu ATLServer, który umożliwi plikowi DLL logowanie się w ramach konta NetworkService w systemie Windows XP Home Edition, Windows XP Professional, Windows Server 2003 i w większym systemie operacyjnym.

Gdy niestandardowe liczniki dzienników są tworzone z klasą ATLServer CPerfMon w programie MMC programu perfmon, liczniki mogą nie być wyświetlane podczas przeglądania pliku dziennika, chociaż będą prawidłowo wyświetlane w widoku czasu rzeczywistego. Niestandardowe liczniki wydajności CPerfMon nie mają wystarczających uprawnień do uruchomienia w ramach usługi "Dzienniki wydajności i alerty" (smlogsvc.exe) w systemach operacyjnych Windows XP Home Edition, Windows XP Professional, Windows Server 2003 (lub nowszych). Ta usługa działa w ramach konta "NT AUTHORITY\NetworkService".

## <a name="sidsnull"></a><a name="null"></a> Identyfikatory SID:: null

Zwraca identyfikator SID SECURITY_NULL_RID.

```
CSid Null() throw(...);
```

## <a name="sidsprew2kaccess"></a><a name="prew2kaccess"></a> Identyfikatory SID::P reW2KAccess

Zwraca identyfikator SID DOMAIN_ALIAS_RID_PREW2KCOMPACCESS.

```
CSid PreW2KAccess() throw(...);
```

## <a name="sidspowerusers"></a><a name="powerusers"></a> Identyfikatory SID::P owerUsers

Zwraca identyfikator SID DOMAIN_ALIAS_RID_POWER_USERS.

```
CSid PowerUsers() throw(...);
```

## <a name="sidsprintops"></a><a name="printops"></a> Identyfikatory SID::P rintOps

Zwraca identyfikator SID DOMAIN_ALIAS_RID_PRINT_OPS.

```
CSid PrintOps() throw(...);
```

## <a name="sidsproxy"></a><a name="proxy"></a> Identyfikatory SID::P Roxy

Zwraca identyfikator SID SECURITY_PROXY_RID.

```
CSid Proxy() throw(...);
```

## <a name="sidsrasservers"></a><a name="rasservers"></a> Identyfikatory SID:: RasServers

Zwraca identyfikator SID DOMAIN_ALIAS_RID_RAS_SERVERS.

```
CSid RasServers() throw(...);
```

## <a name="sidsreplicator"></a><a name="replicator"></a> SID:: Replikator

Zwraca identyfikator SID DOMAIN_ALIAS_RID_REPLICATOR.

```
CSid Replicator() throw(...);
```

## <a name="sidsrestrictedcode"></a><a name="restrictedcode"></a> Identyfikatory SID:: RestrictedCode

Zwraca identyfikator SID SECURITY_RESTRICTED_CODE_RID.

```
CSid RestrictedCode() throw(...);
```

## <a name="sidsself"></a><a name="self"></a> Identyfikatory SID:: własne

Zwraca identyfikator SID SECURITY_PRINCIPAL_SELF_RID.

```
CSid Self() throw(...);
```

## <a name="sidsserverlogon"></a><a name="serverlogon"></a> Identyfikatory SID:: ServerLogon

Zwraca identyfikator SID SECURITY_SERVER_LOGON_RID.

```
CSid ServerLogon() throw(...);
```

## <a name="sidsservice"></a><a name="service"></a> SID:: Service

Zwraca identyfikator SID SECURITY_SERVICE_RID.

```
CSid Service() throw(...);
```

## <a name="sidssystem"></a><a name="system"></a> SID:: system

Zwraca identyfikator SID SECURITY_LOCAL_SYSTEM_RID.

```
CSid System() throw(...);
```

## <a name="sidssystemops"></a><a name="systemops"></a> Identyfikatory SID:: SystemOps

Zwraca identyfikator SID DOMAIN_ALIAS_RID_SYSTEM_OPS.

```
CSid SystemOps() throw(...);
```

## <a name="sidsterminalserver"></a><a name="terminalserver"></a> Identyfikatory SID:: TerminalServer

Zwraca identyfikator SID SECURITY_TERMINAL_SERVER_RID.

```
CSid TerminalServer() throw(...);
```

## <a name="sidsusers"></a><a name="users"></a> Identyfikatory SID:: users

Zwraca identyfikator SID DOMAIN_ALIAS_RID_USERS.

```
CSid Users() throw(...);
```

## <a name="sidsworld"></a><a name="world"></a> Identyfikatory SID:: World

Zwraca identyfikator SID SECURITY_WORLD_RID.

```
CSid World() throw(...);
```

## <a name="see-also"></a>Zobacz też

[Funkcje](../../atl/reference/atl-functions.md)
