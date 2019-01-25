---
title: Klasa CAccessToken
ms.date: 11/04/2016
f1_keywords:
- CAccessToken
- ATLSECURITY/ATL::CAccessToken
- ATLSECURITY/ATL::CAccessToken::Attach
- ATLSECURITY/ATL::CAccessToken::CheckTokenMembership
- ATLSECURITY/ATL::CAccessToken::CreateImpersonationToken
- ATLSECURITY/ATL::CAccessToken::CreatePrimaryToken
- ATLSECURITY/ATL::CAccessToken::CreateProcessAsUser
- ATLSECURITY/ATL::CAccessToken::CreateRestrictedToken
- ATLSECURITY/ATL::CAccessToken::Detach
- ATLSECURITY/ATL::CAccessToken::DisablePrivilege
- ATLSECURITY/ATL::CAccessToken::DisablePrivileges
- ATLSECURITY/ATL::CAccessToken::EnablePrivilege
- ATLSECURITY/ATL::CAccessToken::EnablePrivileges
- ATLSECURITY/ATL::CAccessToken::GetDefaultDacl
- ATLSECURITY/ATL::CAccessToken::GetEffectiveToken
- ATLSECURITY/ATL::CAccessToken::GetGroups
- ATLSECURITY/ATL::CAccessToken::GetHandle
- ATLSECURITY/ATL::CAccessToken::GetImpersonationLevel
- ATLSECURITY/ATL::CAccessToken::GetLogonSessionId
- ATLSECURITY/ATL::CAccessToken::GetLogonSid
- ATLSECURITY/ATL::CAccessToken::GetOwner
- ATLSECURITY/ATL::CAccessToken::GetPrimaryGroup
- ATLSECURITY/ATL::CAccessToken::GetPrivileges
- ATLSECURITY/ATL::CAccessToken::GetProcessToken
- ATLSECURITY/ATL::CAccessToken::GetProfile
- ATLSECURITY/ATL::CAccessToken::GetSource
- ATLSECURITY/ATL::CAccessToken::GetStatistics
- ATLSECURITY/ATL::CAccessToken::GetTerminalServicesSessionId
- ATLSECURITY/ATL::CAccessToken::GetThreadToken
- ATLSECURITY/ATL::CAccessToken::GetTokenId
- ATLSECURITY/ATL::CAccessToken::GetType
- ATLSECURITY/ATL::CAccessToken::GetUser
- ATLSECURITY/ATL::CAccessToken::HKeyCurrentUser
- ATLSECURITY/ATL::CAccessToken::Impersonate
- ATLSECURITY/ATL::CAccessToken::ImpersonateLoggedOnUser
- ATLSECURITY/ATL::CAccessToken::IsTokenRestricted
- ATLSECURITY/ATL::CAccessToken::LoadUserProfile
- ATLSECURITY/ATL::CAccessToken::LogonUser
- ATLSECURITY/ATL::CAccessToken::OpenCOMClientToken
- ATLSECURITY/ATL::CAccessToken::OpenNamedPipeClientToken
- ATLSECURITY/ATL::CAccessToken::OpenRPCClientToken
- ATLSECURITY/ATL::CAccessToken::OpenThreadToken
- ATLSECURITY/ATL::CAccessToken::PrivilegeCheck
- ATLSECURITY/ATL::CAccessToken::Revert
- ATLSECURITY/ATL::CAccessToken::SetDefaultDacl
- ATLSECURITY/ATL::CAccessToken::SetOwner
- ATLSECURITY/ATL::CAccessToken::SetPrimaryGroup
helpviewer_keywords:
- CAccessToken class
ms.assetid: bb5c5945-56a5-4083-b442-76573cee83ab
ms.openlocfilehash: e53160860211ba09114f2d4d101a2eaaf7de941f
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894249"
---
# <a name="caccesstoken-class"></a>Klasa CAccessToken

