---
title: Klasa CAccessToken
ms.date: 07/02/2019
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
ms.openlocfilehash: 33fbaae5dafaccdf7f7e6880eaa42dd68352e840
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418161"
---
# <a name="caccesstoken-class"></a>Klasa CAccessToken

Ta klasa jest otoką dla tokenu dostępu.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
class CAccessToken
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CAccessToken:: ~ CAccessToken](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CAccessToken:: Attach](#attach)|Wywołaj tę metodę, aby przejąć własność danego dojścia tokenu dostępu.|
|[CAccessToken::CheckTokenMembership](#checktokenmembership)|Wywołaj tę metodę, aby określić, czy w obiekcie `CAccessToken` jest włączony określony identyfikator SID.|
|[CAccessToken::CreateImpersonationToken](#createimpersonationtoken)|Wywołaj tę metodę, aby utworzyć nowy token dostępu personifikacji.|
|[CAccessToken::CreatePrimaryToken](#createprimarytoken)|Wywołaj tę metodę, aby utworzyć nowy token podstawowy.|
|[CAccessToken:: CreateProcessAsUser](#createprocessasuser)|Wywołaj tę metodę, aby utworzyć nowy proces uruchomiony w kontekście zabezpieczeń użytkownika reprezentowanego przez obiekt `CAccessToken`.|
|[CAccessToken::CreateRestrictedToken](#createrestrictedtoken)|Wywołaj tę metodę, aby utworzyć nowy, ograniczony obiekt `CAccessToken`.|
|[CAccessToken::D etach](#detach)|Wywołaj tę metodę, aby odwołać własność tokenu dostępu.|
|[CAccessToken::D isablePrivilege](#disableprivilege)|Wywołaj tę metodę, aby wyłączyć uprawnienie w obiekcie `CAccessToken`.|
|[CAccessToken::D isablePrivileges](#disableprivileges)|Wywołaj tę metodę, aby wyłączyć co najmniej jedno uprawnienia w obiekcie `CAccessToken`.|
|[CAccessToken::EnablePrivilege](#enableprivilege)|Wywołaj tę metodę, aby włączyć uprawnienie w obiekcie `CAccessToken`.|
|[CAccessToken::EnablePrivileges](#enableprivileges)|Wywołaj tę metodę, aby włączyć co najmniej jedno uprawnienia w obiekcie `CAccessToken`.|
|[CAccessToken::GetDefaultDacl](#getdefaultdacl)|Wywołaj tę metodę, aby zwrócić domyślną listę DACL obiektu `CAccessToken`.|
|[CAccessToken::GetEffectiveToken](#geteffectivetoken)|Wywołaj tę metodę, aby uzyskać `CAccessToken` obiekt równy tokenowi dostępu obowiązującego dla bieżącego wątku.|
|[CAccessToken:: GetGroups](#getgroups)|Wywołaj tę metodę, aby zwrócić grupy tokenów obiektu `CAccessToken`.|
|[CAccessToken:: GetHandle](#gethandle)|Wywołaj tę metodę, aby pobrać uchwyt do tokenu dostępu.|
|[CAccessToken::GetImpersonationLevel](#getimpersonationlevel)|Wywołaj tę metodę, aby uzyskać poziom personifikacji z tokenu dostępu.|
|[CAccessToken::GetLogonSessionId](#getlogonsessionid)|Wywołaj tę metodę, aby uzyskać identyfikator sesji logowania skojarzony z obiektem `CAccessToken`.|
|[CAccessToken::GetLogonSid](#getlogonsid)|Wywołaj tę metodę, aby uzyskać identyfikator SID logowania skojarzony z obiektem `CAccessToken`.|
|[CAccessToken:: getOwner](#getowner)|Wywołaj tę metodę, aby uzyskać właściciela skojarzonego z obiektem `CAccessToken`.|
|[CAccessToken:: getpodstawową](#getprimarygroup)|Wywołaj tę metodę, aby uzyskać grupę podstawową skojarzoną z obiektem `CAccessToken`.|
|[CAccessToken:: getprivileges](#getprivileges)|Wywołaj tę metodę, aby uzyskać uprawnienia skojarzone z obiektem `CAccessToken`.|
|[CAccessToken::GetProcessToken](#getprocesstoken)|Wywołaj tę metodę, aby zainicjować `CAccessToken` przy użyciu tokenu dostępu z danego procesu.|
|[CAccessToken:: getprofil](#getprofile)|Wywołaj tę metodę, aby uzyskać uchwyt wskazujący profil użytkownika skojarzony z obiektem `CAccessToken`.|
|[CAccessToken:: GetSource](#getsource)|Wywołaj tę metodę, aby uzyskać źródło obiektu `CAccessToken`.|
|[CAccessToken:: getstatistics](#getstatistics)|Wywołaj tę metodę, aby uzyskać informacje skojarzone z obiektem `CAccessToken`.|
|[CAccessToken::GetTerminalServicesSessionId](#getterminalservicessessionid)|Wywołaj tę metodę, aby uzyskać identyfikator sesji usług terminalowych skojarzony z obiektem `CAccessToken`.|
|[CAccessToken::GetThreadToken](#getthreadtoken)|Wywołaj tę metodę, aby zainicjować `CAccessToken` przy użyciu tokenu z danego wątku.|
|[CAccessToken::GetTokenId](#gettokenid)|Wywołaj tę metodę, aby uzyskać identyfikator tokenu skojarzony z obiektem `CAccessToken`.|
|[CAccessToken:: GetType](#gettype)|Wywołaj tę metodę, aby uzyskać typ tokenu obiektu `CAccessToken`.|
|[CAccessToken::GetUser](#getuser)|Wywołaj tę metodę, aby zidentyfikować użytkownika skojarzonego z obiektem `CAccessToken`.|
|[CAccessToken::HKeyCurrentUser](#hkeycurrentuser)|Wywołaj tę metodę, aby uzyskać uchwyt wskazujący profil użytkownika skojarzony z obiektem `CAccessToken`.|
|[CAccessToken:: personifikacja](#impersonate)|Wywołaj tę metodę, aby przypisać personifikację `CAccessToken` do wątku.|
|[CAccessToken:: ImpersonateLoggedOnUser —](#impersonateloggedonuser)|Wywołaj tę metodę, aby zezwolić na wątek wywołujący do personifikacji kontekstu zabezpieczeń zalogowanego użytkownika.|
|[CAccessToken::IsTokenRestricted](#istokenrestricted)|Wywołaj tę metodę, aby sprawdzić, czy obiekt `CAccessToken` zawiera listę identyfikatorów SID z ograniczeniami.|
|[CAccessToken:: LoadUserProfile](#loaduserprofile)|Wywołaj tę metodę, aby załadować profil użytkownika skojarzony z obiektem `CAccessToken`.|
|[CAccessToken:: funkcji LogonUser](#logonuser)|Wywołaj tę metodę, aby utworzyć sesję logowania dla użytkownika skojarzonego z podanym poświadczeniami.|
|[CAccessToken::OpenCOMClientToken](#opencomclienttoken)|Wywołaj tę metodę z poziomu serwera COM obsługującego wywołanie z klienta, aby zainicjować `CAccessToken` przy użyciu tokenu dostępu z klienta COM.|
|[CAccessToken::OpenNamedPipeClientToken](#opennamedpipeclienttoken)|Wywołaj tę metodę z poziomu serwera przyjmującego żądania za pośrednictwem nazwanego potoku, aby zainicjować `CAccessToken` przy użyciu tokenu dostępu z klienta.|
|[CAccessToken::OpenRPCClientToken](#openrpcclienttoken)|Wywołaj tę metodę z poziomu serwera obsługującego wywołanie z klienta RPC w celu zainicjowania `CAccessToken` przy użyciu tokenu dostępu z klienta.|
|[CAccessToken:: OpenThreadToken —](#openthreadtoken)|Wywołaj tę metodę, aby ustawić poziom personifikacji, a następnie zainicjuj `CAccessToken` przy użyciu tokenu z danego wątku.|
|[CAccessToken::P rivilegeCheck](#privilegecheck)|Wywołaj tę metodę, aby określić, czy w obiekcie `CAccessToken` jest włączony określony zestaw uprawnień.|
|[CAccessToken:: Revert](#revert)|Wywołaj tę metodę, aby zatrzymać wątek, który używa tokenu personifikacji.|
|[CAccessToken::SetDefaultDacl](#setdefaultdacl)|Wywołaj tę metodę, aby ustawić domyślną listę DACL obiektu `CAccessToken`.|
|[CAccessToken:: SetOwner](#setowner)|Wywołaj tę metodę, aby ustawić właściciela obiektu `CAccessToken`.|
|[CAccessToken:: setprimary,](#setprimarygroup)|Wywołaj tę metodę, aby ustawić grupę podstawową obiektu `CAccessToken`.|

## <a name="remarks"></a>Uwagi

[Token dostępu](/windows/win32/SecAuthZ/access-tokens) jest obiektem opisującym kontekst zabezpieczeń procesu lub wątku i jest przypisywany do każdego użytkownika zalogowanego w systemie Windows.

Aby zapoznać się z wprowadzeniem do modelu kontroli dostępu w systemie Windows, zobacz [Access Control](/windows/win32/SecAuthZ/access-control) w Windows SDK.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity. h

##  <a name="attach"></a>CAccessToken:: Attach

Wywołaj tę metodę, aby przejąć własność danego dojścia tokenu dostępu.

```
void Attach(HANDLE hToken) throw();
```

### <a name="parameters"></a>Parametry

*hToken*<br/>
Dojście do tokenu dostępu.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli obiekt `CAccessToken` ma już własność tokenu dostępu.

##  <a name="dtor"></a>CAccessToken:: ~ CAccessToken

Destruktor.

```
virtual ~CAccessToken() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzieloną zasoby.

##  <a name="checktokenmembership"></a>CAccessToken::CheckTokenMembership

Wywołaj tę metodę, aby określić, czy w obiekcie `CAccessToken` jest włączony określony identyfikator SID.

```
bool CheckTokenMembership(
    const CSid& rSid,
    bool* pbIsMember) const throw(...);
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
Odwołanie do obiektu [klasy CSid](../../atl/reference/csid-class.md) .

*pbIsMember*<br/>
Wskaźnik do zmiennej, która otrzymuje wyniki kontroli.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Metoda `CheckTokenMembership` sprawdza obecność identyfikatora SID w identyfikatorach SID użytkowników i grup tokenu dostępu. Jeśli identyfikator SID jest obecny i ma atrybut SE_GROUP_ENABLED, *pbIsMember* jest ustawiona na wartość true; w przeciwnym razie jest ustawiony na wartość FALSE.

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli *pbIsMember* nie jest prawidłowym wskaźnikiem.

> [!NOTE]
>  Obiekt `CAccessToken` musi być tokenem personifikacji, a nie tokenem podstawowym.

##  <a name="createimpersonationtoken"></a>CAccessToken::CreateImpersonationToken

Wywołaj tę metodę, aby utworzyć token dostępu personifikacji.

```
bool CreateImpersonationToken(
    CAccessToken* pImp,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) const throw(...);
```

### <a name="parameters"></a>Parametry

*pImp*<br/>
Wskaźnik do nowego obiektu `CAccessToken`.

*SIL*<br/>
Określa [SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level) typ wyliczeniowy, który dostarcza poziom personifikacji nowego tokenu.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

`CreateImpersonationToken` wywołania [operacja duplicatetoken](/windows/win32/api/securitybaseapi/nf-securitybaseapi-duplicatetoken) do utworzenia nowego tokenu personifikacji.

##  <a name="createprimarytoken"></a>CAccessToken::CreatePrimaryToken

Wywołaj tę metodę, aby utworzyć nowy token podstawowy.

```
bool CreatePrimaryToken(
    CAccessToken* pPri,
    DWORD dwDesiredAccess = MAXIMUM_ALLOWED,
    const CSecurityAttributes* pTokenAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pPri*<br/>
Wskaźnik do nowego obiektu `CAccessToken`.

*dwDesiredAccess*<br/>
Określa żądane prawa dostępu dla nowego tokenu. Wartość domyślna, MAXIMUM_ALLOWED, żąda wszystkich praw dostępu, które są prawidłowe dla obiektu wywołującego. Aby uzyskać więcej informacji na temat praw dostępu, zobacz temat [prawa dostępu i Maska dostępu](/windows/win32/SecAuthZ/access-rights-and-access-masks) .

*pTokenAttributes*<br/>
Wskaźnik do struktury [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) , która określa deskryptor zabezpieczeń dla nowego tokenu i określa, czy procesy podrzędne mogą dziedziczyć token. Jeśli *pTokenAttributes* ma wartość null, token Pobiera domyślny deskryptor zabezpieczeń, a uchwyt nie może być dziedziczony.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

`CreatePrimaryToken` wywołuje [DuplicateTokenEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-duplicatetokenex) , aby utworzyć nowy token podstawowy.

##  <a name="createprocessasuser"></a>CAccessToken:: CreateProcessAsUser

Wywołaj tę metodę, aby utworzyć nowy proces uruchomiony w kontekście zabezpieczeń użytkownika reprezentowanego przez obiekt `CAccessToken`.

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
Wskaźnik na ciąg zakończony znakiem null, który określa moduł do wykonania. Ten parametr nie może mieć wartości NULL.

*pCommandLine*<br/>
Wskaźnik na ciąg zakończony znakiem null, który określa wiersz polecenia do wykonania.

*pProcessInformation*<br/>
Wskaźnik do [struktury PROCESS_INFORMATION](/windows/win32/api/processthreadsapi/ns-processthreadsapi-process_information) , która otrzymuje informacje identyfikacyjne o nowym procesie.

*pStartupInfo*<br/>
Wskaźnik do struktury [STARTUPINFO](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfow) , który określa sposób wyświetlania głównego okna dla nowego procesu.

*dwCreationFlags*<br/>
Określa dodatkowe flagi kontrolujące klasę priorytetu i proces tworzenia procesu. Zobacz funkcję Win32 [CreateProcessAsUser](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessasuserw) , aby zapoznać się z listą flag.

*bLoadProfile*<br/>
W przypadku wartości TRUE profil użytkownika jest ładowany z [loadUserProfile](/windows/win32/api/userenv/nf-userenv-loaduserprofilew).

*pProcessAttributes*<br/>
Wskaźnik do struktury [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) , która określa deskryptor zabezpieczeń dla nowego procesu i określa, czy procesy podrzędne mogą dziedziczyć zwracany uchwyt. Jeśli *pProcessAttributes* ma wartość null, proces Pobiera domyślny deskryptor zabezpieczeń, a uchwyt nie może być dziedziczony.

*pThreadAttributes*<br/>
Wskaźnik do struktury [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) , która określa deskryptor zabezpieczeń dla nowego wątku i określa, czy procesy podrzędne mogą dziedziczyć zwracany uchwyt. Jeśli *pThreadAttributes* ma wartość null, wątek Pobiera domyślny deskryptor zabezpieczeń, a uchwyt nie może być dziedziczony.

*bInherit*<br/>
Wskazuje, czy nowy proces dziedziczy uchwyty z procesu wywołującego. Jeśli wartość jest równa TRUE, każdy Dziedziczony otwarty uchwyt w procesie wywołującym jest dziedziczony przez nowy proces. Dziedziczone dojścia mają takie same uprawnienia wartości i dostępu jak oryginalne dojścia.

*pCurrentDirectory*<br/>
Wskaźnik na ciąg zakończony znakiem null, który określa bieżący dysk i katalog dla nowego procesu. Ciąg musi być pełną ścieżką, która zawiera literę dysku. Jeśli ten parametr ma wartość NULL, nowy proces będzie miał ten sam bieżący dysk i katalog co proces wywołujący.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

`CreateProcessAsUser` korzysta z funkcji `CreateProcessAsUser` Win32, aby utworzyć nowy proces, który jest uruchamiany w kontekście zabezpieczeń użytkownika reprezentowanego przez obiekt `CAccessToken`. Zobacz opis funkcji [CreateProcessAsUser](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessasuserw) , aby uzyskać pełną dyskusję na temat wymaganych parametrów.

Aby ta metoda zakończyła się pomyślnie, obiekt `CAccessToken` musi mieć AssignPrimaryToken (chyba że jest to ograniczony token) i IncreaseQuota uprawnień.

##  <a name="createrestrictedtoken"></a>CAccessToken::CreateRestrictedToken

Wywołaj tę metodę, aby utworzyć nowy, ograniczony obiekt `CAccessToken`.

```
bool CreateRestrictedToken(
    CAccessToken* pRestrictedToken,
    const CTokenGroups& SidsToDisable,
    const CTokenGroups& SidsToRestrict,
    const CTokenPrivileges& PrivilegesToDelete = CTokenPrivileges()) const throw(...);
```

### <a name="parameters"></a>Parametry

*pRestrictedToken*<br/>
Nowy, ograniczony obiekt `CAccessToken`.

*SidsToDisable*<br/>
Obiekt `CTokenGroups`, który określa identyfikatory SID tylko Odmów.

*SidsToRestrict*<br/>
Obiekt `CTokenGroups`, który określa ograniczenia identyfikatorów SID.

*PrivilegesToDelete*<br/>
Obiekt `CTokenPrivileges`, który określa uprawnienia do usunięcia w ograniczonym tokenie. Wartość domyślna powoduje utworzenie pustego obiektu.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

`CreateRestrictedToken` używa funkcji Win32 [CreateRestrictedToken](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createrestrictedtoken) do utworzenia nowego obiektu `CAccessToken` z ograniczeniami.

> [!IMPORTANT]
>  W przypadku korzystania z `CreateRestrictedToken`upewnij się, że istniejący token jest prawidłowy (i nie został wprowadzony przez użytkownika), a wartości *SidsToDisable* i *PrivilegesToDelete* są prawidłowe (i nie są wprowadzane przez użytkownika). Jeśli metoda zwraca FALSE, funkcja Odmów.

##  <a name="detach"></a>CAccessToken::D etach

Wywołaj tę metodę, aby odwołać własność tokenu dostępu.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca dojście do `CAccessToken`, która została odłączona.

### <a name="remarks"></a>Uwagi

Ta metoda odwołuje własność `CAccessToken`tokenu dostępu.

##  <a name="disableprivilege"></a>CAccessToken::D isablePrivilege

Wywołaj tę metodę, aby wyłączyć uprawnienie w obiekcie `CAccessToken`.

```
bool DisablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*pszPrivilege*<br/>
Wskaźnik do ciągu zawierającego uprawnienia, które ma zostać wyłączone w obiekcie `CAccessToken`.

*pPreviousState*<br/>
Wskaźnik do obiektu `CTokenPrivileges`, który będzie zawierać poprzedni stan uprawnień.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

##  <a name="disableprivileges"></a>CAccessToken::D isablePrivileges

Wywołaj tę metodę, aby wyłączyć co najmniej jedno uprawnienia w obiekcie `CAccessToken`.

```
bool DisablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*rPrivileges*<br/>
Wskaźnik do tablicy ciągów zawierających uprawnienia, które mają zostać wyłączone w obiekcie `CAccessToken`.

*pPreviousState*<br/>
Wskaźnik do obiektu `CTokenPrivileges`, który będzie zawierać poprzedni stan uprawnień.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

##  <a name="enableprivilege"></a>CAccessToken::EnablePrivilege

Wywołaj tę metodę, aby włączyć uprawnienie w obiekcie `CAccessToken`.

```
bool EnablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*pszPrivilege*<br/>
Wskaźnik do ciągu zawierającego uprawnienia do włączenia w obiekcie `CAccessToken`.

*pPreviousState*<br/>
Wskaźnik do obiektu `CTokenPrivileges`, który będzie zawierać poprzedni stan uprawnień.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

##  <a name="enableprivileges"></a>CAccessToken::EnablePrivileges

Wywołaj tę metodę, aby włączyć co najmniej jedno uprawnienia w obiekcie `CAccessToken`.

```
bool EnablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*rPrivileges*<br/>
Wskaźnik do tablicy ciągów zawierających uprawnienia do włączenia w obiekcie `CAccessToken`.

*pPreviousState*<br/>
Wskaźnik do obiektu `CTokenPrivileges`, który będzie zawierać poprzedni stan uprawnień.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

##  <a name="getdefaultdacl"></a>CAccessToken::GetDefaultDacl

Wywołaj tę metodę, aby zwrócić domyślną listę DACL obiektu `CAccessToken`.

```
bool GetDefaultDacl(CDacl* pDacl) const throw(...);
```

### <a name="parameters"></a>Parametry

*pDacl*<br/>
Wskaźnik do obiektu [klasy CDacl](../../atl/reference/cdacl-class.md) , który otrzyma domyślną listę DACL obiektu `CAccessToken`.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE, jeśli domyślna lista DACL została odzyskana, w przeciwnym razie FALSE.

##  <a name="geteffectivetoken"></a>CAccessToken::GetEffectiveToken

Wywołaj tę metodę, aby uzyskać `CAccessToken` obiekt równy tokenowi dostępu obowiązującego dla bieżącego wątku.

```
bool GetEffectiveToken(DWORD dwDesiredAccess) throw();
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Określa maskę dostępu określającą żądane typy dostępu do tokenu dostępu. Te typy żądanych dostępu są porównywane z LISTą DACL tokenu, aby określić, które prawa dostępu są udzielane lub odrzucane.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

##  <a name="getgroups"></a>CAccessToken:: GetGroups

Wywołaj tę metodę, aby zwrócić grupy tokenów obiektu `CAccessToken`.

```
bool GetGroups(CTokenGroups* pGroups) const throw(...);
```

### <a name="parameters"></a>Parametry

*pGroups*<br/>
Wskaźnik do obiektu [klasy CTokenGroups](../../atl/reference/ctokengroups-class.md) , który otrzyma informacje o grupie.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

##  <a name="gethandle"></a>CAccessToken:: GetHandle

Wywołaj tę metodę, aby pobrać uchwyt do tokenu dostępu.

```
HANDLE GetHandle() const throw();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca dojście do tokenu dostępu obiektu `CAccessToken`.

##  <a name="getimpersonationlevel"></a>CAccessToken::GetImpersonationLevel

Wywołaj tę metodę, aby uzyskać poziom personifikacji z tokenu dostępu.

```
bool GetImpersonationLevel(
    SECURITY_IMPERSONATION_LEVEL* pImpersonationLevel) const throw(...);
```

### <a name="parameters"></a>Parametry

*pImpersonationLevel*<br/>
Wskaźnik do [SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level) typu wyliczeniowego, który otrzyma informacje o poziomie personifikacji.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

##  <a name="getlogonsessionid"></a>CAccessToken::GetLogonSessionId

Wywołaj tę metodę, aby uzyskać identyfikator sesji logowania skojarzony z obiektem `CAccessToken`.

```
bool GetLogonSessionId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pluid*<br/>
Wskaźnik do identyfikatora [LUID](/windows/win32/api/winnt/ns-winnt-luid) , który będzie otrzymywał identyfikator sesji logowania.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli *pluid* jest nieprawidłową wartością.

##  <a name="getlogonsid"></a>CAccessToken::GetLogonSid

Wywołaj tę metodę, aby uzyskać identyfikator SID logowania skojarzony z obiektem `CAccessToken`.

```
bool GetLogonSid(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parametry

*Pusty PSID*<br/>
Wskaźnik do obiektu [klasy CSid](../../atl/reference/csid-class.md) .

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli *pusty PSID* jest nieprawidłową wartością.

##  <a name="getowner"></a>CAccessToken:: getOwner

Wywołaj tę metodę, aby uzyskać właściciela skojarzonego z obiektem `CAccessToken`.

```
bool GetOwner(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parametry

*Pusty PSID*<br/>
Wskaźnik do obiektu [klasy CSid](../../atl/reference/csid-class.md) .

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Właściciel jest ustawiany domyślnie dla wszystkich obiektów utworzonych w trakcie działania tego tokenu dostępu.

##  <a name="getprimarygroup"></a>CAccessToken:: getpodstawową

Wywołaj tę metodę, aby uzyskać grupę podstawową skojarzoną z obiektem `CAccessToken`.

```
bool GetPrimaryGroup(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parametry

*Pusty PSID*<br/>
Wskaźnik do obiektu [klasy CSid](../../atl/reference/csid-class.md) .

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Grupa jest ustawiana domyślnie dla wszystkich obiektów utworzonych w trakcie działania tego tokenu dostępu.

##  <a name="getprivileges"></a>CAccessToken:: getprivileges

Wywołaj tę metodę, aby uzyskać uprawnienia skojarzone z obiektem `CAccessToken`.

```
bool GetPrivileges(CTokenPrivileges* pPrivileges) const throw(...);
```

### <a name="parameters"></a>Parametry

*pPrivileges*<br/>
Wskaźnik do obiektu [klasy CTokenPrivileges](../../atl/reference/ctokenprivileges-class.md) , który otrzyma uprawnienia.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

##  <a name="getprocesstoken"></a>CAccessToken::GetProcessToken

Wywołaj tę metodę, aby zainicjować `CAccessToken` przy użyciu tokenu dostępu z danego procesu.

```
bool GetProcessToken(DWORD dwDesiredAccess, HANDLE hProcess = NULL) throw();
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Określa maskę dostępu określającą żądane typy dostępu do tokenu dostępu. Te typy żądanych dostępu są porównywane z LISTą DACL tokenu, aby określić, które prawa dostępu są udzielane lub odrzucane.

*hProcess*<br/>
Dojście do procesu, którego token dostępu jest otwarty. Jeśli zostanie użyta domyślna wartość NULL, używany jest bieżący proces.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Wywołuje funkcję Win32 [OpenProcessToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-openprocesstoken) .

##  <a name="getprofile"></a>CAccessToken:: getprofil

Wywołaj tę metodę, aby uzyskać uchwyt wskazujący profil użytkownika skojarzony z obiektem `CAccessToken`.

```
HANDLE GetProfile() const throw();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca dojście wskazujące profil użytkownika lub wartość NULL, jeśli profil nie istnieje.

##  <a name="getsource"></a>CAccessToken:: GetSource

Wywołaj tę metodę, aby uzyskać źródło obiektu `CAccessToken`.

```
bool GetSource(TOKEN_SOURCE* pSource) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSource*<br/>
Wskaźnik do struktury [TOKEN_SOURCE](/windows/win32/api/winnt/ns-winnt-token_source) .

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

##  <a name="getstatistics"></a>CAccessToken:: getstatistics

Wywołaj tę metodę, aby uzyskać informacje skojarzone z obiektem `CAccessToken`.

```
bool GetStatistics(TOKEN_STATISTICS* pStatistics) const throw(...);
```

### <a name="parameters"></a>Parametry

*pStatistics*<br/>
Wskaźnik do struktury [TOKEN_STATISTICS](/windows/win32/api/winnt/ns-winnt-token_statistics) .

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

##  <a name="getterminalservicessessionid"></a>CAccessToken::GetTerminalServicesSessionId

Wywołaj tę metodę, aby uzyskać identyfikator sesji usług terminalowych skojarzony z obiektem `CAccessToken`.

```
bool GetTerminalServicesSessionId(DWORD* pdwSessionId) const throw(...);
```

### <a name="parameters"></a>Parametry

*pdwSessionId*<br/>
Identyfikator sesji usług terminalowych.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

##  <a name="getthreadtoken"></a>CAccessToken::GetThreadToken

Wywołaj tę metodę, aby zainicjować `CAccessToken` przy użyciu tokenu z danego wątku.

```
bool GetThreadToken(
    DWORD dwDesiredAccess,
    HANDLE hThread = NULL,
    bool bOpenAsSelf = true) throw();
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Określa maskę dostępu określającą żądane typy dostępu do tokenu dostępu. Te typy żądanych dostępu są porównywane z LISTą DACL tokenu, aby określić, które prawa dostępu są udzielane lub odrzucane.

*hThread*<br/>
Dojście do wątku, którego token dostępu jest otwarty.

*bOpenAsSelf*<br/>
Wskazuje, czy sprawdzanie dostępu ma zostać wykonane względem kontekstu zabezpieczeń wątku wywołującego metodę `GetThreadToken` lub względem kontekstu zabezpieczeń procesu dla wątku wywołującego.

Jeśli ten parametr ma wartość FALSE, sprawdzanie dostępu odbywa się przy użyciu kontekstu zabezpieczeń dla wątku wywołującego. Jeśli wątek personifikuje klienta, ten kontekst zabezpieczeń może być procesem klienta. Jeśli ten parametr ma wartość TRUE, sprawdzanie dostępu odbywa się przy użyciu kontekstu zabezpieczeń procesu dla wątku wywołującego.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

##  <a name="gettokenid"></a>CAccessToken::GetTokenId

Wywołaj tę metodę, aby uzyskać identyfikator tokenu skojarzony z obiektem `CAccessToken`.

```
bool GetTokenId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pluid*<br/>
Wskaźnik do identyfikatora [LUID](/windows/win32/api/winnt/ns-winnt-luid) , który będzie otrzymywał Identyfikator tokenu.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

##  <a name="gettype"></a>CAccessToken:: GetType

Wywołaj tę metodę, aby uzyskać typ tokenu obiektu `CAccessToken`.

```
bool GetType(TOKEN_TYPE* pType) const throw(...);
```

### <a name="parameters"></a>Parametry

*pType*<br/>
Adres zmiennej [TOKEN_TYPE](/windows/win32/api/winnt/ne-winnt-token_type) , która po powodzeniu odbiera typ tokenu.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Typ wyliczeniowy TOKEN_TYPE zawiera wartości, które różnią się między tokenem podstawowym i tokenem personifikacji.

##  <a name="getuser"></a>CAccessToken::GetUser

Wywołaj tę metodę, aby zidentyfikować użytkownika skojarzonego z obiektem `CAccessToken`.

```
bool GetUser(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parametry

*Pusty PSID*<br/>
Wskaźnik do obiektu [klasy CSid](../../atl/reference/csid-class.md) .

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

##  <a name="hkeycurrentuser"></a>CAccessToken::HKeyCurrentUser

Wywołaj tę metodę, aby uzyskać uchwyt wskazujący profil użytkownika skojarzony z obiektem `CAccessToken`.

```
HKEY HKeyCurrentUser() const throw();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca dojście wskazujące profil użytkownika lub wartość NULL, jeśli profil nie istnieje.

##  <a name="impersonate"></a>CAccessToken:: personifikacja

Wywołaj tę metodę, aby przypisać personifikację `CAccessToken` do wątku.

```
bool Impersonate(HANDLE hThread = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*hThread*<br/>
Dojście do wątku, do którego ma zostać przypisany token personifikacji. Ten uchwyt musi być otwarty z uprawnieniami dostępu TOKEN_IMPERSONATE. Jeśli *hThread* ma wartość null, metoda powoduje zatrzymanie wątku przy użyciu tokenu personifikacji.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli `CAccessToken` nie ma prawidłowego wskaźnika do tokenu.

[Klasa CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) może być używana do automatycznego przywracania personifikowanych tokenów dostępu.

##  <a name="impersonateloggedonuser"></a>CAccessToken:: ImpersonateLoggedOnUser —

Wywołaj tę metodę, aby zezwolić na wątek wywołujący do personifikacji kontekstu zabezpieczeń zalogowanego użytkownika.

```
bool ImpersonateLoggedOnUser() const throw(...);
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

> [!IMPORTANT]
>  Jeśli wywołanie funkcji personifikacji nie powiedzie się z jakiegokolwiek powodu, klient nie zostanie personifikowany, a żądanie klienta zostanie wykonane w kontekście zabezpieczeń procesu, z którego wykonano wywołanie. Jeśli proces jest uruchomiony jako konto o wysokim poziomie uprawnień lub jako członek grupy administracyjnej, może być możliwe wykonanie akcji, które w przeciwnym razie byłyby niedozwolone. W związku z tym, wartość zwracana dla tej funkcji powinna zawsze zostać potwierdzona.

##  <a name="istokenrestricted"></a>CAccessToken::IsTokenRestricted

Wywołaj tę metodę, aby sprawdzić, czy obiekt `CAccessToken` zawiera listę identyfikatorów SID z ograniczeniami.

```
bool IsTokenRestricted() const throw();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE, jeśli obiekt zawiera listę ograniczającą identyfikatory SID, FAŁSZ Jeśli nie ma ograniczeń identyfikatorów SID lub metoda nie powiedzie się.

##  <a name="loaduserprofile"></a>CAccessToken:: LoadUserProfile

Wywołaj tę metodę, aby załadować profil użytkownika skojarzony z obiektem `CAccessToken`.

```
bool LoadUserProfile() throw(...);
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli `CAccessToken` nie zawiera prawidłowego tokenu lub jeśli profil użytkownika już istnieje.

##  <a name="logonuser"></a>CAccessToken:: funkcji LogonUser

Wywołaj tę metodę, aby utworzyć sesję logowania dla użytkownika skojarzonego z podanym poświadczeniami.

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
Wskaźnik na ciąg zakończony znakiem null, który określa nazwę użytkownika. To jest nazwa konta użytkownika, na którym należy się zalogować.

*pszDomain*<br/>
Wskaźnik na ciąg zakończony znakiem null, który określa nazwę domeny lub serwera, którego baza danych kont zawiera konto *pszUserName* .

*pszPassword*<br/>
Wskaźnik na ciąg zakończony znakiem null, który określa hasło w postaci zwykłego tekstu dla konta użytkownika określonego przez *pszUserName*.

*dwLogonType*<br/>
Określa typ operacji logowania do wykonania. Aby uzyskać więcej informacji, zobacz [funkcji LogonUser](/windows/win32/api/winbase/nf-winbase-logonuserw) .

*dwLogonProvider*<br/>
Określa dostawcę logowania. Aby uzyskać więcej informacji, zobacz [funkcji LogonUser](/windows/win32/api/winbase/nf-winbase-logonuserw) .

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Token dostępu wynikający z logowania zostanie skojarzony z `CAccessToken`. Aby ta metoda zakończyła się pomyślnie, obiekt `CAccessToken` musi mieć uprawnienia SE_TCB_NAME, które identyfikują właściciela jako część bazy zaufanych komputerów. Aby uzyskać więcej informacji na temat wymaganych uprawnień, zobacz [funkcji LogonUser](/windows/win32/api/winbase/nf-winbase-logonuserw) .

##  <a name="opencomclienttoken"></a>CAccessToken::OpenCOMClientToken

Wywołaj tę metodę z poziomu serwera COM obsługującego wywołanie z klienta, aby zainicjować `CAccessToken` przy użyciu tokenu dostępu z klienta COM.

```
bool OpenCOMClientToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Określa maskę dostępu określającą żądane typy dostępu do tokenu dostępu. Te typy żądanych dostępu są porównywane z LISTą DACL tokenu, aby określić, które prawa dostępu są udzielane lub odrzucane.

*bImpersonate*<br/>
W przypadku wartości TRUE bieżący wątek personifikuje wywołującego klienta COM, jeśli to wywołanie zakończy się pomyślnie. W przypadku wartości FALSE token dostępu zostanie otwarty, ale wątek nie będzie miał tokenu personifikacji po zakończeniu tego wywołania.

*bOpenAsSelf*<br/>
Wskazuje, czy sprawdzanie dostępu ma zostać wykonane względem kontekstu zabezpieczeń wątku wywołującego metodę [GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) lub względem kontekstu zabezpieczeń procesu dla wątku wywołującego.

Jeśli ten parametr ma wartość FALSE, sprawdzanie dostępu odbywa się przy użyciu kontekstu zabezpieczeń dla wątku wywołującego. Jeśli wątek personifikuje klienta, ten kontekst zabezpieczeń może być procesem klienta. Jeśli ten parametr ma wartość TRUE, sprawdzanie dostępu odbywa się przy użyciu kontekstu zabezpieczeń procesu dla wątku wywołującego.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

[Klasy CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) można użyć do automatycznego przywrócenia personifikowanych tokenów dostępu utworzonych przez ustawienie flagi *bImpersonate* na true.

##  <a name="opennamedpipeclienttoken"></a>CAccessToken::OpenNamedPipeClientToken

Wywołaj tę metodę z poziomu serwera przyjmującego żądania za pośrednictwem nazwanego potoku, aby zainicjować `CAccessToken` przy użyciu tokenu dostępu z klienta.

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
Określa maskę dostępu określającą żądane typy dostępu do tokenu dostępu. Te typy żądanych dostępu są porównywane z LISTą DACL tokenu, aby określić, które prawa dostępu są udzielane lub odrzucane.

*bImpersonate*<br/>
W przypadku wartości TRUE bieżący wątek personifikuje klienta potoku wywołania, jeśli to wywołanie zakończy się pomyślnie. W przypadku wartości FALSE token dostępu zostanie otwarty, ale wątek nie będzie miał tokenu personifikacji po zakończeniu tego wywołania.

*bOpenAsSelf*<br/>
Wskazuje, czy sprawdzanie dostępu ma zostać wykonane względem kontekstu zabezpieczeń wątku wywołującego metodę [GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) lub względem kontekstu zabezpieczeń procesu dla wątku wywołującego.

Jeśli ten parametr ma wartość FALSE, sprawdzanie dostępu odbywa się przy użyciu kontekstu zabezpieczeń dla wątku wywołującego. Jeśli wątek personifikuje klienta, ten kontekst zabezpieczeń może być procesem klienta. Jeśli ten parametr ma wartość TRUE, sprawdzanie dostępu odbywa się przy użyciu kontekstu zabezpieczeń procesu dla wątku wywołującego.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

[Klasy CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) można użyć do automatycznego przywrócenia personifikowanych tokenów dostępu utworzonych przez ustawienie flagi *bImpersonate* na true.

##  <a name="openrpcclienttoken"></a>CAccessToken::OpenRPCClientToken

Wywołaj tę metodę z poziomu serwera obsługującego wywołanie z klienta RPC w celu zainicjowania `CAccessToken` przy użyciu tokenu dostępu z klienta.

```
bool OpenRPCClientToken(
    RPC_BINDING_HANDLE BindingHandle,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Parametry

*BindingHandle*<br/>
Dojście powiązania na serwerze, który reprezentuje powiązanie z klientem.

*dwDesiredAccess*<br/>
Określa maskę dostępu określającą żądane typy dostępu do tokenu dostępu. Te typy żądanych dostępu są porównywane z LISTą DACL tokenu, aby określić, które prawa dostępu są udzielane lub odrzucane.

*bImpersonate*<br/>
W przypadku wartości TRUE bieżący wątek personifikuje wywołującego klienta RPC, jeśli to wywołanie zostało pomyślnie zakończone. W przypadku wartości FALSE token dostępu zostanie otwarty, ale wątek nie będzie miał tokenu personifikacji po zakończeniu tego wywołania.

*bOpenAsSelf*<br/>
Wskazuje, czy sprawdzanie dostępu ma zostać wykonane względem kontekstu zabezpieczeń wątku wywołującego metodę [GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) lub względem kontekstu zabezpieczeń procesu dla wątku wywołującego.

Jeśli ten parametr ma wartość FALSE, sprawdzanie dostępu odbywa się przy użyciu kontekstu zabezpieczeń dla wątku wywołującego. Jeśli wątek personifikuje klienta, ten kontekst zabezpieczeń może być procesem klienta. Jeśli ten parametr ma wartość TRUE, sprawdzanie dostępu odbywa się przy użyciu kontekstu zabezpieczeń procesu dla wątku wywołującego.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

[Klasy CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) można użyć do automatycznego przywrócenia personifikowanych tokenów dostępu utworzonych przez ustawienie flagi *bImpersonate* na true.

##  <a name="openthreadtoken"></a>CAccessToken:: OpenThreadToken —

Wywołaj tę metodę, aby ustawić poziom personifikacji, a następnie zainicjuj `CAccessToken` przy użyciu tokenu z danego wątku.

```
bool OpenThreadToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) throw(...);
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Określa maskę dostępu określającą żądane typy dostępu do tokenu dostępu. Te typy żądanych dostępu są porównywane z LISTą DACL tokenu, aby określić, które prawa dostępu są udzielane lub odrzucane.

*bImpersonate*<br/>
W przypadku wartości TRUE wątek zostanie pozostawiony na żądanym poziomie personifikacji po zakończeniu tej metody. W przypadku wartości FALSE wątek zostanie przywrócony do oryginalnego poziomu personifikacji.

*bOpenAsSelf*<br/>
Wskazuje, czy sprawdzanie dostępu ma zostać wykonane względem kontekstu zabezpieczeń wątku wywołującego metodę [GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) lub względem kontekstu zabezpieczeń procesu dla wątku wywołującego.

Jeśli ten parametr ma wartość FALSE, sprawdzanie dostępu odbywa się przy użyciu kontekstu zabezpieczeń dla wątku wywołującego. Jeśli wątek personifikuje klienta, ten kontekst zabezpieczeń może być procesem klienta. Jeśli ten parametr ma wartość TRUE, sprawdzanie dostępu odbywa się przy użyciu kontekstu zabezpieczeń procesu dla wątku wywołującego.

*SIL*<br/>
Określa [SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level) typ wyliczeniowy, który dostarcza poziom personifikacji tokenu.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

`OpenThreadToken` jest podobna do [CAccessToken:: GetThreadToken](#getthreadtoken), ale ustawia poziom personifikacji przed zainicjowaniem `CAccessToken` z tokenu dostępu do wątku.

[Klasy CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) można użyć do automatycznego przywrócenia personifikowanych tokenów dostępu utworzonych przez ustawienie flagi *bImpersonate* na true.

##  <a name="privilegecheck"></a>CAccessToken::P rivilegeCheck

Wywołaj tę metodę, aby określić, czy w obiekcie `CAccessToken` jest włączony określony zestaw uprawnień.

```
bool PrivilegeCheck(
    PPRIVILEGE_SET RequiredPrivileges,
    bool* pbResult) const throw();
```

### <a name="parameters"></a>Parametry

*RequiredPrivileges*<br/>
Wskaźnik do struktury [PRIVILEGE_SET](/windows/win32/api/winnt/ns-winnt-privilege_set) .

*pbResult*<br/>
Wskaźnik na wartość ustawianą przez metodę wskazującą, czy dowolne lub wszystkie określone uprawnienia są włączone w obiekcie `CAccessToken`.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Gdy `PrivilegeCheck` zwraca, `Attributes` składowa każdej struktury [LUID_AND_ATTRIBUTES](/windows/win32/api/winnt/ns-winnt-luid_and_attributes) jest ustawiona na SE_PRIVILEGE_USED_FOR_ACCESS, jeśli odpowiednie uprawnienie jest włączone. Ta metoda wywołuje funkcję Win32 [PrivilegeCheck](/windows/win32/api/securitybaseapi/nf-securitybaseapi-privilegecheck) .

##  <a name="revert"></a>CAccessToken:: Revert

Wywołaj tę metodę, aby zatrzymać wątek przy użyciu tokenu personifikacji.

```
bool Revert(HANDLE hThread = NULL) const throw();
```

### <a name="parameters"></a>Parametry

*hThread*<br/>
Dojście do wątku, aby powrócić po personifikacji. Jeśli *hThread* ma wartość null, przyjmuje się bieżący wątek.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Rewersję tokenów personifikacji można przeprowadzić automatycznie z [klasą CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md).

##  <a name="setdefaultdacl"></a>CAccessToken::SetDefaultDacl

Wywołaj tę metodę, aby ustawić domyślną listę DACL obiektu `CAccessToken`.

```
bool SetDefaultDacl(const CDacl& rDacl) throw(...);
```

### <a name="parameters"></a>Parametry

*rDacl*<br/>
Nowe domyślne informacje o [klasie CDacl](../../atl/reference/cdacl-class.md) .

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Domyślna lista DACL to lista DACL, która jest używana domyślnie podczas tworzenia nowych obiektów przy użyciu tego tokenu dostępu.

##  <a name="setowner"></a>CAccessToken:: SetOwner

Wywołaj tę metodę, aby ustawić właściciela obiektu `CAccessToken`.

```
bool SetOwner(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
Obiekt [klasy CSid](../../atl/reference/csid-class.md) zawierający informacje o właścicielu.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Właściciel jest domyślnym właścicielem, który jest używany dla nowych obiektów utworzonych w trakcie działania tego tokenu dostępu.

##  <a name="setprimarygroup"></a>CAccessToken:: setprimary,

Wywołaj tę metodę, aby ustawić grupę podstawową obiektu `CAccessToken`.

```
bool SetPrimaryGroup(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
Obiekt [klasy CSid](../../atl/reference/csid-class.md) zawierający informacje o grupie podstawowej.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Grupa podstawowa jest grupą domyślną dla nowych obiektów utworzonych podczas działania tego tokenu dostępu.

## <a name="see-also"></a>Zobacz też

[Przykład ATLSecurity](../../overview/visual-cpp-samples.md)<br/>
[Tokeny dostępu](/windows/win32/SecAuthZ/access-tokens)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
