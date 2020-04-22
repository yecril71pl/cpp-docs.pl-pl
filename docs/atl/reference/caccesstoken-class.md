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
ms.openlocfilehash: f7a2ee2f9d633c1ed743621eec5b2f7cc04c0e0b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748829"
---
# <a name="caccesstoken-class"></a>Klasa CAccessToken

Ta klasa jest otoką dla tokenu dostępu.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

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
|[CAccessToken::Dołącz](#attach)|Wywołanie tej metody, aby przejąć na własność danego dojścia tokenu dostępu.|
|[CAccessToken::CheckTokenMembership](#checktokenmembership)|Wywołanie tej metody, aby ustalić, czy `CAccessToken` określony identyfikator SID jest włączony w obiekcie.|
|[CAccessToken::CreateImpersonationToken](#createimpersonationtoken)|Wywołanie tej metody, aby utworzyć nowy token dostępu personifikacji.|
|[CAccessToken::CreatePrimaryToken](#createprimarytoken)|Wywołanie tej metody, aby utworzyć nowy token podstawowy.|
|[CAccessToken::CreateProcessAsUser](#createprocessasuser)|Wywołanie tej metody, aby utworzyć nowy proces uruchomiony w `CAccessToken` kontekście zabezpieczeń użytkownika reprezentowanego przez obiekt.|
|[CAccessToken::CreateRestrictedToken](#createrestrictedtoken)|Wywołanie tej metody, aby `CAccessToken` utworzyć nowy obiekt z ograniczeniami.|
|[CAccessToken::Detach](#detach)|Wywołanie tej metody, aby odwołać własność tokenu dostępu.|
|[CAccessToken::DisablePrivilege](#disableprivilege)|Wywołanie tej metody, aby `CAccessToken` wyłączyć uprawnienia w obiekcie.|
|[CAccessToken::DisablePrivileges](#disableprivileges)|Wywołanie tej metody, aby wyłączyć `CAccessToken` jeden lub więcej uprawnień w obiekcie.|
|[CAccessToken::EnablePrivilege](#enableprivilege)|Wywołanie tej metody, aby `CAccessToken` włączyć uprawnienia w obiekcie.|
|[CAccessToken::EnablePrivileges](#enableprivileges)|Wywołanie tej metody, aby włączyć `CAccessToken` jeden lub więcej uprawnień w obiekcie.|
|[CAccessToken::GetDefaultDacl](#getdefaultdacl)|Wywołanie tej metody, aby zwrócić domyślną dacl `CAccessToken` obiektu.|
|[CAccessToken::GetEffectiveToken](#geteffectivetoken)|Wywołanie tej metody, aby uzyskać `CAccessToken` obiekt równy token dostępu w życie dla bieżącego wątku.|
|[CAccessToken::Grupy GetGroups](#getgroups)|Wywołanie tej metody, aby zwrócić grupy tokenów `CAccessToken` obiektu.|
|[CAccessToken::GetHandle](#gethandle)|Wywołanie tej metody, aby pobrać dojście do tokenu dostępu.|
|[CAccessToken::GetImpersonationNastępnie](#getimpersonationlevel)|Wywołanie tej metody, aby uzyskać poziom personifikacji z tokenu dostępu.|
|[CAccessToken::GetLogonSessionId](#getlogonsessionid)|Wywołanie tej metody, aby uzyskać identyfikator sesji `CAccessToken` logowania skojarzone z obiektem.|
|[CAccessToken::GetLogonSid](#getlogonsid)|Wywołanie tej metody, aby uzyskać identyfikator `CAccessToken` SID logowania skojarzone z obiektem.|
|[CAccessToken::Właściciel firmy GetOwner](#getowner)|Wywołanie tej metody, aby uzyskać `CAccessToken` właściciela skojarzone z obiektem.|
|[CAccessToken::GetPrimaryGroup](#getprimarygroup)|Wywołanie tej metody, aby uzyskać `CAccessToken` podstawową grupę skojarzoną z obiektem.|
|[CAccessToken::GetPrivileges](#getprivileges)|Wywołanie tej metody, aby uzyskać `CAccessToken` uprawnienia skojarzone z obiektem.|
|[CAccessToken::GetProcessToken](#getprocesstoken)|Wywołanie tej metody, `CAccessToken` aby zainicjować za pomocą tokenu dostępu z danego procesu.|
|[CAccessToken::GetProfile](#getprofile)|Wywołanie tej metody, aby uzyskać uchwyt wskazujący `CAccessToken` profil użytkownika skojarzony z obiektem.|
|[CAccessToken::GetSource](#getsource)|Wywołanie tej metody, aby `CAccessToken` uzyskać źródło obiektu.|
|[CAccessToken::GetStatistics](#getstatistics)|Wywołanie tej metody, aby `CAccessToken` uzyskać informacje skojarzone z obiektem.|
|[CAccessToken::GetTerminalServicesSessionId](#getterminalservicessessionid)|Wywołanie tej metody, aby uzyskać identyfikator sesji `CAccessToken` usług terminalowych skojarzone z obiektem.|
|[CAccessToken::GetThreadToken](#getthreadtoken)|Wywołanie tej metody, `CAccessToken` aby zainicjować z tokenem z danego wątku.|
|[CAccessToken::GetTokenId](#gettokenid)|Wywołanie tej metody, aby uzyskać identyfikator `CAccessToken` tokenu skojarzone z obiektem.|
|[CAccessToken::GetType](#gettype)|Wywołanie tej metody, aby `CAccessToken` uzyskać typ tokenu obiektu.|
|[CAccessToken::GetUser](#getuser)|Wywołanie tej metody, aby zidentyfikować `CAccessToken` użytkownika skojarzonego z obiektem.|
|[CAccessToken::HKeyCurrentUser](#hkeycurrentuser)|Wywołanie tej metody, aby uzyskać uchwyt wskazujący `CAccessToken` profil użytkownika skojarzony z obiektem.|
|[CAccessToken::Personifikuj](#impersonate)|Wywołanie tej metody, `CAccessToken` aby przypisać personifikacji do wątku.|
|[CAccessToken::PersoneLoggedOnUser](#impersonateloggedonuser)|Wywołanie tej metody, aby umożliwić wątku wywołującego personifikować kontekst zabezpieczeń zalogowanego użytkownika.|
|[CAccessToken::IsTokenRestricted](#istokenrestricted)|Wywołanie tej metody, `CAccessToken` aby sprawdzić, czy obiekt zawiera listę ograniczonych identyfikatorów SID.|
|[CAccessToken::LoadUserProfile](#loaduserprofile)|Wywołanie tej metody, aby załadować `CAccessToken` profil użytkownika skojarzony z obiektem.|
|[CAccessToken::LogonUżycie](#logonuser)|Wywołanie tej metody, aby utworzyć sesję logowania dla użytkownika skojarzonego z podanymi poświadczeniami.|
|[CAccessToken::OpenCOMClientToken](#opencomclienttoken)|Wywołanie tej metody z poziomu serwera COM obsługi wywołania od klienta, aby zainicjować `CAccessToken` za pomocą tokenu dostępu z klienta COM.|
|[CAccessToken::OpenNamedPipeClientToken](#opennamedpipeclienttoken)|Wywołanie tej metody z poziomu serwera, biorąc żądania `CAccessToken` za pomocą potoku o nazwie, aby zainicjować za pomocą tokenu dostępu z klienta.|
|[CAccessToken::OpenRPCClientToken](#openrpcclienttoken)|Wywołanie tej metody z poziomu serwera obsługi wywołania z `CAccessToken` klienta RPC, aby zainicjować za pomocą tokenu dostępu z klienta.|
|[CAccessToken::OpenThreadToken](#openthreadtoken)|Wywołanie tej metody, aby ustawić poziom `CAccessToken` personifikacji, a następnie zainicjować token z danego wątku.|
|[CAccessToken::PrivilegeCheck](#privilegecheck)|Wywołanie tej metody, aby ustalić, czy określony `CAccessToken` zestaw uprawnień są włączone w obiekcie.|
|[CAccessToken::Powrót](#revert)|Wywołanie tej metody, aby zatrzymać wątek, który używa tokenu personifikacji.|
|[CAccessToken::SetDefaultDacl](#setdefaultdacl)|Wywołanie tej metody, aby ustawić `CAccessToken` domyślną dacl obiektu.|
|[CAccessToken::SetOwner](#setowner)|Wywołanie tej metody, aby `CAccessToken` ustawić właściciela obiektu.|
|[CAccessToken::SetPrimaryGroup](#setprimarygroup)|Wywołanie tej metody, aby `CAccessToken` ustawić grupę podstawową obiektu.|

## <a name="remarks"></a>Uwagi

[Token dostępu](/windows/win32/SecAuthZ/access-tokens) jest obiektem opisującym kontekst zabezpieczeń procesu lub wątku i przydzielanym każdemu użytkownikowi zalogowanym do systemu Windows.

Aby zapoznać się z wprowadzeniem do modelu kontroli dostępu w systemie Windows, zobacz [Kontrola dostępu](/windows/win32/SecAuthZ/access-control) w zestaw Windows SDK.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

## <a name="caccesstokenattach"></a><a name="attach"></a>CAccessToken::Dołącz

Wywołanie tej metody, aby przejąć na własność danego dojścia tokenu dostępu.

```cpp
void Attach(HANDLE hToken) throw();
```

### <a name="parameters"></a>Parametry

*hToken (własówce)*<br/>
Dojście do tokenu dostępu.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania błąd potwierdzenia `CAccessToken` wystąpi, jeśli obiekt ma już własność tokenu dostępu.

## <a name="caccesstokencaccesstoken"></a><a name="dtor"></a>CAccessToken::~CAccessToken

Destruktor.

```
virtual ~CAccessToken() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby.

## <a name="caccesstokenchecktokenmembership"></a><a name="checktokenmembership"></a>CAccessToken::CheckTokenMembership

Wywołanie tej metody, aby ustalić, czy `CAccessToken` określony identyfikator SID jest włączony w obiekcie.

```
bool CheckTokenMembership(
    const CSid& rSid,
    bool* pbIsMember) const throw(...);
```

### <a name="parameters"></a>Parametry

*rSid (wyd.*<br/>
Odwołanie do obiektu [klasy CSid.](../../atl/reference/csid-class.md)

*pbIsCzłonek*<br/>
Wskaźnik do zmiennej, która odbiera wyniki kontroli.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Metoda `CheckTokenMembership` sprawdza obecność identyfikatora SID w identyfikatorze SID użytkownika i grupy identyfikatorów SID tokenu dostępu. Jeśli identyfikator SID jest obecny i ma atrybut SE_GROUP_ENABLED, *pbIsMember* jest ustawiona na WARTOŚĆ PRAWDA; w przeciwnym razie jest ustawiona na FAŁSZ.

W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli *pbIsMember* nie jest prawidłowym wskaźnikiem.

> [!NOTE]
> Obiekt `CAccessToken` musi być token personifikacji, a nie token podstawowy.

## <a name="caccesstokencreateimpersonationtoken"></a><a name="createimpersonationtoken"></a>CAccessToken::CreateImpersonationToken

Wywołanie tej metody, aby utworzyć token dostępu personifikacji.

```
bool CreateImpersonationToken(
    CAccessToken* pImp,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) const throw(...);
```

### <a name="parameters"></a>Parametry

*Pimp*<br/>
Wskaźnik do `CAccessToken` nowego obiektu.

*Sil*<br/>
Określa [typ SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level) wyliczony, który dostarcza poziom personifikacji nowego tokenu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

`CreateImpersonationToken`wywołuje [DuplicateToken,](/windows/win32/api/securitybaseapi/nf-securitybaseapi-duplicatetoken) aby utworzyć nowy token personifikacji.

## <a name="caccesstokencreateprimarytoken"></a><a name="createprimarytoken"></a>CAccessToken::CreatePrimaryToken

Wywołanie tej metody, aby utworzyć nowy token podstawowy.

```
bool CreatePrimaryToken(
    CAccessToken* pPri,
    DWORD dwDesiredAccess = MAXIMUM_ALLOWED,
    const CSecurityAttributes* pTokenAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pPri (pPri)*<br/>
Wskaźnik do `CAccessToken` nowego obiektu.

*dwDesiredAccess*<br/>
Określa żądane prawa dostępu dla nowego tokenu. Domyślna MAXIMUM_ALLOWED żąda wszystkich praw dostępu, które są prawidłowe dla obiektu wywołującego. Aby uzyskać więcej informacji na temat praw dostępu, zobacz [Prawa dostępu i Maski dostępu.](/windows/win32/SecAuthZ/access-rights-and-access-masks)

*pTokenAttributes (Przyciski PTokenAttributes)*<br/>
Wskaźnik do [struktury SECURITY_ATTRIBUTES,](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) która określa deskryptora zabezpieczeń dla nowego tokenu i określa, czy procesy podrzędne mogą dziedziczyć token. Jeśli *pTokenAttributes* ma wartość NULL, token pobiera domyślny deskryptor zabezpieczeń i nie można dziedziczyć dojścia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

`CreatePrimaryToken`wywołuje [DuplicateTokenEx,](/windows/win32/api/securitybaseapi/nf-securitybaseapi-duplicatetokenex) aby utworzyć nowy token podstawowy.

## <a name="caccesstokencreateprocessasuser"></a><a name="createprocessasuser"></a>CAccessToken::CreateProcessAsUser

Wywołanie tej metody, aby utworzyć nowy proces uruchomiony w `CAccessToken` kontekście zabezpieczeń użytkownika reprezentowanego przez obiekt.

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
Wskaźnik do ciągu zakończonego z wartością null, który określa moduł do wykonania. Ten parametr może nie być null.

*pCommandLine (Linia)*<br/>
Wskaźnik do ciągu zakończonego zerem, który określa wiersz polecenia do wykonania.

*pProcessInformacja*<br/>
Wskaźnik do [struktury PROCESS_INFORMATION,](/windows/win32/api/processthreadsapi/ns-processthreadsapi-process_information) która odbiera informacje identyfikacyjne o nowym procesie.

*pStartupInfo*<br/>
Wskaźnik do [startupinfo](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfow) struktury, która określa, jak powinno być wyświetlane okno główne dla nowego procesu.

*dwCreationFlags*<br/>
Określa dodatkowe flagi, które kontrolują klasę priorytetu i tworzenie procesu. Zobacz Win32 funkcja [CreateProcessAsUser](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessasuserw) listę flag.

*bLoadProfile*<br/>
Jeśli true, profil użytkownika jest ładowany [z LoadUserProfile](/windows/win32/api/userenv/nf-userenv-loaduserprofilew).

*pProcessAttributes*<br/>
Wskaźnik do [struktury SECURITY_ATTRIBUTES,](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) która określa deskryptora zabezpieczeń dla nowego procesu i określa, czy procesy podrzędne mogą dziedziczyć zwrócony uchwyt. Jeśli *pProcessAttributes* ma wartość NULL, proces pobiera domyślny deskryptor zabezpieczeń i nie można dziedziczyć dojścia.

*pThreadAttributes (PsżućAttributes)*<br/>
Wskaźnik do [struktury SECURITY_ATTRIBUTES,](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) która określa deskryptora zabezpieczeń dla nowego wątku i określa, czy procesy podrzędne mogą dziedziczyć zwrócony uchwyt. Jeśli *pThreadAttributes* ma wartość NULL, wątek otrzymuje domyślny deskryptor zabezpieczeń i nie można dziedziczyć dojścia.

*bInherit (w tym)*<br/>
Wskazuje, czy nowy proces dziedziczy uchwyty z procesu wywołującego. Jeśli TRUE, każdy dziedziczny otwarty dojście w procesie wywołującym jest dziedziczona przez nowy proces. Dziedziczone uchwyty mają taką samą wartość i uprawnienia dostępu jak oryginalne uchwyty.

*pCurrentDirectory (Kierunek)*<br/>
Wskaźnik do ciągu zakończonego z wartością null, który określa bieżący dysk i katalog dla nowego procesu. Ciąg musi być pełną ścieżką zawierającą literę dysku. Jeśli ten parametr ma wartość NULL, nowy proces będzie miał ten sam bieżący dysk i katalog co proces wywołujący.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

`CreateProcessAsUser`Używa funkcji `CreateProcessAsUser` Win32 do utworzenia nowego procesu, który działa w kontekście zabezpieczeń użytkownika reprezentowanego przez `CAccessToken` obiekt. Zobacz opis [CreateProcessAsUser](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessasuserw) funkcji pełne omówienie wymaganych parametrów.

Aby ta metoda powiodła `CAccessToken` się, obiekt musi zawierać AssignPrimaryToken (chyba że jest to token z ograniczeniami) i IncreaseQuota uprawnień.

## <a name="caccesstokencreaterestrictedtoken"></a><a name="createrestrictedtoken"></a>CAccessToken::CreateRestrictedToken

Wywołanie tej metody, aby `CAccessToken` utworzyć nowy obiekt z ograniczeniami.

```
bool CreateRestrictedToken(
    CAccessToken* pRestrictedToken,
    const CTokenGroups& SidsToDisable,
    const CTokenGroups& SidsToRestrict,
    const CTokenPrivileges& PrivilegesToDelete = CTokenPrivileges()) const throw(...);
```

### <a name="parameters"></a>Parametry

*pRestrictedToken (Niem.*<br/>
Nowy, ograniczony `CAccessToken` obiekt.

*SidsToDisable (Możliwe jest wykrywanie)*<br/>
Obiekt, `CTokenGroups` który określa identyfikatory SID tylko do odmowy.

*SidsToRestrict ( SidsToRestrict )*<br/>
Obiekt `CTokenGroups` określający ograniczające identyfikatory SID.

*PrivilegesToDelete*<br/>
Obiekt, `CTokenPrivileges` który określa uprawnienia do usunięcia w tokenie z ograniczeniami. Wartość domyślna tworzy pusty obiekt.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

`CreateRestrictedToken`Używa [createRestrictedToken](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createrestrictedtoken) Win32 funkcji do `CAccessToken` tworzenia nowego obiektu, z ograniczeniami.

> [!IMPORTANT]
> Podczas `CreateRestrictedToken`korzystania , upewnij się, że są prawidłowe: istniejący token jest prawidłowy (i nie wprowadzony przez użytkownika) i *SidsToDisable* i *PrivilegesToDelete* są prawidłowe (i nie wprowadzone przez użytkownika). Jeśli metoda zwraca FAŁSZ, odmów funkcji.

## <a name="caccesstokendetach"></a><a name="detach"></a>CAccessToken::Detach

Wywołanie tej metody, aby odwołać własność tokenu dostępu.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca uchwyt do `CAccessToken` tego, który został odłączony.

### <a name="remarks"></a>Uwagi

Ta metoda odwołuje `CAccessToken`własność 's tokenu dostępu.

## <a name="caccesstokendisableprivilege"></a><a name="disableprivilege"></a>CAccessToken::DisablePrivilege

Wywołanie tej metody, aby `CAccessToken` wyłączyć uprawnienia w obiekcie.

```
bool DisablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*pszPrivilege*<br/>
Wskaźnik do ciągu zawierającego uprawnienia, `CAccessToken` aby wyłączyć w obiekcie.

*pPoprzedniPaństwo*<br/>
Wskaźnik do `CTokenPrivileges` obiektu, który będzie zawierał poprzedni stan uprawnień.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

## <a name="caccesstokendisableprivileges"></a><a name="disableprivileges"></a>CAccessToken::DisablePrivileges

Wywołanie tej metody, aby wyłączyć `CAccessToken` jeden lub więcej uprawnień w obiekcie.

```
bool DisablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*rPrivileges*<br/>
Wskaźnik do tablicy ciągów zawierających uprawnienia, aby `CAccessToken` wyłączyć w obiekcie.

*pPoprzedniPaństwo*<br/>
Wskaźnik do `CTokenPrivileges` obiektu, który będzie zawierał poprzedni stan uprawnień.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

## <a name="caccesstokenenableprivilege"></a><a name="enableprivilege"></a>CAccessToken::EnablePrivilege

Wywołanie tej metody, aby `CAccessToken` włączyć uprawnienia w obiekcie.

```
bool EnablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*pszPrivilege*<br/>
Wskaźnik do ciągu zawierającego uprawnienia, `CAccessToken` aby włączyć w obiekcie.

*pPoprzedniPaństwo*<br/>
Wskaźnik do `CTokenPrivileges` obiektu, który będzie zawierał poprzedni stan uprawnień.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

## <a name="caccesstokenenableprivileges"></a><a name="enableprivileges"></a>CAccessToken::EnablePrivileges

Wywołanie tej metody, aby włączyć `CAccessToken` jeden lub więcej uprawnień w obiekcie.

```
bool EnablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*rPrivileges*<br/>
Wskaźnik do tablicy ciągów zawierających uprawnienia, aby `CAccessToken` włączyć w obiekcie.

*pPoprzedniPaństwo*<br/>
Wskaźnik do `CTokenPrivileges` obiektu, który będzie zawierał poprzedni stan uprawnień.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

## <a name="caccesstokengetdefaultdacl"></a><a name="getdefaultdacl"></a>CAccessToken::GetDefaultDacl

Wywołanie tej metody, aby zwrócić domyślną dacl `CAccessToken` obiektu.

```
bool GetDefaultDacl(CDacl* pDacl) const throw(...);
```

### <a name="parameters"></a>Parametry

*pDacl (pDacl)*<br/>
Wskaźnik do obiektu [Klasy CDacl,](../../atl/reference/cdacl-class.md) który otrzyma domyślną `CAccessToken` listy DACL obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli domyślna funkcja DACL została odzyskana, w przeciwnym razie wartość FAŁSZ.

## <a name="caccesstokengeteffectivetoken"></a><a name="geteffectivetoken"></a>CAccessToken::GetEffectiveToken

Wywołanie tej metody, aby uzyskać `CAccessToken` obiekt równy token dostępu w życie dla bieżącego wątku.

```
bool GetEffectiveToken(DWORD dwDesiredAccess) throw();
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Określa maskę dostępu określającą żądane typy dostępu do tokenu dostępu. Te żądane typy dostępu są porównywane z listy DACL tokenu, aby określić, które dostępy są przyznawane lub odrzucane.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

## <a name="caccesstokengetgroups"></a><a name="getgroups"></a>CAccessToken::Grupy GetGroups

Wywołanie tej metody, aby zwrócić grupy tokenów `CAccessToken` obiektu.

```
bool GetGroups(CTokenGroups* pGroups) const throw(...);
```

### <a name="parameters"></a>Parametry

*pGrupy*<br/>
Wskaźnik do [CTokenGroups Class](../../atl/reference/ctokengroups-class.md) obiektu, który otrzyma informacje o grupie.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

## <a name="caccesstokengethandle"></a><a name="gethandle"></a>CAccessToken::GetHandle

Wywołanie tej metody, aby pobrać dojście do tokenu dostępu.

```
HANDLE GetHandle() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca dojście `CAccessToken` do tokenu dostępu obiektu.

## <a name="caccesstokengetimpersonationlevel"></a><a name="getimpersonationlevel"></a>CAccessToken::GetImpersonationNastępnie

Wywołanie tej metody, aby uzyskać poziom personifikacji z tokenu dostępu.

```
bool GetImpersonationLevel(
    SECURITY_IMPERSONATION_LEVEL* pImpersonationLevel) const throw(...);
```

### <a name="parameters"></a>Parametry

*pImpersonationPoziom*<br/>
Wskaźnik do typu wyliczenia [SECURITY_IMPERSONATION_LEVEL,](/windows/win32/api/winnt/ne-winnt-security_impersonation_level) który otrzyma informacje o poziomie personifikacji.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

## <a name="caccesstokengetlogonsessionid"></a><a name="getlogonsessionid"></a>CAccessToken::GetLogonSessionId

Wywołanie tej metody, aby uzyskać identyfikator sesji `CAccessToken` logowania skojarzone z obiektem.

```
bool GetLogonSessionId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pluid ( pluid )*<br/>
Wskaźnik do [identyfikatora LUID,](/windows/win32/api/winnt/ns-winnt-luid) który otrzyma identyfikator sesji logowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli *pluid* jest nieprawidłową wartością.

## <a name="caccesstokengetlogonsid"></a><a name="getlogonsid"></a>CAccessToken::GetLogonSid

Wywołanie tej metody, aby uzyskać identyfikator `CAccessToken` SID logowania skojarzone z obiektem.

```
bool GetLogonSid(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSid*<br/>
Wskaźnik do obiektu [klasy CSid.](../../atl/reference/csid-class.md)

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli *pSid* jest nieprawidłową wartością.

## <a name="caccesstokengetowner"></a><a name="getowner"></a>CAccessToken::Właściciel firmy GetOwner

Wywołanie tej metody, aby uzyskać `CAccessToken` właściciela skojarzone z obiektem.

```
bool GetOwner(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSid*<br/>
Wskaźnik do obiektu [klasy CSid.](../../atl/reference/csid-class.md)

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Właściciel jest domyślnie ustawiany na wszystkie obiekty utworzone, gdy ten token dostępu jest w mocy.

## <a name="caccesstokengetprimarygroup"></a><a name="getprimarygroup"></a>CAccessToken::GetPrimaryGroup

Wywołanie tej metody, aby uzyskać `CAccessToken` podstawową grupę skojarzoną z obiektem.

```
bool GetPrimaryGroup(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSid*<br/>
Wskaźnik do obiektu [klasy CSid.](../../atl/reference/csid-class.md)

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Grupa jest ustawiona domyślnie na wszystkie obiekty utworzone, gdy ten token dostępu jest w mocy.

## <a name="caccesstokengetprivileges"></a><a name="getprivileges"></a>CAccessToken::GetPrivileges

Wywołanie tej metody, aby uzyskać `CAccessToken` uprawnienia skojarzone z obiektem.

```
bool GetPrivileges(CTokenPrivileges* pPrivileges) const throw(...);
```

### <a name="parameters"></a>Parametry

*pPrivileges*<br/>
Wskaźnik do [CTokenPrivileges Class](../../atl/reference/ctokenprivileges-class.md) obiektu, który otrzyma uprawnienia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

## <a name="caccesstokengetprocesstoken"></a><a name="getprocesstoken"></a>CAccessToken::GetProcessToken

Wywołanie tej metody, `CAccessToken` aby zainicjować za pomocą tokenu dostępu z danego procesu.

```
bool GetProcessToken(DWORD dwDesiredAccess, HANDLE hProcess = NULL) throw();
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Określa maskę dostępu określającą żądane typy dostępu do tokenu dostępu. Te żądane typy dostępu są porównywane z listy DACL tokenu, aby określić, które dostępy są przyznawane lub odrzucane.

*hProcess ( proces)*<br/>
Dojem do procesu, którego token dostępu jest otwarty. Jeśli używana jest domyślna wartość NULL, używany jest bieżący proces.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Wywołuje funkcję [OpenProcessToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-openprocesstoken) Win32.

## <a name="caccesstokengetprofile"></a><a name="getprofile"></a>CAccessToken::GetProfile

Wywołanie tej metody, aby uzyskać uchwyt wskazujący `CAccessToken` profil użytkownika skojarzony z obiektem.

```
HANDLE GetProfile() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca uchwyt wskazujący profil użytkownika lub NULL, jeśli nie istnieje żaden profil.

## <a name="caccesstokengetsource"></a><a name="getsource"></a>CAccessToken::GetSource

Wywołanie tej metody, aby `CAccessToken` uzyskać źródło obiektu.

```
bool GetSource(TOKEN_SOURCE* pSource) const throw(...);
```

### <a name="parameters"></a>Parametry

*pŹródło*<br/>
Wskaźnik do [struktury TOKEN_SOURCE.](/windows/win32/api/winnt/ns-winnt-token_source)

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

## <a name="caccesstokengetstatistics"></a><a name="getstatistics"></a>CAccessToken::GetStatistics

Wywołanie tej metody, aby `CAccessToken` uzyskać informacje skojarzone z obiektem.

```
bool GetStatistics(TOKEN_STATISTICS* pStatistics) const throw(...);
```

### <a name="parameters"></a>Parametry

*pStatistics (statystyki)*<br/>
Wskaźnik do [struktury TOKEN_STATISTICS.](/windows/win32/api/winnt/ns-winnt-token_statistics)

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

## <a name="caccesstokengetterminalservicessessionid"></a><a name="getterminalservicessessionid"></a>CAccessToken::GetTerminalServicesSessionId

Wywołanie tej metody, aby uzyskać identyfikator sesji `CAccessToken` usług terminalowych skojarzone z obiektem.

```
bool GetTerminalServicesSessionId(DWORD* pdwSessionId) const throw(...);
```

### <a name="parameters"></a>Parametry

*pdwSessionId*<br/>
Identyfikator sesji usług terminalowych.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

## <a name="caccesstokengetthreadtoken"></a><a name="getthreadtoken"></a>CAccessToken::GetThreadToken

Wywołanie tej metody, `CAccessToken` aby zainicjować z tokenem z danego wątku.

```
bool GetThreadToken(
    DWORD dwDesiredAccess,
    HANDLE hThread = NULL,
    bool bOpenAsSelf = true) throw();
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Określa maskę dostępu określającą żądane typy dostępu do tokenu dostępu. Te żądane typy dostępu są porównywane z listy DACL tokenu, aby określić, które dostępy są przyznawane lub odrzucane.

*hWczynienie*<br/>
Dojście do wątku, którego token dostępu jest otwarty.

*bOpenAsSelf*<br/>
Wskazuje, czy sprawdzanie dostępu ma być wykonane w kontekście `GetThreadToken` zabezpieczeń wątku wywołującego metodę lub w kontekście zabezpieczeń procesu dla wątku wywołującego.

Jeśli ten parametr jest FALSE, sprawdzanie dostępu jest wykonywane przy użyciu kontekstu zabezpieczeń dla wątku wywołującego. Jeśli wątek personifikuje klienta, ten kontekst zabezpieczeń może być kontekstu procesu klienta. Jeśli ten parametr jest TRUE, sprawdzanie dostępu jest dokonywane przy użyciu kontekstu zabezpieczeń procesu dla wątku wywołującego.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

## <a name="caccesstokengettokenid"></a><a name="gettokenid"></a>CAccessToken::GetTokenId

Wywołanie tej metody, aby uzyskać identyfikator `CAccessToken` tokenu skojarzone z obiektem.

```
bool GetTokenId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pluid ( pluid )*<br/>
Wskaźnik do [identyfikatora LUID,](/windows/win32/api/winnt/ns-winnt-luid) który otrzyma identyfikator tokenu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

## <a name="caccesstokengettype"></a><a name="gettype"></a>CAccessToken::GetType

Wywołanie tej metody, aby `CAccessToken` uzyskać typ tokenu obiektu.

```
bool GetType(TOKEN_TYPE* pType) const throw(...);
```

### <a name="parameters"></a>Parametry

*pTyp*<br/>
Adres [zmiennej TOKEN_TYPE,](/windows/win32/api/winnt/ne-winnt-token_type) która po powodzenie otrzymuje typ tokenu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Typ wyliczenia TOKEN_TYPE zawiera wartości, które rozróżniają token podstawowy i token personifikacji.

## <a name="caccesstokengetuser"></a><a name="getuser"></a>CAccessToken::GetUser

Wywołanie tej metody, aby zidentyfikować `CAccessToken` użytkownika skojarzonego z obiektem.

```
bool GetUser(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSid*<br/>
Wskaźnik do obiektu [klasy CSid.](../../atl/reference/csid-class.md)

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

## <a name="caccesstokenhkeycurrentuser"></a><a name="hkeycurrentuser"></a>CAccessToken::HKeyCurrentUser

Wywołanie tej metody, aby uzyskać uchwyt wskazujący `CAccessToken` profil użytkownika skojarzony z obiektem.

```
HKEY HKeyCurrentUser() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca uchwyt wskazujący profil użytkownika lub NULL, jeśli nie istnieje żaden profil.

## <a name="caccesstokenimpersonate"></a><a name="impersonate"></a>CAccessToken::Personifikuj

Wywołanie tej metody, `CAccessToken` aby przypisać personifikacji do wątku.

```
bool Impersonate(HANDLE hThread = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*hWczynienie*<br/>
Dojrzyj do wątku, aby przypisać token personifikacji do. Ten dojście musi zostać otwarty z TOKEN_IMPERSONATE praw dostępu. Jeśli *hThread* jest NULL, metoda powoduje, że wątek, aby zatrzymać przy użyciu tokenu personifikacji.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania wystąpi błąd `CAccessToken` potwierdzenia, jeśli nie ma prawidłowego wskaźnika do tokenu.

[Klasa CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) może służyć do automatycznego przywracania personifikowanych tokenów dostępu.

## <a name="caccesstokenimpersonateloggedonuser"></a><a name="impersonateloggedonuser"></a>CAccessToken::PersoneLoggedOnUser

Wywołanie tej metody, aby umożliwić wątku wywołującego personifikować kontekst zabezpieczeń zalogowanego użytkownika.

```
bool ImpersonateLoggedOnUser() const throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

> [!IMPORTANT]
> Jeśli wywołanie funkcji personifikacji nie powiedzie się z jakiegokolwiek powodu, klient nie jest personifikowany, a żądanie klienta jest składane w kontekście zabezpieczeń procesu, z którego zostało wykonane wywołanie. Jeśli proces jest uruchomiony jako konto o wysokim stopniu uprzywilejowania lub jako członek grupy administracyjnej, użytkownik może być w stanie wykonać akcje, które w przeciwnym razie nie będą dozwolone. W związku z tym zwracana wartość dla tej funkcji powinna być zawsze potwierdzona.

## <a name="caccesstokenistokenrestricted"></a><a name="istokenrestricted"></a>CAccessToken::IsTokenRestricted

Wywołanie tej metody, `CAccessToken` aby sprawdzić, czy obiekt zawiera listę ograniczonych identyfikatorów SID.

```
bool IsTokenRestricted() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli obiekt zawiera listę ograniczających identyfikatorów SID, FALSE, jeśli nie ma żadnych ograniczających identyfikatorów SID lub jeśli metoda nie powiedzie się.

## <a name="caccesstokenloaduserprofile"></a><a name="loaduserprofile"></a>CAccessToken::LoadUserProfile

Wywołanie tej metody, aby załadować `CAccessToken` profil użytkownika skojarzony z obiektem.

```
bool LoadUserProfile() throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania błąd potwierdzenia `CAccessToken` wystąpi, jeśli nie zawiera prawidłowego tokenu lub jeśli profil użytkownika już istnieje.

## <a name="caccesstokenlogonuser"></a><a name="logonuser"></a>CAccessToken::LogonUżycie

Wywołanie tej metody, aby utworzyć sesję logowania dla użytkownika skojarzonego z podanymi poświadczeniami.

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
Wskaźnik do ciągu zakończonego z wartością null, który określa nazwę użytkownika. Jest to nazwa konta użytkownika, do na które chcesz się zalogować.

*pszDomain*<br/>
Wskaźnik do ciągu zakończonego z wartością null, który określa nazwę domeny lub serwera, którego baza danych kont zawiera konto *pszUserName.*

*pszPassword*<br/>
Wskaźnik do ciągu zakończonego zerem, który określa hasło w postaci zwykłego tekstu dla konta użytkownika określonego przez *pszUserName*.

*typ dwLogonType*<br/>
Określa typ operacji logowania do wykonania. Zobacz [LogonUser aby](/windows/win32/api/winbase/nf-winbase-logonuserw) uzyskać więcej informacji.

*dwLogonProvider*<br/>
Określa dostawcę logowania. Zobacz [LogonUser aby](/windows/win32/api/winbase/nf-winbase-logonuserw) uzyskać więcej informacji.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Token dostępu wynikający z logowania będzie skojarzony `CAccessToken`z . Aby ta metoda powiodła `CAccessToken` się, obiekt musi posiadać SE_TCB_NAME uprawnienia, identyfikując posiadacza jako część zaufanej bazy komputera. Zobacz [LogonUser aby](/windows/win32/api/winbase/nf-winbase-logonuserw) uzyskać więcej informacji dotyczących wymaganych uprawnień.

## <a name="caccesstokenopencomclienttoken"></a><a name="opencomclienttoken"></a>CAccessToken::OpenCOMClientToken

Wywołanie tej metody z poziomu serwera COM obsługi wywołania od klienta, aby zainicjować `CAccessToken` za pomocą tokenu dostępu z klienta COM.

```
bool OpenCOMClientToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Określa maskę dostępu określającą żądane typy dostępu do tokenu dostępu. Te żądane typy dostępu są porównywane z listy DACL tokenu, aby określić, które dostępy są przyznawane lub odrzucane.

*bImpersonate*<br/>
Jeśli TRUE, bieżący wątek będzie personifikować wywołującego klienta COM, jeśli to wywołanie zakończy się pomyślnie. Jeśli FALSE, token dostępu zostanie otwarty, ale wątek nie będzie miał token personifikacji po zakończeniu tego wywołania.

*bOpenAsSelf*<br/>
Wskazuje, czy sprawdzanie dostępu ma zostać wykonane w kontekście zabezpieczeń wątku wywołującego [Metodę GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) lub w kontekście zabezpieczeń procesu dla wątku wywołującego.

Jeśli ten parametr jest FALSE, sprawdzanie dostępu jest wykonywane przy użyciu kontekstu zabezpieczeń dla wątku wywołującego. Jeśli wątek personifikuje klienta, ten kontekst zabezpieczeń może być kontekstu procesu klienta. Jeśli ten parametr jest TRUE, sprawdzanie dostępu jest dokonywane przy użyciu kontekstu zabezpieczeń procesu dla wątku wywołującego.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

[Klasa CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) może służyć do automatycznego przywracania personifikowanych tokenów dostępu utworzonych przez ustawienie flagi *bImpersonate* na TRUE.

## <a name="caccesstokenopennamedpipeclienttoken"></a><a name="opennamedpipeclienttoken"></a>CAccessToken::OpenNamedPipeClientToken

Wywołanie tej metody z poziomu serwera, biorąc żądania `CAccessToken` za pomocą potoku o nazwie, aby zainicjować za pomocą tokenu dostępu z klienta.

```
bool OpenNamedPipeClientToken(
    HANDLE hPipe,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Parametry

*hPipe (rura)*<br/>
Dojście do nazwanego potoku.

*dwDesiredAccess*<br/>
Określa maskę dostępu określającą żądane typy dostępu do tokenu dostępu. Te żądane typy dostępu są porównywane z listy DACL tokenu, aby określić, które dostępy są przyznawane lub odrzucane.

*bImpersonate*<br/>
Jeśli TRUE, bieżący wątek będzie personifikować klienta potoku wywołującego, jeśli to wywołanie zakończy się pomyślnie. Jeśli FALSE, token dostępu zostanie otwarty, ale wątek nie będzie miał token personifikacji po zakończeniu tego wywołania.

*bOpenAsSelf*<br/>
Wskazuje, czy sprawdzanie dostępu ma zostać wykonane w kontekście zabezpieczeń wątku wywołującego [Metodę GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) lub w kontekście zabezpieczeń procesu dla wątku wywołującego.

Jeśli ten parametr jest FALSE, sprawdzanie dostępu jest wykonywane przy użyciu kontekstu zabezpieczeń dla wątku wywołującego. Jeśli wątek personifikuje klienta, ten kontekst zabezpieczeń może być kontekstu procesu klienta. Jeśli ten parametr jest TRUE, sprawdzanie dostępu jest dokonywane przy użyciu kontekstu zabezpieczeń procesu dla wątku wywołującego.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

[Klasa CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) może służyć do automatycznego przywracania personifikowanych tokenów dostępu utworzonych przez ustawienie flagi *bImpersonate* na TRUE.

## <a name="caccesstokenopenrpcclienttoken"></a><a name="openrpcclienttoken"></a>CAccessToken::OpenRPCClientToken

Wywołanie tej metody z poziomu serwera obsługi wywołania z `CAccessToken` klienta RPC, aby zainicjować za pomocą tokenu dostępu z klienta.

```
bool OpenRPCClientToken(
    RPC_BINDING_HANDLE BindingHandle,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Parametry

*BindingHandle (Uchwyt wiązania)*<br/>
Powiązanie dojścia na serwerze, który reprezentuje powiązanie z klientem.

*dwDesiredAccess*<br/>
Określa maskę dostępu określającą żądane typy dostępu do tokenu dostępu. Te żądane typy dostępu są porównywane z listy DACL tokenu, aby określić, które dostępy są przyznawane lub odrzucane.

*bImpersonate*<br/>
Jeśli TRUE, bieżący wątek będzie personifikować wywołującego klienta RPC, jeśli to wywołanie zakończy się pomyślnie. Jeśli FALSE, token dostępu zostanie otwarty, ale wątek nie będzie miał token personifikacji po zakończeniu tego wywołania.

*bOpenAsSelf*<br/>
Wskazuje, czy sprawdzanie dostępu ma zostać wykonane w kontekście zabezpieczeń wątku wywołującego [Metodę GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) lub w kontekście zabezpieczeń procesu dla wątku wywołującego.

Jeśli ten parametr jest FALSE, sprawdzanie dostępu jest wykonywane przy użyciu kontekstu zabezpieczeń dla wątku wywołującego. Jeśli wątek personifikuje klienta, ten kontekst zabezpieczeń może być kontekstu procesu klienta. Jeśli ten parametr jest TRUE, sprawdzanie dostępu jest dokonywane przy użyciu kontekstu zabezpieczeń procesu dla wątku wywołującego.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

[Klasa CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) może służyć do automatycznego przywracania personifikowanych tokenów dostępu utworzonych przez ustawienie flagi *bImpersonate* na TRUE.

## <a name="caccesstokenopenthreadtoken"></a><a name="openthreadtoken"></a>CAccessToken::OpenThreadToken

Wywołanie tej metody, aby ustawić poziom `CAccessToken` personifikacji, a następnie zainicjować token z danego wątku.

```
bool OpenThreadToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) throw(...);
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Określa maskę dostępu określającą żądane typy dostępu do tokenu dostępu. Te żądane typy dostępu są porównywane z listy DACL tokenu, aby określić, które dostępy są przyznawane lub odrzucane.

*bImpersonate*<br/>
Jeśli TRUE, wątek pozostanie na żądanym poziomie personifikacji po zakończeniu tej metody. Jeśli FALSE, wątek powróci do jego oryginalnego poziomu personifikacji.

*bOpenAsSelf*<br/>
Wskazuje, czy sprawdzanie dostępu ma zostać wykonane w kontekście zabezpieczeń wątku wywołującego [Metodę GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) lub w kontekście zabezpieczeń procesu dla wątku wywołującego.

Jeśli ten parametr jest FALSE, sprawdzanie dostępu jest wykonywane przy użyciu kontekstu zabezpieczeń dla wątku wywołującego. Jeśli wątek personifikuje klienta, ten kontekst zabezpieczeń może być kontekstu procesu klienta. Jeśli ten parametr jest TRUE, sprawdzanie dostępu jest dokonywane przy użyciu kontekstu zabezpieczeń procesu dla wątku wywołującego.

*Sil*<br/>
Określa [typ SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level) wyliczony, który dostarcza poziom personifikacji tokenu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

`OpenThreadToken`jest podobny do [CAccessToken::GetThreadToken](#getthreadtoken), ale ustawia poziom `CAccessToken` personifikacji przed zainicjowaniem tokenu dostępu wątku.

[Klasa CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) może służyć do automatycznego przywracania personifikowanych tokenów dostępu utworzonych przez ustawienie flagi *bImpersonate* na TRUE.

## <a name="caccesstokenprivilegecheck"></a><a name="privilegecheck"></a>CAccessToken::PrivilegeCheck

Wywołanie tej metody, aby ustalić, czy określony `CAccessToken` zestaw uprawnień są włączone w obiekcie.

```
bool PrivilegeCheck(
    PPRIVILEGE_SET RequiredPrivileges,
    bool* pbResult) const throw();
```

### <a name="parameters"></a>Parametry

*WymaganePrivileges*<br/>
Wskaźnik do [struktury PRIVILEGE_SET.](/windows/win32/api/winnt/ns-winnt-privilege_set)

*pbResult (wyniki)*<br/>
Wskaźnik do wartości ustawia metody, aby wskazać, czy dowolne `CAccessToken` lub wszystkie określone uprawnienia są włączone w obiekcie.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Po `PrivilegeCheck` powrocie `Attributes` element członkowski każdej struktury [LUID_AND_ATTRIBUTES](/windows/win32/api/winnt/ns-winnt-luid_and_attributes) jest ustawiony na SE_PRIVILEGE_USED_FOR_ACCESS, jeśli odpowiednie uprawnienie jest włączone. Ta metoda wywołuje [funkcję PrivilegeCheck](/windows/win32/api/securitybaseapi/nf-securitybaseapi-privilegecheck) Win32.

## <a name="caccesstokenrevert"></a><a name="revert"></a>CAccessToken::Powrót

Wywołanie tej metody, aby zatrzymać wątku przy użyciu tokenu personifikacji.

```
bool Revert(HANDLE hThread = NULL) const throw();
```

### <a name="parameters"></a>Parametry

*hWczynienie*<br/>
Dojście do wątku, aby powrócić z personifikacji. Jeśli *hThread* ma wartość NULL, przyjmuje się bieżący wątek.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ponowne odwrót tokenów personifikacji można wykonać automatycznie za pomocą [klasy CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md).

## <a name="caccesstokensetdefaultdacl"></a><a name="setdefaultdacl"></a>CAccessToken::SetDefaultDacl

Wywołanie tej metody, aby ustawić `CAccessToken` domyślną dacl obiektu.

```
bool SetDefaultDacl(const CDacl& rDacl) throw(...);
```

### <a name="parameters"></a>Parametry

*rDacl ( rDacl )*<br/>
Nowe domyślne informacje o [klasie CDacl.](../../atl/reference/cdacl-class.md)

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Domyślna listy DACL to listy DACL, która jest używana domyślnie, gdy nowe obiekty są tworzone z tego tokenu dostępu w efekcie.

## <a name="caccesstokensetowner"></a><a name="setowner"></a>CAccessToken::SetOwner

Wywołanie tej metody, aby `CAccessToken` ustawić właściciela obiektu.

```
bool SetOwner(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parametry

*rSid (wyd.*<br/>
[CSid Class](../../atl/reference/csid-class.md) obiekt zawierający informacje o właścicielu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Właściciel jest domyślnym właścicielem, który jest używany dla nowych obiektów utworzonych, gdy ten token dostępu jest w mocy.

## <a name="caccesstokensetprimarygroup"></a><a name="setprimarygroup"></a>CAccessToken::SetPrimaryGroup

Wywołanie tej metody, aby `CAccessToken` ustawić grupę podstawową obiektu.

```
bool SetPrimaryGroup(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parametry

*rSid (wyd.*<br/>
Obiekt [klasy CSid](../../atl/reference/csid-class.md) zawierający informacje o grupie podstawowej.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Grupa podstawowa jest domyślną grupą dla nowych obiektów utworzonych, gdy ten token dostępu jest w mocy.

## <a name="see-also"></a>Zobacz też

[Przykład ATLSecurity](../../overview/visual-cpp-samples.md)<br/>
[Tokeny dostępu](/windows/win32/SecAuthZ/access-tokens)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