Ta klasa jest otoką dla tokenu dostępu.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
class CAccessToken
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAccessToken::~CAccessToken](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAccessToken::Attach](#attach)|Wywołaj tę metodę, aby przejąć prawo własności uchwyt token dostęp.|
|[CAccessToken::CheckTokenMembership](#checktokenmembership)|Wywołaj tę metodę w celu określenia, czy określony identyfikator SID jest włączone w `CAccessToken` obiektu.|
|[CAccessToken::CreateImpersonationToken](#createimpersonationtoken)|Wywołaj tę metodę, aby utworzyć nowy token dostępu personifikacji.|
|[CAccessToken::CreatePrimaryToken](#createprimarytoken)|Wywołaj tę metodę, aby utworzyć nowy token podstawowy.|
|[CAccessToken::CreateProcessAsUser](#createprocessasuser)|Wywołaj tę metodę, aby utworzyć nowy proces uruchomiony w kontekście zabezpieczeń użytkownika, reprezentowane przez `CAccessToken` obiektu.|
|[CAccessToken::CreateRestrictedToken](#createrestrictedtoken)|Wywołaj tę metodę, aby utworzyć nową, ograniczeniami `CAccessToken` obiektu.|
|[CAccessToken::Detach](#detach)|Wywołaj tę metodę, aby można było odwołać prawa własności tokenu dostępu.|
|[CAccessToken::DisablePrivilege](#disableprivilege)|Wywołanie tej metody, aby wyłączyć uprawnień w `CAccessToken` obiektu.|
|[CAccessToken::DisablePrivileges](#disableprivileges)|Wywołanie tej metody, aby wyłączyć co najmniej uprawnienia w `CAccessToken` obiektu.|
|[CAccessToken::EnablePrivilege](#enableprivilege)|Wywołanie tej metody, aby umożliwić uprawnień w `CAccessToken` obiektu.|
|[CAccessToken::EnablePrivileges](#enableprivileges)|Wywołanie tej metody, aby włączyć co najmniej uprawnienia w `CAccessToken` obiektu.|
|[CAccessToken::GetDefaultDacl](#getdefaultdacl)|Wywołaj tę metodę, aby zwrócić `CAccessToken` obiektu domyślnej listy DACL.|
|[CAccessToken::GetEffectiveToken](#geteffectivetoken)|Wywołaj tę metodę, aby uzyskać `CAccessToken` obiektu równa tokenu dostępu dla bieżącego wątku.|
|[CAccessToken::GetGroups](#getgroups)|Wywołaj tę metodę, aby zwrócić `CAccessToken` obiektu tokenu grup.|
|[CAccessToken::GetHandle](#gethandle)|Wywołaj tę metodę można pobrać dojścia do tokena dostępu.|
|[CAccessToken::GetImpersonationLevel](#getimpersonationlevel)|Wywołaj tę metodę, aby uzyskać poziom personifikacji z tokenu dostępu.|
|[CAccessToken::GetLogonSessionId](#getlogonsessionid)|Wywołanie tej metody można pobrać Identyfikatora sesji logowania, które są skojarzone z `CAccessToken` obiektu.|
|[CAccessToken::GetLogonSid](#getlogonsid)|Wywołaj tę metodę w celu pobrania identyfikatora SID logowania skojarzone z `CAccessToken` obiektu.|
|[CAccessToken::GetOwner](#getowner)|Wywołanie tej metody można pobrać skojarzony właściciel `CAccessToken` obiektu.|
|[CAccessToken::GetPrimaryGroup](#getprimarygroup)|Wywołanie tej metody można pobrać skojarzone z grupą podstawową `CAccessToken` obiektu.|
|[CAccessToken::GetPrivileges](#getprivileges)|Wywołanie tej metody, aby uzyskać uprawnienia skojarzone z `CAccessToken` obiektu.|
|[CAccessToken::GetProcessToken](#getprocesstoken)|Wywołaj tę metodę, aby zainicjować `CAccessToken` przy użyciu tokenu dostępu z danego procesu.|
|[CAccessToken::GetProfile](#getprofile)|Wywołanie tej metody można pobrać uchwytu, wskazując skojarzony profil użytkownika `CAccessToken` obiektu.|
|[CAccessToken::GetSource](#getsource)|Wywołanie tej metody można pobrać źródło `CAccessToken` obiektu.|
|[CAccessToken::GetStatistics](#getstatistics)|Wywołanie tej metody, aby uzyskać informacje związane z `CAccessToken` obiektu.|
|[CAccessToken::GetTerminalServicesSessionId](#getterminalservicessessionid)|Wywołanie tej metody, aby uzyskać identyfikator sesji usług terminalowych skojarzony `CAccessToken` obiektu.|
|[CAccessToken::GetThreadToken](#getthreadtoken)|Wywołaj tę metodę, aby zainicjować `CAccessToken` przy użyciu tokenu z danym wątku.|
|[CAccessToken::GetTokenId](#gettokenid)|Wywołanie tej metody można pobrać tokenu identyfikator skojarzony z `CAccessToken` obiektu.|
|[CAccessToken::GetType](#gettype)|Wywołanie tej metody można uzyskać tokenu typu `CAccessToken` obiektu.|
|[CAccessToken::GetUser](#getuser)|Wywołanie tej metody, aby zidentyfikować użytkownika skojarzonego z `CAccessToken` obiektu.|
|[CAccessToken::HKeyCurrentUser](#hkeycurrentuser)|Wywołanie tej metody można pobrać uchwytu, wskazując skojarzony profil użytkownika `CAccessToken` obiektu.|
|[CAccessToken::Impersonate](#impersonate)|Wywołanie tej metody, aby przypisać personifikacji `CAccessToken` wątku.|
|[CAccessToken::ImpersonateLoggedOnUser](#impersonateloggedonuser)|Wywołaj tę metodę, aby zezwolić na wątku wywołującego do personifikacji w kontekście zabezpieczeń zalogowanego użytkownika.|
|[CAccessToken::IsTokenRestricted](#istokenrestricted)|Wywołaj tę metodę, aby sprawdzić, czy `CAccessToken` obiekt zawiera listę identyfikatorów SID ograniczone.|
|[CAccessToken::LoadUserProfile](#loaduserprofile)|Wywołaj tę metodę, aby załadować profil użytkownika skojarzony z `CAccessToken` obiektu.|
|[CAccessToken::LogonUser](#logonuser)|Wywołaj tę metodę, aby utworzyć sesję logowania dla użytkownika skojarzonego z danego poświadczenia.|
|[CAccessToken::OpenCOMClientToken](#opencomclienttoken)|Wywołanie tej metody z w ramach serwera COM, obsługa wywołania klienta można zainicjować `CAccessToken` przy użyciu tokenu dostępu z klientów modelu COM.|
|[CAccessToken::OpenNamedPipeClientToken](#opennamedpipeclienttoken)|Tę metodę należy wywołać z w ramach serwera żądania pobierania przez nazwany potok zainicjować `CAccessToken` przy użyciu tokenu dostępu od klienta.|
|[CAccessToken::OpenRPCClientToken](#openrpcclienttoken)|Wywołanie tej metody z w ramach wywołania RPC klienta można zainicjować obsługi serwera `CAccessToken` przy użyciu tokenu dostępu od klienta.|
|[CAccessToken::OpenThreadToken](#openthreadtoken)|Wywołaj tę metodę, aby ustawić poziom personifikacji i następnie zainicjowanie `CAccessToken` przy użyciu tokenu z danym wątku.|
|[CAccessToken::PrivilegeCheck](#privilegecheck)|Wywołaj tę metodę w celu określenia, czy określony zestaw uprawnień są włączone w `CAccessToken` obiektu.|
|[CAccessToken::Revert](#revert)|Wywołaj tę metodę, aby zatrzymać wątek, który jest przy użyciu tokenu personifikacji.|
|[CAccessToken::SetDefaultDacl](#setdefaultdacl)|Wywołaj tę metodę, aby ustawić wartości domyślne listy DACL `CAccessToken` obiektu.|
|[CAccessToken::SetOwner](#setowner)|Wywołaj tę metodę, aby ustawić właściciela `CAccessToken` obiektu.|
|[CAccessToken::SetPrimaryGroup](#setprimarygroup)|Wywołanie tej metody, aby ustawić podstawowej grupy `CAccessToken` obiektu.|

## <a name="remarks"></a>Uwagi

[Token dostępu](/windows/desktop/SecAuthZ/access-tokens) jest obiektem, w tym artykule opisano proces lub wątek kontekstu zabezpieczeń, która jest przydzielona do każdego użytkownika zalogowanego w systemie Windows.

Wprowadzenie do modelu kontroli dostępu w Windows, zobacz [kontroli dostępu](/windows/desktop/SecAuthZ/access-control) w zestawie Windows SDK.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

##  <a name="attach"></a>  CAccessToken::Attach

Wywołaj tę metodę, aby przejąć prawo własności uchwyt token dostęp.

```
void Attach(HANDLE hToken) throw();
```

### <a name="parameters"></a>Parametry

*hToken*<br/>
Dojście do tokena dostępu.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania, wystąpi błąd asercji Jeśli `CAccessToken` obiekt ma już własności tokenu dostępu.

##  <a name="dtor"></a>  CAccessToken:: ~ CAccessToken

Destruktor.

```
virtual ~CAccessToken() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby.

##  <a name="checktokenmembership"></a>  CAccessToken::CheckTokenMembership

Wywołaj tę metodę w celu określenia, czy określony identyfikator SID jest włączone w `CAccessToken` obiektu.

```
bool CheckTokenMembership(
    const CSid& rSid,
    bool* pbIsMember) const throw(...);
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
Odwołanie do [klasa CSid](../../atl/reference/csid-class.md) obiektu.

*pbIsMember*<br/>
Wskaźnik do zmiennej, która otrzymuje wyniki sprawdzania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

`CheckTokenMembership` Metoda sprawdza obecność identyfikatora SID w użytkowników i grup identyfikatory SID z tokenu dostępu. Jeśli identyfikator SID jest obecny i ma atrybut SE_GROUP_ENABLED *pbIsMember* jest ustawiona na TRUE; w przeciwnym razie, jest ustawiana na wartość FAŁSZ.

W kompilacjach debugowania, wystąpi błąd asercji Jeśli *pbIsMember* nie jest prawidłowy wskaźnik.

> [!NOTE]
>  `CAccessToken` Obiekt musi być token personifikacji i nie token podstawowy.

##  <a name="createimpersonationtoken"></a>  CAccessToken::CreateImpersonationToken

Wywołaj tę metodę, aby utworzyć token dostępu personifikacji.

```
bool CreateImpersonationToken(
    CAccessToken* pImp,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) const throw(...);
```

### <a name="parameters"></a>Parametry

*pImp*<br/>
Wskaźnik do nowego `CAccessToken` obiektu.

*sil*<br/>
Określa [SECURITY_IMPERSONATION_LEVEL](/windows/desktop/api/winnt/ne-winnt-_security_impersonation_level) wyliczany typ, który dostarcza poziom personifikacji nowy token.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

`CreateImpersonationToken` wywołania [DuplicateToken](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-duplicatetoken) do utworzenia nowego tokenu personifikacji.

##  <a name="createprimarytoken"></a>  CAccessToken::CreatePrimaryToken

Wywołaj tę metodę, aby utworzyć nowy token podstawowy.

```
bool CreatePrimaryToken(
    CAccessToken* pPri,
    DWORD dwDesiredAccess = MAXIMUM_ALLOWED,
    const CSecurityAttributes* pTokenAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pPri*<br/>
Wskaźnik do nowego `CAccessToken` obiektu.

*dwDesiredAccess*<br/>
Określa prawa dostępu do żądanego dla nowego tokenu. Domyślnie MAXIMUM_ALLOWED, żąda wszystkie prawa dostępu, które są prawidłowe dla obiektu wywołującego. Zobacz [prawa dostępu i maski dostępu](/windows/desktop/SecAuthZ/access-rights-and-access-masks) więcej włączone prawa dostępu.

*pTokenAttributes*<br/>
Wskaźnik do [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) struktura, która określa deskryptora zabezpieczeń dla nowego tokenu i określa, czy procesy podrzędne mogą dziedziczyć token. Jeśli *pTokenAttributes* ma wartość NULL, token pobiera domyślny deskryptor zabezpieczeń i nie może być dziedziczona uchwytu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

`CreatePrimaryToken` wywołania [DuplicateTokenEx](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-duplicatetokenex) do utworzenia nowego tokenu podstawowego.

##  <a name="createprocessasuser"></a>  CAccessToken::CreateProcessAsUser

Wywołaj tę metodę, aby utworzyć nowy proces uruchomiony w kontekście zabezpieczeń użytkownika, reprezentowane przez `CAccessToken` obiektu.

```
bool CreateProcessAsUser(
    LPCTSTR pApplicationName,
    LPTSTR pCommandLine,
    LPPROCESS_INFORMATION pProcessInformation,
    LPSTARTUPINFO pStartupInfo,
    DWORD dwCreationFlags = NORMAL_PRIORITY_CLASS,
    bool bLoadProfile = false,
    const CSecurityAttributes* pProcessAttributes = NULL,
    const CSecurityAttributes* pThreadAttributes = NULL,
    bool bInherit = false,
    LPCTSTR pCurrentDirectory = NULL) throw();
```

### <a name="parameters"></a>Parametry

*pApplicationName*<br/>
Wskaźnik na ciąg zakończony znakiem null Określa moduł do wykonania. Ten parametr nie może być NULL.

*pCommandLine*<br/>
Wskaźnik na ciąg zakończony znakiem null, który określa wiersz poleceń do wykonania.

*pProcessInformation*<br/>
Wskaźnik do [PROCESS_INFORMATION](/windows/desktop/api/processthreadsapi/ns-processthreadsapi-_process_information) strukturę, która otrzymuje informacje identyfikacyjne dotyczące nowego procesu.

*pStartupInfo*<br/>
Wskaźnik do [STARTUPINFO](/windows/desktop/api/processthreadsapi/ns-processthreadsapi-_startupinfoa) strukturę, która określa, jak powinno pojawić się główne okno nowy proces.

*dwCreationFlags*<br/>
Określa dodatkowe flagi, priorytet i utworzenia procesu. Zobacz opis funkcji Win32 [CreateProcessAsUser](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessasusera) listę flag.

*bLoadProfile*<br/>
W przypadku opcji TRUE profil użytkownika jest ładowany z [LoadUserProfile](/windows/desktop/api/userenv/nf-userenv-loaduserprofilea).

*pProcessAttributes*<br/>
Wskaźnik do [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) struktura, która określa deskryptora zabezpieczeń dla nowego procesu i określa, czy procesy podrzędne mogą dziedziczyć zwracany uchwyt. Jeśli *pProcessAttributes* ma wartość NULL, proces pobiera domyślny deskryptor zabezpieczeń i nie może być dziedziczona uchwytu.

*pThreadAttributes*<br/>
Wskaźnik do [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) struktura, która określa deskryptora zabezpieczeń dla nowego wątku i określa, czy procesy podrzędne mogą dziedziczyć zwracany uchwyt. Jeśli *pThreadAttributes* ma wartość NULL, wątek pobiera domyślny deskryptor zabezpieczeń i nie może być dziedziczona uchwytu.

*bInherit*<br/>
Wskazuje, czy nowy proces dziedziczy dojść procesu wywołującego. W przypadku opcji TRUE każdy dziedziczne otwarte dojście w proces wywołujący jest dziedziczona przez nowy proces. Uchwyty odziedziczone mają takie same uprawnienia wartość i dostępem jako oryginalnego obsługuje.

*pCurrentDirectory*<br/>
Wskaźnik na ciąg zakończony znakiem null, który określa bieżący dysk i katalog dla nowego procesu. Ciąg musi być pełną ścieżką, która zawiera literę dysku. Jeśli ten parametr ma wartość NULL, nowy proces, będzie miał ten sam bieżącego dysku i katalogu jako procesu wywołującego.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

`CreateProcessAsUser` używa `CreateProcessAsUser` funkcji Win32, aby utworzyć nowy proces, który jest uruchamiany w kontekście zabezpieczeń użytkownika, reprezentowane przez `CAccessToken` obiektu. Zobacz opis [CreateProcessAsUser](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessasusera) funkcja pełne omówienie wymagane parametry.

Metoda ta powiedzie się `CAccessToken` obiekt musi przechowywać AssignPrimaryToken (chyba że jest tokenu ograniczonego) i IncreaseQuota uprawnień.

##  <a name="createrestrictedtoken"></a>  CAccessToken::CreateRestrictedToken

Wywołaj tę metodę, aby utworzyć nową, ograniczeniami `CAccessToken` obiektu.

```
bool CreateRestrictedToken(
    CAccessToken* pRestrictedToken,
    const CTokenGroups& SidsToDisable,
    const CTokenGroups& SidsToRestrict,
    const CTokenPrivileges& PrivilegesToDelete = CTokenPrivileges()) const throw(...);
```

### <a name="parameters"></a>Parametry

*pRestrictedToken*<br/>
Nowe, ograniczeniami `CAccessToken` obiektu.

*: SidsToDisable*<br/>
A `CTokenGroups` obiekt, który określa tylko odmowa identyfikatory SID.

*SidsToRestrict*<br/>
A `CTokenGroups` obiekt, który określa ograniczenie identyfikatory SID.

*PrivilegesToDelete*<br/>
A `CTokenPrivileges` obiekt, który określa uprawnienia do usunięcia w tokenu ograniczone. Domyślnie tworzy pustego obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

`CreateRestrictedToken` używa [CreateRestrictedToken](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-createrestrictedtoken) funkcji Win32, aby utworzyć nową `CAccessToken` obiektu z ograniczeniami.

> [!IMPORTANT]
>  Korzystając z `CreateRestrictedToken`, upewnij się, że: istniejący token jest prawidłowy (i nie jest podana przez użytkownika) i *: SidsToDisable* i *PrivilegesToDelete* są prawidłowe (i nie jest podana przez użytkownika). Jeśli metoda zwraca wartość FALSE, odmowa funkcji.

##  <a name="detach"></a>  CAccessToken::Detach

Wywołaj tę metodę, aby można było odwołać prawa własności tokenu dostępu.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca uchwyt do `CAccessToken` którego została odłączona.

### <a name="remarks"></a>Uwagi

Ta metoda odwołuje `CAccessToken`firmy własności tokenu dostępu.

##  <a name="disableprivilege"></a>  CAccessToken::DisablePrivilege

Wywołanie tej metody, aby wyłączyć uprawnień w `CAccessToken` obiektu.

```
bool DisablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*pszPrivilege*<br/>
Wskaźnik do ciągu zawierającego uprawnień, aby wyłączyć w `CAccessToken` obiektu.

*pPreviousState*<br/>
Wskaźnik do `CTokenPrivileges` obiektu, który będzie zawierać poprzedni stan uprawnienia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

##  <a name="disableprivileges"></a>  CAccessToken::DisablePrivileges

Wywołanie tej metody, aby wyłączyć co najmniej uprawnienia w `CAccessToken` obiektu.

```
bool DisablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*rPrivileges*<br/>
Wskaźnik na tablicę ciągów, które zawierają uprawnień, aby wyłączyć w `CAccessToken` obiektu.

*pPreviousState*<br/>
Wskaźnik do `CTokenPrivileges` obiektu, który będzie zawierać poprzedni stan uprawnienia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

##  <a name="enableprivilege"></a>  CAccessToken::EnablePrivilege

Wywołanie tej metody, aby umożliwić uprawnień w `CAccessToken` obiektu.

```
bool EnablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*pszPrivilege*<br/>
Wskaźnik do ciągu zawierającego uprawnień do włączenia w `CAccessToken` obiektu.

*pPreviousState*<br/>
Wskaźnik do `CTokenPrivileges` obiektu, który będzie zawierać poprzedni stan uprawnienia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

##  <a name="enableprivileges"></a>  CAccessToken::EnablePrivileges

Wywołanie tej metody, aby włączyć co najmniej uprawnienia w `CAccessToken` obiektu.

```
bool EnablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*rPrivileges*<br/>
Wskaźnik na tablicę ciągów, które zawierają uprawnień do włączenia w `CAccessToken` obiektu.

*pPreviousState*<br/>
Wskaźnik do `CTokenPrivileges` obiektu, który będzie zawierać poprzedni stan uprawnienia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

##  <a name="getdefaultdacl"></a>  CAccessToken::GetDefaultDacl

Wywołaj tę metodę, aby zwrócić `CAccessToken` obiektu domyślnej listy DACL.

```
bool GetDefaultDacl(CDacl* pDacl) const throw(...);
```

### <a name="parameters"></a>Parametry

*pDacl*<br/>
Wskaźnik do [klasa CDacl](../../atl/reference/cdacl-class.md) obiektu, który otrzyma `CAccessToken` obiektu domyślnej listy DACL.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli domyślnej listy DACL zostało odzyskane, wartość FALSE w przeciwnym razie.

##  <a name="geteffectivetoken"></a>  CAccessToken::GetEffectiveToken

Wywołaj tę metodę, aby uzyskać `CAccessToken` obiektu równa tokenu dostępu dla bieżącego wątku.

```
bool GetEffectiveToken(DWORD dwDesiredAccess) throw();
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Określa maskę dostępu określająca żądany typ dostępu do tokena dostępu. Te typy żądanego dostępu są porównywane z listy DACL tokenu, aby określić, których dostępów do udzielono lub odmówiono.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

##  <a name="getgroups"></a>  CAccessToken::GetGroups

Wywołaj tę metodę, aby zwrócić `CAccessToken` obiektu tokenu grup.

```
bool GetGroups(CTokenGroups* pGroups) const throw(...);
```

### <a name="parameters"></a>Parametry

*pGroups*<br/>
Wskaźnik do [klasa CTokenGroups](../../atl/reference/ctokengroups-class.md) obiektu, który otrzyma informacje o grupie.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

##  <a name="gethandle"></a>  CAccessToken::GetHandle

Wywołaj tę metodę można pobrać dojścia do tokena dostępu.

```
HANDLE GetHandle() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca uchwyt do `CAccessToken` token dostępu tego obiektu.

##  <a name="getimpersonationlevel"></a>  CAccessToken::GetImpersonationLevel

Wywołaj tę metodę, aby uzyskać poziom personifikacji z tokenu dostępu.

```
bool GetImpersonationLevel(
    SECURITY_IMPERSONATION_LEVEL* pImpersonationLevel) const throw(...);
```

### <a name="parameters"></a>Parametry

*pImpersonationLevel*<br/>
Wskaźnik do [SECURITY_IMPERSONATION_LEVEL](/windows/desktop/api/winnt/ne-winnt-_security_impersonation_level) typ wyliczeniowy, który otrzyma informacje o poziomie personifikacji.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

##  <a name="getlogonsessionid"></a>  CAccessToken::GetLogonSessionId

Wywołanie tej metody można pobrać Identyfikatora sesji logowania, które są skojarzone z `CAccessToken` obiektu.

```
bool GetLogonSessionId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pluid*<br/>
Wskaźnik do [LUID](/windows/desktop/api/winnt/ns-winnt-_luid) której zostanie wyświetlony identyfikator sesji logowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania, wystąpi błąd asercji Jeśli *pluid* jest nieprawidłową wartością.

##  <a name="getlogonsid"></a>  CAccessToken::GetLogonSid

Wywołaj tę metodę w celu pobrania identyfikatora SID logowania skojarzone z `CAccessToken` obiektu.

```
bool GetLogonSid(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSid*<br/>
Wskaźnik do [klasa CSid](../../atl/reference/csid-class.md) obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania, wystąpi błąd asercji Jeśli *pSid* jest nieprawidłową wartością.

##  <a name="getowner"></a>  CAccessToken::GetOwner

Wywołanie tej metody można pobrać skojarzony właściciel `CAccessToken` obiektu.

```
bool GetOwner(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSid*<br/>
Wskaźnik do [klasa CSid](../../atl/reference/csid-class.md) obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Właściciel jest ustawiany domyślnie na wszystkie obiekty utworzone ten token dostępu w czasie działania.

##  <a name="getprimarygroup"></a>  CAccessToken::GetPrimaryGroup

Wywołanie tej metody można pobrać skojarzone z grupą podstawową `CAccessToken` obiektu.

```
bool GetPrimaryGroup(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSid*<br/>
Wskaźnik do [klasa CSid](../../atl/reference/csid-class.md) obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Grupa jest ustawiona domyślnie na wszystkie obiekty utworzone ten token dostępu w czasie działania.

##  <a name="getprivileges"></a>  CAccessToken::GetPrivileges

Wywołanie tej metody, aby uzyskać uprawnienia skojarzone z `CAccessToken` obiektu.

```
bool GetPrivileges(CTokenPrivileges* pPrivileges) const throw(...);
```

### <a name="parameters"></a>Parametry

*pPrivileges*<br/>
Wskaźnik do [klasa CTokenPrivileges](../../atl/reference/ctokenprivileges-class.md) obiektu, który otrzyma uprawnienia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

##  <a name="getprocesstoken"></a>  CAccessToken::GetProcessToken

Wywołaj tę metodę, aby zainicjować `CAccessToken` przy użyciu tokenu dostępu z danego procesu.

```
bool GetProcessToken(DWORD dwDesiredAccess, HANDLE hProcess = NULL) throw();
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Określa maskę dostępu określająca żądany typ dostępu do tokena dostępu. Te typy żądanego dostępu są porównywane z listy DACL tokenu, aby określić, których dostępów do udzielono lub odmówiono.

*hProcess*<br/>
Dojście do procesu, którego token dostępu jest otwarty. Jeśli jest używana domyślna wartość NULL, jest używany bieżący proces.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Wywołania [OpenProcessToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-openprocesstoken) funkcję Win32.

##  <a name="getprofile"></a>  CAccessToken::GetProfile

Wywołanie tej metody można pobrać uchwytu, wskazując skojarzony profil użytkownika `CAccessToken` obiektu.

```
HANDLE GetProfile() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca uchwyt wskazujący profilu użytkownika lub wartość NULL, jeśli nie istnieje profil.

##  <a name="getsource"></a>  CAccessToken::GetSource

Wywołanie tej metody można pobrać źródło `CAccessToken` obiektu.

```
bool GetSource(TOKEN_SOURCE* pSource) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSource*<br/>
Wskaźnik do [TOKEN_SOURCE](/windows/desktop/api/winnt/ns-winnt-_token_source) struktury.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

##  <a name="getstatistics"></a>  CAccessToken::GetStatistics

Wywołanie tej metody, aby uzyskać informacje związane z `CAccessToken` obiektu.

```
bool GetStatistics(TOKEN_STATISTICS* pStatistics) const throw(...);
```

### <a name="parameters"></a>Parametry

*pStatistics*<br/>
Wskaźnik do [TOKEN_STATISTICS](/windows/desktop/api/winnt/ns-winnt-_token_statistics) struktury.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

##  <a name="getterminalservicessessionid"></a>  CAccessToken::GetTerminalServicesSessionId

Wywołanie tej metody, aby uzyskać identyfikator sesji usług terminalowych skojarzony `CAccessToken` obiektu.

```
bool GetTerminalServicesSessionId(DWORD* pdwSessionId) const throw(...);
```

### <a name="parameters"></a>Parametry

*pdwSessionId*<br/>
Identyfikator sesji usług terminalowych.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

##  <a name="getthreadtoken"></a>  CAccessToken::GetThreadToken

Wywołaj tę metodę, aby zainicjować `CAccessToken` przy użyciu tokenu z danym wątku.

```
bool GetThreadToken(
    DWORD dwDesiredAccess,
    HANDLE hThread = NULL,
    bool bOpenAsSelf = true) throw();
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Określa maskę dostępu określająca żądany typ dostępu do tokena dostępu. Te typy żądanego dostępu są porównywane z listy DACL tokenu, aby określić, których dostępów do udzielono lub odmówiono.

*hThread*<br/>
Uchwyt do wątku, którego token dostępu jest otwarty.

*bOpenAsSelf*<br/>
Wskazuje, czy kontroli dostępu ma zostać wykonane w stosunku do kontekstu zabezpieczeń wywołania wątku `GetThreadToken` metody lub dla kontekstu zabezpieczeń procesu wywołującego wątku.

Jeśli ten parametr ma wartość FALSE, kontrolę dostępu odbywa się za pomocą kontekstu zabezpieczeń dla wątku wywołującego. Jeśli wątek nie personifikuje klienta, ten kontekst zabezpieczeń może być procesu klienta. Jeśli ten parametr ma wartość TRUE, kontroli dostępu jest tworzone za pomocą kontekstu zabezpieczeń procesu wywołującego wątku.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

##  <a name="gettokenid"></a>  CAccessToken::GetTokenId

Wywołanie tej metody można pobrać tokenu identyfikator skojarzony z `CAccessToken` obiektu.

```
bool GetTokenId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pluid*<br/>
Wskaźnik do [LUID](/windows/desktop/api/winnt/ns-winnt-_luid) który otrzyma tokenu identyfikatora.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

##  <a name="gettype"></a>  CAccessToken::GetType

Wywołanie tej metody można uzyskać tokenu typu `CAccessToken` obiektu.

```
bool GetType(TOKEN_TYPE* pType) const throw(...);
```

### <a name="parameters"></a>Parametry

*pType*<br/>
Adres [TOKEN_TYPE](/windows/desktop/api/winnt/ne-winnt-_token_type) zmiennej, która w przypadku powodzenia otrzymuje typ tokenu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Typ wyliczeniowy TOKEN_TYPE zawiera wartości, które rozróżnienia między podstawowym token i token personifikacji.

##  <a name="getuser"></a>  CAccessToken::GetUser

Wywołanie tej metody, aby zidentyfikować użytkownika skojarzonego z `CAccessToken` obiektu.

```
bool GetUser(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSid*<br/>
Wskaźnik do [klasa CSid](../../atl/reference/csid-class.md) obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

##  <a name="hkeycurrentuser"></a>  CAccessToken::HKeyCurrentUser

Wywołanie tej metody można pobrać uchwytu, wskazując skojarzony profil użytkownika `CAccessToken` obiektu.

```
HKEY HKeyCurrentUser() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca uchwyt wskazujący profilu użytkownika lub wartość NULL, jeśli nie istnieje profil.

##  <a name="impersonate"></a>  CAccessToken::Impersonate

Wywołanie tej metody, aby przypisać personifikacji `CAccessToken` wątku.

```
bool Impersonate(HANDLE hThread = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*hThread*<br/>
Uchwyt do wątku, który można przypisać token personifikacji, aby. Tego dojścia musi otworzyć przy użyciu TOKEN_IMPERSONATE praw dostępu. Jeśli *hThread* ma wartość NULL, metoda powoduje, że wątek przestać korzystać z tokenu personifikacji.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania, wystąpi błąd asercji Jeśli `CAccessToken` nie ma prawidłowego wskaźnika do tokenu.

[Klasa CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) może służyć do automatycznie przywrócić tokenów dostępu spersonifikowanego.

##  <a name="impersonateloggedonuser"></a>  CAccessToken::ImpersonateLoggedOnUser

Wywołaj tę metodę, aby zezwolić na wątku wywołującego do personifikacji w kontekście zabezpieczeń zalogowanego użytkownika.

```
bool ImpersonateLoggedOnUser() const throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

> [!IMPORTANT]
>  Jeśli wywołanie funkcji personifikacja nie powiedzie się z jakiegokolwiek powodu, klient nie jest Personifikowany i żądanie klienta jest nawiązywane w kontekście zabezpieczeń procesu, z którego wykonano wywołanie. Jeśli proces działa jako konto o wysokim poziomie uprawnień lub jako członek grupy administratorów, użytkownik będzie mógł wykonywać akcje on w przeciwnym razie będzie niedozwolone. W związku z tym zawsze należy potwierdzić wartość zwracana przez tę funkcję.

##  <a name="istokenrestricted"></a>  CAccessToken::IsTokenRestricted

Wywołaj tę metodę, aby sprawdzić, czy `CAccessToken` obiekt zawiera listę identyfikatorów SID ograniczone.

```
bool IsTokenRestricted() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli obiekt zawiera listę ograniczenie identyfikatory SID, FALSE, jeśli nie ograniczenie identyfikatory SID, lub jeśli metoda nie powiedzie się.

##  <a name="loaduserprofile"></a>  CAccessToken::LoadUserProfile

Wywołaj tę metodę, aby załadować profil użytkownika skojarzony z `CAccessToken` obiektu.

```
bool LoadUserProfile() throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania, wystąpi błąd asercji Jeśli `CAccessToken` nie zawiera prawidłowego tokenu lub jeśli użytkownik profilu już istnieje.

##  <a name="logonuser"></a>  CAccessToken::LogonUser

Wywołaj tę metodę, aby utworzyć sesję logowania dla użytkownika skojarzonego z danego poświadczenia.

```
bool LogonUser(
    LPCTSTR pszUserName,
    LPCTSTR pszDomain,
    LPCTSTR pszPassword,
    DWORD dwLogonType = LOGON32_LOGON_INTERACTIVE,
    DWORD dwLogonProvider = LOGON32_PROVIDER_DEFAULT) throw();
```

### <a name="parameters"></a>Parametry

*pszUserName*<br/>
Wskaźnik na ciąg zakończony znakiem null, który określa nazwę użytkownika. Jest to nazwa konta użytkownika, aby zalogować się do.

*pszDomain*<br/>
Wskaźnik na ciąg zakończony znakiem null, który określa nazwę domeny lub serwer, którego konto bazy danych zawiera *pszUserName* konta.

*pszPassword*<br/>
Wskaźnik na ciąg zakończony znakiem null, który określa hasło zwykłego tekstu dla konta użytkownika określonego przez *pszUserName*.

*dwLogonType*<br/>
Określa typ operacji logowania do wykonania. Zobacz [funkcji LogonUser](/windows/desktop/api/winbase/nf-winbase-logonusera) Aby uzyskać więcej informacji.

*dwLogonProvider*<br/>
Określa dostawcę logowania. Zobacz [funkcji LogonUser](/windows/desktop/api/winbase/nf-winbase-logonusera) Aby uzyskać więcej informacji.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Dostęp do tokenu wynikające z logowania zostaną skojarzone z `CAccessToken`. Metoda ta powiedzie się `CAccessToken` obiekt musi przechowywać SE_TCB_NAME uprawnień, identyfikacji posiadacza jako część zaufany komputer podstawowy. Zobacz [funkcji LogonUser](/windows/desktop/api/winbase/nf-winbase-logonusera) Aby uzyskać więcej informacji na temat uprawnień wymaganych.

##  <a name="opencomclienttoken"></a>  CAccessToken::OpenCOMClientToken

Wywołanie tej metody z w ramach serwera COM, obsługa wywołania klienta można zainicjować `CAccessToken` przy użyciu tokenu dostępu z klientów modelu COM.

```
bool OpenCOMClientToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Określa maskę dostępu określająca żądany typ dostępu do tokena dostępu. Te typy żądanego dostępu są porównywane z listy DACL tokenu, aby określić, których dostępów do udzielono lub odmówiono.

*bImpersonate*<br/>
W przypadku opcji TRUE bieżącego wątku Personifikuj klienta wywołującego COM, jeśli to wywołanie zakończy się pomyślnie. W przypadku wartości FAŁSZ token dostępu zostanie otwarty, ale wątek nie będzie tokenu personifikacji po zakończeniu tego wywołania.

*bOpenAsSelf*<br/>
Wskazuje, czy kontroli dostępu ma zostać wykonane w stosunku do kontekstu zabezpieczeń wywołania wątku [GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) metody lub dla kontekstu zabezpieczeń procesu wywołującego wątku.

Jeśli ten parametr ma wartość FALSE, kontrolę dostępu odbywa się za pomocą kontekstu zabezpieczeń dla wątku wywołującego. Jeśli wątek nie personifikuje klienta, ten kontekst zabezpieczeń może być procesu klienta. Jeśli ten parametr ma wartość TRUE, kontroli dostępu jest tworzone za pomocą kontekstu zabezpieczeń procesu wywołującego wątku.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

[Klasa CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) może służyć do automatycznie przywrócić tokenów dostępu spersonifikowanego, utworzone przez ustawienie *bImpersonate* flagi na wartość TRUE.

##  <a name="opennamedpipeclienttoken"></a>  CAccessToken::OpenNamedPipeClientToken

Tę metodę należy wywołać z w ramach serwera żądania pobierania przez nazwany potok zainicjować `CAccessToken` przy użyciu tokenu dostępu od klienta.

```
bool OpenNamedPipeClientToken(
    HANDLE hPipe,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Parametry

*hPipe*<br/>
Dojście do nazwanego potoku.

*dwDesiredAccess*<br/>
Określa maskę dostępu określająca żądany typ dostępu do tokena dostępu. Te typy żądanego dostępu są porównywane z listy DACL tokenu, aby określić, których dostępów do udzielono lub odmówiono.

*bImpersonate*<br/>
W przypadku opcji TRUE bieżącego wątku Personifikuj klienta wywołującego potoku, jeśli to wywołanie zakończy się pomyślnie. W przypadku wartości FAŁSZ token dostępu zostanie otwarty, ale wątek nie będzie tokenu personifikacji po zakończeniu tego wywołania.

*bOpenAsSelf*<br/>
Wskazuje, czy kontroli dostępu ma zostać wykonane w stosunku do kontekstu zabezpieczeń wywołania wątku [GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) metody lub dla kontekstu zabezpieczeń procesu wywołującego wątku.

Jeśli ten parametr ma wartość FALSE, kontrolę dostępu odbywa się za pomocą kontekstu zabezpieczeń dla wątku wywołującego. Jeśli wątek nie personifikuje klienta, ten kontekst zabezpieczeń może być procesu klienta. Jeśli ten parametr ma wartość TRUE, kontroli dostępu jest tworzone za pomocą kontekstu zabezpieczeń procesu wywołującego wątku.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

[Klasa CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) może służyć do automatycznie przywrócić tokenów dostępu spersonifikowanego, utworzone przez ustawienie *bImpersonate* flagi na wartość TRUE.

##  <a name="openrpcclienttoken"></a>  CAccessToken::OpenRPCClientToken

Wywołanie tej metody z w ramach wywołania RPC klienta można zainicjować obsługi serwera `CAccessToken` przy użyciu tokenu dostępu od klienta.

```
bool OpenRPCClientToken(
    RPC_BINDING_HANDLE BindingHandle,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Parametry

*BindingHandle*<br/>
Dojście powiązania na serwerze, który reprezentuje powiązanie do klienta.

*dwDesiredAccess*<br/>
Określa maskę dostępu określająca żądany typ dostępu do tokena dostępu. Te typy żądanego dostępu są porównywane z listy DACL tokenu, aby określić, których dostępów do udzielono lub odmówiono.

*bImpersonate*<br/>
W przypadku opcji TRUE bieżącego wątku Personifikuj klienta wywołującego RPC, jeśli to wywołanie zakończy się pomyślnie. W przypadku wartości FAŁSZ token dostępu zostanie otwarty, ale wątek nie będzie tokenu personifikacji po zakończeniu tego wywołania.

*bOpenAsSelf*<br/>
Wskazuje, czy kontroli dostępu ma zostać wykonane w stosunku do kontekstu zabezpieczeń wywołania wątku [GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) metody lub dla kontekstu zabezpieczeń procesu wywołującego wątku.

Jeśli ten parametr ma wartość FALSE, kontrolę dostępu odbywa się za pomocą kontekstu zabezpieczeń dla wątku wywołującego. Jeśli wątek nie personifikuje klienta, ten kontekst zabezpieczeń może być procesu klienta. Jeśli ten parametr ma wartość TRUE, kontroli dostępu jest tworzone za pomocą kontekstu zabezpieczeń procesu wywołującego wątku.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

[Klasa CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) może służyć do automatycznie przywrócić tokenów dostępu spersonifikowanego, utworzone przez ustawienie *bImpersonate* flagi na wartość TRUE.

##  <a name="openthreadtoken"></a>  CAccessToken::OpenThreadToken

Wywołaj tę metodę, aby ustawić poziom personifikacji i następnie zainicjowanie `CAccessToken` przy użyciu tokenu z danym wątku.

```
bool OpenThreadToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) throw(...);
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Określa maskę dostępu określająca żądany typ dostępu do tokena dostępu. Te typy żądanego dostępu są porównywane z listy DACL tokenu, aby określić, których dostępów do udzielono lub odmówiono.

*bImpersonate*<br/>
W przypadku opcji TRUE wątku pozostanie na poziomie personifikacji żądanego po ukończeniu tej metody. W przypadku wartości FAŁSZ wątku powróci do jego oryginalnej poziom personifikacji.

*bOpenAsSelf*<br/>
Wskazuje, czy kontroli dostępu ma zostać wykonane w stosunku do kontekstu zabezpieczeń wywołania wątku [GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) metody lub dla kontekstu zabezpieczeń procesu wywołującego wątku.

Jeśli ten parametr ma wartość FALSE, kontrolę dostępu odbywa się za pomocą kontekstu zabezpieczeń dla wątku wywołującego. Jeśli wątek nie personifikuje klienta, ten kontekst zabezpieczeń może być procesu klienta. Jeśli ten parametr ma wartość TRUE, kontroli dostępu jest tworzone za pomocą kontekstu zabezpieczeń procesu wywołującego wątku.

*sil*<br/>
Określa [SECURITY_IMPERSONATION_LEVEL](/windows/desktop/api/winnt/ne-winnt-_security_impersonation_level) wyliczany typ, który dostarcza poziom personifikacji tokenów.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

`OpenThreadToken` jest podobny do [CAccessToken::GetThreadToken](#getthreadtoken), ale ustawia poziom personifikacji przed inicjowanie `CAccessToken` z tokenu dostępu dla wątku.

[Klasa CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) może służyć do automatycznie przywrócić tokenów dostępu spersonifikowanego, utworzone przez ustawienie *bImpersonate* flagi na wartość TRUE.

##  <a name="privilegecheck"></a>  CAccessToken::PrivilegeCheck

Wywołaj tę metodę w celu określenia, czy określony zestaw uprawnień są włączone w `CAccessToken` obiektu.

```
bool PrivilegeCheck(
    PPRIVILEGE_SET RequiredPrivileges,
    bool* pbResult) const throw();
```

### <a name="parameters"></a>Parametry

*RequiredPrivileges*<br/>
Wskaźnik do [PRIVILEGE_SET](/windows/desktop/api/winnt/ns-winnt-_privilege_set) struktury.

*pbResult*<br/>
Wskaźnik do wartości metody ustawia wskazuje, czy dowolne lub wszystkie określone uprawnienie są włączone w `CAccessToken` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Gdy `PrivilegeCheck` zwraca, `Attributes` z każdej [LUID_AND_ATTRIBUTES](/windows/desktop/api/winnt/ns-winnt-_luid_and_attributes) struktury jest ustawiona na SE_PRIVILEGE_USED_FOR_ACCESS, jeśli włączono odpowiednie uprawnienia. Ta metoda wywołuje [PrivilegeCheck](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-privilegecheck) funkcję Win32.

##  <a name="revert"></a>  CAccessToken::Revert

Wywołaj tę metodę, aby zatrzymać wątek z przy użyciu tokenu personifikacji.

```
bool Revert(HANDLE hThread = NULL) const throw();
```

### <a name="parameters"></a>Parametry

*hThread*<br/>
Uchwyt do wątku, aby przywrócić z personifikacji. Jeśli *hThread* ma wartość NULL, zakłada, że bieżący wątek.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Operacja cofania personifikacji tokenów mogą być wykonywane automatycznie za pomocą [klasa CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md).

##  <a name="setdefaultdacl"></a>  CAccessToken::SetDefaultDacl

Wywołaj tę metodę, aby ustawić wartości domyślne listy DACL `CAccessToken` obiektu.

```
bool SetDefaultDacl(const CDacl& rDacl) throw(...);
```

### <a name="parameters"></a>Parametry

*rDacl*<br/>
Nowe rozwiązanie domyślne [klasa CDacl](../../atl/reference/cdacl-class.md) informacji.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Domyślnie lista DACL jest DACL, używany domyślnie, gdy nowe obiekty są tworzone za pomocą tego tokenu dostępu w praktyce.

##  <a name="setowner"></a>  CAccessToken::SetOwner

Wywołaj tę metodę, aby ustawić właściciela `CAccessToken` obiektu.

```
bool SetOwner(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
[Klasa CSid](../../atl/reference/csid-class.md) obiekt zawierający informacje o właścicielu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Właściciel jest domyślnym właścicielem, który jest używany dla nowych obiektów tworzonych ten token dostępu w czasie działania.

##  <a name="setprimarygroup"></a>  CAccessToken::SetPrimaryGroup

Wywołanie tej metody, aby ustawić podstawowej grupy `CAccessToken` obiektu.

```
bool SetPrimaryGroup(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
[Klasa CSid](../../atl/reference/csid-class.md) obiekt zawierający podstawowe informacje o grupach.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Grupa podstawowa jest domyślną grupą nowych obiektów tworzonych ten token dostępu w czasie działania.

## <a name="see-also"></a>Zobacz też

[Przykładowe ATLSecurity](../../visual-cpp-samples.md)<br/>
[Tokeny dostępu](/windows/desktop/SecAuthZ/access-tokens)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
