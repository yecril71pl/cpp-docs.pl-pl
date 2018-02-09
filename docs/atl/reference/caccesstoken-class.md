---
title: Klasa CAccessToken | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAccessToken class
ms.assetid: bb5c5945-56a5-4083-b442-76573cee83ab
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b8d2a314ea7697ef4379b899ee6845cd4ceca707
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="caccesstoken-class"></a>Klasa CAccessToken
Ta klasa jest otoki dla tokenu dostępu.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
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
|[CAccessToken::Attach](#attach)|Wywołaj tę metodę, aby przejąć na własność dojście tokenu dostęp.|  
|[CAccessToken::CheckTokenMembership](#checktokenmembership)|Wywołaj tę metodę, aby określić, czy określony identyfikator SID jest włączony w `CAccessToken` obiektu.|  
|[CAccessToken::CreateImpersonationToken](#createimpersonationtoken)|Wywołaj tę metodę, aby utworzyć nowy token dostępu personifikacji.|  
|[CAccessToken::CreatePrimaryToken](#createprimarytoken)|Wywołaj tę metodę, aby utworzyć nowy token podstawowy.|  
|[CAccessToken::CreateProcessAsUser](#createprocessasuser)|Wywołaj tę metodę w celu utworzenia nowego procesu uruchomiona w kontekście zabezpieczeń użytkownika reprezentowanego przez `CAccessToken` obiektu.|  
|[CAccessToken::CreateRestrictedToken](#createrestrictedtoken)|Wywołanie tej metody, aby utworzyć nową, ograniczeniami `CAccessToken` obiektu.|  
|[CAccessToken::Detach](#detach)|Wywołanie tej metody, aby można było odwołać prawa własności tokenu dostępu.|  
|[CAccessToken::DisablePrivilege](#disableprivilege)|Wywołanie tej metody, aby wyłączyć uprawnień w `CAccessToken` obiektu.|  
|[CAccessToken::DisablePrivileges](#disableprivileges)|Wywołanie tej metody, aby wyłączyć jeden lub więcej uprawnień w `CAccessToken` obiektu.|  
|[CAccessToken::EnablePrivilege](#enableprivilege)|Wywołanie tej metody, aby włączyć uprawnień w `CAccessToken` obiektu.|  
|[CAccessToken::EnablePrivileges](#enableprivileges)|Wywołanie tej metody, aby włączyć co najmniej jednego uprawnienia w `CAccessToken` obiektu.|  
|[CAccessToken::GetDefaultDacl](#getdefaultdacl)|Wywołanie tej metody, aby zwrócić `CAccessToken` obiektu domyślnej listy DACL.|  
|[CAccessToken::GetEffectiveToken](#geteffectivetoken)|Wywołanie tej metody, aby uzyskać `CAccessToken` obiektu równa tokenu dostępu dla bieżącego wątku.|  
|[CAccessToken::GetGroups](#getgroups)|Wywołanie tej metody, aby zwrócić `CAccessToken` grup token obiektu.|  
|[CAccessToken::GetHandle](#gethandle)|Wywołanie tej metody można pobrać dojścia do tokena dostępu.|  
|[CAccessToken::GetImpersonationLevel](#getimpersonationlevel)|Wywołaj tę metodę, aby uzyskać poziom personifikacji z tokenu dostępu.|  
|[CAccessToken::GetLogonSessionId](#getlogonsessionid)|Wywołanie tej metody można uzyskać Identyfikatora sesji logowania skojarzone z `CAccessToken` obiektu.|  
|[CAccessToken::GetLogonSid](#getlogonsid)|Wywołanie tej metody można pobrać identyfikatora SID logowania skojarzone z `CAccessToken` obiektu.|  
|[CAccessToken::GetOwner](#getowner)|Wywołanie tej metody można pobrać właściciela skojarzone z `CAccessToken` obiektu.|  
|[CAccessToken::GetPrimaryGroup](#getprimarygroup)|Wywołaj tę metodę, aby pobrać skojarzone z grupą podstawową `CAccessToken` obiektu.|  
|[CAccessToken::GetPrivileges](#getprivileges)|Wywołanie tej metody, aby uzyskać uprawnienia skojarzone z `CAccessToken` obiektu.|  
|[CAccessToken::GetProcessToken](#getprocesstoken)|Wywołanie tej metody można zainicjować `CAccessToken` przy użyciu tokenu dostępu z danego procesu.|  
|[CAccessToken::GetProfile](#getprofile)|Wywołanie tej metody można pobrać uchwytu wskazujący profilu użytkownika skojarzonego z `CAccessToken` obiektu.|  
|[CAccessToken::GetSource](#getsource)|Wywołanie tej metody można uzyskać źródła `CAccessToken` obiektu.|  
|[CAccessToken::GetStatistics](#getstatistics)|Wywołanie tej metody, aby uzyskać informacje związane z `CAccessToken` obiektu.|  
|[CAccessToken::GetTerminalServicesSessionId](#getterminalservicessessionid)|Wywołanie tej metody można uzyskać Identyfikatora sesji usług terminalowych skojarzone z `CAccessToken` obiektu.|  
|[CAccessToken::GetThreadToken](#getthreadtoken)|Wywołanie tej metody można zainicjować `CAccessToken` przy użyciu tokenu z danym wątku.|  
|[CAccessToken::GetTokenId](#gettokenid)|Wywołanie tej metody można uzyskać Identyfikatora tokenu skojarzone z `CAccessToken` obiektu.|  
|[CAccessToken::GetType](#gettype)|Wywołaj tę metodę, aby uzyskać token typu `CAccessToken` obiektu.|  
|[CAccessToken::GetUser](#getuser)|Wywołanie tej metody do identyfikowania użytkownika skojarzonego z `CAccessToken` obiektu.|  
|[CAccessToken::HKeyCurrentUser](#hkeycurrentuser)|Wywołanie tej metody można pobrać uchwytu wskazujący profilu użytkownika skojarzonego z `CAccessToken` obiektu.|  
|[CAccessToken::Impersonate](#impersonate)|Wywołanie tej metody można przypisać personifikacji `CAccessToken` do wątku.|  
|[CAccessToken::ImpersonateLoggedOnUser](#impersonateloggedonuser)|Wywołanie tej metody, aby umożliwić wątek wywołujący personifikować kontekst zabezpieczeń zalogowanego użytkownika.|  
|[CAccessToken::IsTokenRestricted](#istokenrestricted)|Wywołanie tej metody, aby sprawdzić, czy `CAccessToken` obiektu zawiera listę identyfikatorów SID ograniczone.|  
|[CAccessToken::LoadUserProfile](#loaduserprofile)|Wywołanie tej metody do załadowania profilu użytkownika skojarzonego z `CAccessToken` obiektu.|  
|[CAccessToken::LogonUser](#logonuser)|Wywołaj tę metodę w celu utworzenia sesji logowania dla użytkownika skojarzonego z danym poświadczeń.|  
|[CAccessToken::OpenCOMClientToken](#opencomclienttoken)|Wywołanie tej metody z wewnątrz serwer COM, wywołanie z klienta do zainicjowania obsługi `CAccessToken` przy użyciu tokenu dostępu z klienta COM.|  
|[CAccessToken::OpenNamedPipeClientToken](#opennamedpipeclienttoken)|Ta metoda jest wywoływana z wewnątrz serwer żądań pobierania przez nazwany potok zainicjować `CAccessToken` przy użyciu tokenu dostępu z klienta.|  
|[CAccessToken::OpenRPCClientToken](#openrpcclienttoken)|Wywołanie tej metody z wewnątrz wywołania RPC klienta do zainicjowania obsługi serwera `CAccessToken` przy użyciu tokenu dostępu z klienta.|  
|[CAccessToken::OpenThreadToken](#openthreadtoken)|Wywołaj tę metodę, aby ustawić poziom personifikacji, a następnie zainicjuj `CAccessToken` przy użyciu tokenu z danym wątku.|  
|[CAccessToken::PrivilegeCheck](#privilegecheck)|Wywołanie tej metody, aby określić, czy określony zestaw uprawnień są włączone w **CAccessToken** obiektu.|  
|[CAccessToken::Revert](#revert)|Wywołaj tę metodę w celu zatrzymania wątku, który używa tokenu personifikacji.|  
|[CAccessToken::SetDefaultDacl](#setdefaultdacl)|Wywołanie tej metody do określania listy DACL `CAccessToken` obiektu.|  
|[CAccessToken::SetOwner](#setowner)|Wywołanie tej metody, aby ustawić właściciela `CAccessToken` obiektu.|  
|[CAccessToken::SetPrimaryGroup](#setprimarygroup)|Wywołanie tej metody, aby ustawić grupą podstawową `CAccessToken` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 [Token dostępu](http://msdn.microsoft.com/library/windows/desktop/aa374909) jest obiekt, który opisuje kontekst zabezpieczeń proces lub Wątek i jest przydzielana każdy użytkownik zalogowany do systemu Windows.  
  
 Aby obejrzeć wprowadzenie do modelu kontroli dostępu w systemie Windows, temacie [kontroli dostępu](http://msdn.microsoft.com/library/windows/desktop/aa374860) w zestawie Windows SDK.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h  
  
##  <a name="attach"></a>CAccessToken::Attach  
 Wywołaj tę metodę, aby przejąć na własność dojście tokenu dostęp.  
  
```
void Attach(HANDLE hToken) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *hToken*  
 Dojście do tokena dostępu.  
  
### <a name="remarks"></a>Uwagi  
 W kompilacjach debugowania, wystąpi błąd potwierdzenia Jeśli `CAccessToken` obiekt ma już prawa własności tokenu dostępu.  
  
##  <a name="dtor"></a>CAccessToken:: ~ CAccessToken  
 Destruktor.  
  
```
virtual ~CAccessToken() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie przydzielone zasoby.  
  
##  <a name="checktokenmembership"></a>CAccessToken::CheckTokenMembership  
 Wywołaj tę metodę, aby określić, czy określony identyfikator SID jest włączony w `CAccessToken` obiektu.  
  
```
bool CheckTokenMembership(
    const CSid& rSid, 
    bool* pbIsMember) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rSid`  
 Odwołanie do [klasy CSid](../../atl/reference/csid-class.md) obiektu.  
  
 `pbIsMember`  
 Wskaźnik do zmiennej, która odbiera wyniki sprawdzenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 `CheckTokenMembership` Metoda sprawdza obecność identyfikatora SID użytkownika i identyfikatory SID grupy tokenu dostępu. Jeśli identyfikator SID jest obecny i ma atrybut SE_GROUP_ENABLED *pbIsMember* jest ustawiona na true; w przeciwnym razie, jest ustawiona na wartość false.  
  
 W kompilacjach debugowania, wystąpi błąd potwierdzenia Jeśli `pbIsMember` nie jest prawidłową wskaźnika.  
  
> [!NOTE]
>  `CAccessToken` Obiekt musi być token personifikacji, a nie token podstawowy.  
  
##  <a name="createimpersonationtoken"></a>CAccessToken::CreateImpersonationToken  
 Wywołaj tę metodę, aby utworzyć token dostępu personifikacji.  
  
```
bool CreateImpersonationToken(
    CAccessToken* pImp, 
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pImp`  
 Wskaźnik do nowego `CAccessToken` obiektu.  
  
 `sil`  
 Określa [SECURITY_IMPERSONATION_LEVEL](http://msdn.microsoft.com/library/windows/desktop/aa379572) wyliczany typ, który dostarcza poziom personifikacji nowy token.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 `CreateImpersonationToken`wywołania [DuplicateToken](http://msdn.microsoft.com/library/windows/desktop/aa446616) do utworzenia nowego tokenu personifikacji.  
  
##  <a name="createprimarytoken"></a>CAccessToken::CreatePrimaryToken  
 Wywołaj tę metodę, aby utworzyć nowy token podstawowy.  
  
```
bool CreatePrimaryToken(
    CAccessToken* pPri,
    DWORD dwDesiredAccess = MAXIMUM_ALLOWED,
    const CSecurityAttributes* pTokenAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *pPri*  
 Wskaźnik do nowego `CAccessToken` obiektu.  
  
 `dwDesiredAccess`  
 Określa prawa dostępu do żądanego uzyskać nowy token. Wartość domyślna MAXIMUM_ALLOWED, żąda wszystkich praw dostępu, które są prawidłowe dla obiekt wywołujący. Zobacz [prawa dostępu i maski dostępu](http://msdn.microsoft.com/library/windows/desktop/aa374902) więcej włączone prawa dostępu.  
  
 *pTokenAttributes*  
 Wskaźnik do [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) strukturę, która określa deskryptora zabezpieczeń dla nowy token i określa, czy procesy podrzędne dziedziczą tokenu. Jeśli *pTokenAttributes* ma wartość NULL, token pobiera domyślnego deskryptora zabezpieczeń i nie może być dziedziczona dojście.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 `CreatePrimaryToken`wywołania [DuplicateTokenEx](http://msdn.microsoft.com/library/windows/desktop/aa446617) Aby utworzyć nowy token podstawowy.  
  
##  <a name="createprocessasuser"></a>CAccessToken::CreateProcessAsUser  
 Wywołaj tę metodę w celu utworzenia nowego procesu uruchomiona w kontekście zabezpieczeń użytkownika reprezentowanego przez `CAccessToken` obiektu.  
  
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
 *pApplicationName*  
 Wskaźnik do zerem ciąg, który określa modułu do wykonania. Ten parametr nie może mieć wartości NULL.  
  
 *pCommandLine*  
 Wskaźnik do zerem ciąg, który określa wiersz poleceń do wykonania.  
  
 *pProcessInformation*  
 Wskaźnik do [PROCESS_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/ms684873) struktury, która otrzymuje informacje identyfikacyjne dotyczące nowego procesu.  
  
 *pStartupInfo*  
 Wskaźnik do [STARTUPINFO](http://msdn.microsoft.com/library/windows/desktop/ms686331) strukturę, która określa sposób wyświetlania głównego okna nowego procesu.  
  
 `dwCreationFlags`  
 Określa dodatkowe flagi, określające priorytet i utworzenia procesu. Zobacz opis funkcji Win32 [CreateProcessAsUser](http://msdn.microsoft.com/library/windows/desktop/ms682429) listę flag.  
  
 *bLoadProfile*  
 Jeśli PRAWDA, profil użytkownika jest załadowana [LoadUserProfile](http://msdn.microsoft.com/library/windows/desktop/bb762281).  
  
 *pProcessAttributes*  
 Wskaźnik do [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) strukturę, która określa deskryptora zabezpieczeń dla nowego procesu i określa, czy procesy podrzędne dziedziczą zwrócony dojścia. Jeśli *pProcessAttributes* ma wartość NULL, proces pobiera domyślnego deskryptora zabezpieczeń i nie może być dziedziczona dojście.  
  
 *pThreadAttributes*  
 Wskaźnik do [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) strukturę, która określa deskryptora zabezpieczeń dla nowego wątku i określa, czy procesy podrzędne dziedziczą zwrócony dojścia. Jeśli *pThreadAttributes* ma wartość NULL, wątek pobiera domyślnego deskryptora zabezpieczeń i nie może być dziedziczona dojście.  
  
 *bInherit*  
 Wskazuje, czy nowy proces dziedziczy dojść procesu wywołującego. Jeśli PRAWDA, każdy dziedziczne otwarte dojście wywoływania procesu jest dziedziczona przez nowy proces. Uchwyty odziedziczone mają te same uprawnienia dostępu i wartości, co oryginalny uchwytów.  
  
 *pCurrentDirectory*  
 Wskaźnik do zerem ciąg, który określa bieżącego dysku i katalogu dla nowego procesu. Ciąg musi być pełną ścieżką, która zawiera literę dysku. Jeśli ten parametr ma wartość NULL, nowy proces będzie mieć tego samego bieżącego dysku i katalogu jako proces wywoływania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 **CreateProcessAsUser** używa `CreateProcessAsUser` funkcji Win32 do utworzenia nowego procesu, który jest uruchamiany w kontekście zabezpieczeń użytkownika reprezentowanego przez `CAccessToken` obiektu. Zobacz opis [CreateProcessAsUser](http://msdn.microsoft.com/library/windows/desktop/ms682429) funkcja pełne omówienie wymaganych parametrów.  
  
 Tę metodę pomyślnie `CAccessToken` obiektu musi posiadać AssignPrimaryToken (o ile nie jest tokenem ograniczonym) oraz IncreaseQuota uprawnień.  
  
##  <a name="createrestrictedtoken"></a>CAccessToken::CreateRestrictedToken  
 Wywołanie tej metody, aby utworzyć nową, ograniczeniami `CAccessToken` obiektu.  
  
```
bool CreateRestrictedToken(
    CAccessToken* pRestrictedToken,
    const CTokenGroups& SidsToDisable,
    const CTokenGroups& SidsToRestrict,
    const CTokenPrivileges& PrivilegesToDelete = CTokenPrivileges()) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *pRestrictedToken*  
 Nowe, ograniczone `CAccessToken` obiektu.  
  
 `SidsToDisable`  
 A `CTokenGroups` obiekt, który określa tylko odmowa identyfikatorów SID.  
  
 *SidsToRestrict*  
 A `CTokenGroups` obiekt, który określa ograniczenie identyfikatorów SID.  
  
 `PrivilegesToDelete`  
 A `CTokenPrivileges` obiekt, który określa uprawnień do usuwania z ograniczeniami tokenu. Domyślnie tworzy pusty obiekt.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 `CreateRestrictedToken`używa [CreateRestrictedToken](http://msdn.microsoft.com/library/windows/desktop/aa446583) funkcji Win32, aby utworzyć nową `CAccessToken` obiektu z ograniczeniami.  
  
> [!IMPORTANT]
>  Korzystając z `CreateRestrictedToken`, upewnij się, że: istniejący token jest prawidłowy (i nie wprowadzone przez użytkownika) i `SidsToDisable` i `PrivilegesToDelete` są prawidłowe (i nie wprowadzone przez użytkownika). Jeśli metoda zwraca wartość false, odmowy funkcji.  
  
##  <a name="detach"></a>CAccessToken::Detach  
 Wywołanie tej metody, aby można było odwołać prawa własności tokenu dostępu.  
  
```
HANDLE Detach() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca dojście do `CAccessToken` którego został odłączony.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda odwołuje `CAccessToken`na własność tokenu dostępu.  
  
##  <a name="disableprivilege"></a>CAccessToken::DisablePrivilege  
 Wywołanie tej metody, aby wyłączyć uprawnień w `CAccessToken` obiektu.  
  
```
bool DisablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pszPrivilege`  
 Wskaźnik do ciąg zawierający uprawnień, aby wyłączyć w `CAccessToken` obiektu.  
  
 `pPreviousState`  
 Wskaźnik do `CTokenPrivileges` obiektu, który będzie zawierać poprzedni stan uprawnienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
##  <a name="disableprivileges"></a>CAccessToken::DisablePrivileges  
 Wywołanie tej metody, aby wyłączyć jeden lub więcej uprawnień w `CAccessToken` obiektu.  
  
```
bool DisablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rPrivileges`  
 Wskaźnik do tablicy ciągów, które zawierają uprawnienia, aby wyłączyć w `CAccessToken` obiektu.  
  
 `pPreviousState`  
 Wskaźnik do `CTokenPrivileges` obiektu, który będzie zawierać poprzedni stan uprawnienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
##  <a name="enableprivilege"></a>CAccessToken::EnablePrivilege  
 Wywołanie tej metody, aby włączyć uprawnień w `CAccessToken` obiektu.  
  
```
bool EnablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pszPrivilege`  
 Wskaźnik do ciąg zawierający uprawnień do włączenia w `CAccessToken` obiektu.  
  
 `pPreviousState`  
 Wskaźnik do `CTokenPrivileges` obiektu, który będzie zawierać poprzedni stan uprawnienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
##  <a name="enableprivileges"></a>CAccessToken::EnablePrivileges  
 Wywołanie tej metody, aby włączyć co najmniej jednego uprawnienia w `CAccessToken` obiektu.  
  
```
bool EnablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rPrivileges`  
 Wskaźnik do tablicy ciągów, które zawierają uprawnienia, aby włączyć w `CAccessToken` obiektu.  
  
 `pPreviousState`  
 Wskaźnik do `CTokenPrivileges` obiektu, który będzie zawierać poprzedni stan uprawnienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
##  <a name="getdefaultdacl"></a>CAccessToken::GetDefaultDacl  
 Wywołanie tej metody, aby zwrócić `CAccessToken` obiektu domyślnej listy DACL.  
  
```
bool GetDefaultDacl(CDacl* pDacl) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pDacl`  
 Wskaźnik do [klasy CDacl](../../atl/reference/cdacl-class.md) obiektu, który otrzyma **CAccessToken** obiektu domyślnej listy DACL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli domyślne listy DACL ma zostały odzyskane, wartość false w przeciwnym razie wartość.  
  
##  <a name="geteffectivetoken"></a>  CAccessToken::GetEffectiveToken  
 Wywołanie tej metody, aby uzyskać `CAccessToken` obiektu równa tokenu dostępu dla bieżącego wątku.  
  
```
bool GetEffectiveToken(DWORD dwDesiredAccess) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `dwDesiredAccess`  
 Określa maski dostępu, która określa typy żądany dostęp do tokenu dostępu. Te typy żądany dostęp, są porównywane z listy DACL tokenu, aby określić, które uzyskuje dostęp do udzielono lub odmówiono.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
##  <a name="getgroups"></a>CAccessToken::GetGroups  
 Wywołanie tej metody, aby zwrócić `CAccessToken` grup token obiektu.  
  
```
bool GetGroups(CTokenGroups* pGroups) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *pGroups*  
 Wskaźnik do [klasy CTokenGroups](../../atl/reference/ctokengroups-class.md) obiektu, który będzie otrzymywać informacje o grupie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
##  <a name="gethandle"></a>CAccessToken::GetHandle  
 Wywołanie tej metody można pobrać dojścia do tokena dostępu.  
  
```
HANDLE GetHandle() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca dojście do `CAccessToken` obiektu tokenu dostępu.  
  
##  <a name="getimpersonationlevel"></a>CAccessToken::GetImpersonationLevel  
 Wywołaj tę metodę, aby uzyskać poziom personifikacji z tokenu dostępu.  
  
```
bool GetImpersonationLevel(
    SECURITY_IMPERSONATION_LEVEL* pImpersonationLevel) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *pImpersonationLevel*  
 Wskaźnik do [SECURITY_IMPERSONATION_LEVEL](http://msdn.microsoft.com/library/windows/desktop/aa379572) typu wyliczeniowego, które będą otrzymywać informacji o poziomie personifikacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
##  <a name="getlogonsessionid"></a>CAccessToken::GetLogonSessionId  
 Wywołanie tej metody można uzyskać Identyfikatora sesji logowania skojarzone z `CAccessToken` obiektu.  
  
```
bool GetLogonSessionId(LUID* pluid) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pluid`  
 Wskaźnik do [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261) którego zostanie wyświetlony identyfikator sesji logowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 W kompilacjach debugowania, wystąpi błąd potwierdzenia Jeśli `pluid` jest nieprawidłową wartością.  
  
##  <a name="getlogonsid"></a>CAccessToken::GetLogonSid  
 Wywołanie tej metody można pobrać identyfikatora SID logowania skojarzone z `CAccessToken` obiektu.  
  
```
bool GetLogonSid(CSid* pSid) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pSid`  
 Wskaźnik do [klasy CSid](../../atl/reference/csid-class.md) obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 W kompilacjach debugowania, wystąpi błąd potwierdzenia Jeśli *pSid* jest nieprawidłową wartością.  
  
##  <a name="getowner"></a>CAccessToken::GetOwner  
 Wywołanie tej metody można pobrać właściciela skojarzone z `CAccessToken` obiektu.  
  
```
bool GetOwner(CSid* pSid) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pSid`  
 Wskaźnik do [klasy CSid](../../atl/reference/csid-class.md) obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Właściciel jest ustawiona domyślnie na wszystkie obiekty utworzone ten token dostępu w czasie działania.  
  
##  <a name="getprimarygroup"></a>  CAccessToken::GetPrimaryGroup  
 Wywołaj tę metodę, aby pobrać skojarzone z grupą podstawową `CAccessToken` obiektu.  
  
```
bool GetPrimaryGroup(CSid* pSid) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pSid`  
 Wskaźnik do [klasy CSid](../../atl/reference/csid-class.md) obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Grupa jest ustawiona domyślnie na wszystkie obiekty utworzone ten token dostępu w czasie działania.  
  
##  <a name="getprivileges"></a>CAccessToken::GetPrivileges  
 Wywołanie tej metody, aby uzyskać uprawnienia skojarzone z `CAccessToken` obiektu.  
  
```
bool GetPrivileges(CTokenPrivileges* pPrivileges) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pPrivileges`  
 Wskaźnik do [klasy CTokenPrivileges](../../atl/reference/ctokenprivileges-class.md) obiektu, który otrzyma uprawnienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
##  <a name="getprocesstoken"></a>CAccessToken::GetProcessToken  
 Wywołanie tej metody można zainicjować `CAccessToken` przy użyciu tokenu dostępu z danego procesu.  
  
```
bool GetProcessToken(DWORD dwDesiredAccess, HANDLE hProcess = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `dwDesiredAccess`  
 Określa maski dostępu, która określa typy żądany dostęp do tokenu dostępu. Te typy żądany dostęp, są porównywane z listy DACL tokenu, aby określić, które uzyskuje dostęp do udzielono lub odmówiono.  
  
 *hProcess*  
 Dojście do procesu, w których token dostępu jest otwarty. Jeśli domyślna wartość `NULL` jest używana, bieżący proces jest używany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `true` w przypadku powodzenia `false` w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [OpenProcessToken](http://msdn.microsoft.com/library/aa379295\(vs.85\).aspx) funkcji Win32.  
  
##  <a name="getprofile"></a>CAccessToken::GetProfile  
 Wywołanie tej metody można pobrać uchwytu wskazujący profilu użytkownika skojarzonego z `CAccessToken` obiektu.  
  
```
HANDLE GetProfile() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca uchwyt wskazujący profilu użytkownika lub wartość NULL, jeśli nie istnieje profil.  
  
##  <a name="getsource"></a>CAccessToken::GetSource  
 Wywołanie tej metody można uzyskać źródła `CAccessToken` obiektu.  
  
```
bool GetSource(TOKEN_SOURCE* pSource) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *pSource*  
 Wskaźnik do [TOKEN_SOURCE](http://msdn.microsoft.com/library/windows/desktop/aa379631) struktury.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
##  <a name="getstatistics"></a>CAccessToken::GetStatistics  
 Wywołanie tej metody, aby uzyskać informacje związane z `CAccessToken` obiektu.  
  
```
bool GetStatistics(TOKEN_STATISTICS* pStatistics) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *pStatistics*  
 Wskaźnik do [TOKEN_STATISTICS](http://msdn.microsoft.com/library/windows/desktop/aa379632) struktury.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
##  <a name="getterminalservicessessionid"></a>  CAccessToken::GetTerminalServicesSessionId  
 Wywołanie tej metody można uzyskać Identyfikatora sesji usług terminalowych skojarzone z `CAccessToken` obiektu.  
  
```
bool GetTerminalServicesSessionId(DWORD* pdwSessionId) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *pdwSessionId*  
 Identyfikator sesji usług terminalowych.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
##  <a name="getthreadtoken"></a>CAccessToken::GetThreadToken  
 Wywołanie tej metody można zainicjować `CAccessToken` przy użyciu tokenu z danym wątku.  
  
```
bool GetThreadToken(
    DWORD dwDesiredAccess,
    HANDLE hThread = NULL,
    bool bOpenAsSelf = true) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `dwDesiredAccess`  
 Określa maski dostępu, która określa typy żądany dostęp do tokenu dostępu. Te typy żądany dostęp, są porównywane z listy DACL tokenu, aby określić, które uzyskuje dostęp do udzielono lub odmówiono.  
  
 `hThread`  
 Dojście do wątku, w których token dostępu jest otwarty.  
  
 `bOpenAsSelf`  
 Wskazuje, czy sprawdzanie dostępu ma zostać wykonane w stosunku do kontekstu zabezpieczeń wywołania wątku `GetThreadToken` metody lub względem procesu wątek wywołujący kontekstu zabezpieczeń.  
  
 Jeśli ten parametr ma wartość false, sprawdzanie dostępu odbywa się przy użyciu kontekstu zabezpieczeń dla wywołania wątku. Jeśli wątek personifikuje klienta, ten kontekst zabezpieczeń może być procesu klienta. Jeśli ten parametr ma wartość true, sprawdzenie dostępu jest wykonywane w kontekście zabezpieczeń procesu, wątku wywołującym.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
##  <a name="gettokenid"></a>CAccessToken::GetTokenId  
 Wywołanie tej metody można uzyskać Identyfikatora tokenu skojarzone z `CAccessToken` obiektu.  
  
```
bool GetTokenId(LUID* pluid) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pluid`  
 Wskaźnik do [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261) którego zostanie wyświetlony identyfikator tokenu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
##  <a name="gettype"></a>CAccessToken::GetType  
 Wywołaj tę metodę, aby uzyskać token typu `CAccessToken` obiektu.  
  
```
bool GetType(TOKEN_TYPE* pType) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pType`  
 Adres [TOKEN_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379633) zmiennej, która w przypadku powodzenia otrzymuje typ tokenu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 **TOKEN_TYPE** typu wyliczeniowego zawiera wartości, które rozróżnianie między podstawowym token i token personifikacji.  
  
##  <a name="getuser"></a>CAccessToken::GetUser  
 Wywołanie tej metody do identyfikowania użytkownika skojarzonego z `CAccessToken` obiektu.  
  
```
bool GetUser(CSid* pSid) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pSid`  
 Wskaźnik do [klasy CSid](../../atl/reference/csid-class.md) obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
##  <a name="hkeycurrentuser"></a>CAccessToken::HKeyCurrentUser  
 Wywołanie tej metody można pobrać uchwytu wskazujący profilu użytkownika skojarzonego z `CAccessToken` obiektu.  
  
```
HKEY HKeyCurrentUser() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca uchwyt wskazujący profilu użytkownika lub wartość NULL, jeśli nie istnieje profil.  
  
##  <a name="impersonate"></a>CAccessToken::Impersonate  
 Wywołanie tej metody można przypisać personifikacji `CAccessToken` do wątku.  
  
```
bool Impersonate(HANDLE hThread = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `hThread`  
 Dojście do wątku można przypisać do tokenu personifikacji. Ta dojścia musi została otwarta z TOKEN_IMPERSONATE praw dostępu. Jeśli `hThread` ma wartość NULL, metoda powoduje, że wątek można zatrzymać za pomocą tokenu personifikacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 W kompilacjach debugowania, wystąpi błąd potwierdzenia Jeśli `CAccessToken` nie ma prawidłowego wskaźnika do tokenu.  
  
 [CAutoRevertImpersonation klasy](../../atl/reference/cautorevertimpersonation-class.md) może służyć do automatycznie odwracamy tokeny personifikowanej dostępu.  
  
##  <a name="impersonateloggedonuser"></a>CAccessToken::ImpersonateLoggedOnUser  
 Wywołanie tej metody, aby umożliwić wątek wywołujący personifikować kontekst zabezpieczeń zalogowanego użytkownika.  
  
```
bool ImpersonateLoggedOnUser() const throw(...);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
  
> [!IMPORTANT]
>  Jeśli wywołanie funkcji personifikacji nie powiedzie się z jakiegokolwiek powodu, klient nie jest traktowane i żądanie klienta jest nawiązywane w kontekście zabezpieczeń procesu, z którego wykonano wywołanie. Jeśli proces działa jako wysoko uprzywilejowane konto lub jako członek grupy administratorów, użytkownik będzie mógł wykonywać akcje on w przeciwnym razie będzie niedozwolone. W związku z tym należy potwierdzić zawsze wartość zwracaną dla tej funkcji.  
  
##  <a name="istokenrestricted"></a>CAccessToken::IsTokenRestricted  
 Wywołanie tej metody, aby sprawdzić, czy `CAccessToken` obiektu zawiera listę identyfikatorów SID ograniczone.  
  
```
bool IsTokenRestricted() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true, jeśli obiekt zawiera listę ograniczanie identyfikatory SID, wartość false, jeśli nie ma żadnych ograniczenie identyfikatorów SID lub metoda nie powiedzie się.  
  
##  <a name="loaduserprofile"></a>CAccessToken::LoadUserProfile  
 Wywołanie tej metody do załadowania profilu użytkownika skojarzonego z `CAccessToken` obiektu.  
  
```
bool LoadUserProfile() throw(...);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 W kompilacjach debugowania, wystąpi błąd potwierdzenia Jeśli `CAccessToken` nie zawiera prawidłowego tokenu lub jeśli użytkownik profilu już istnieje.  
  
##  <a name="logonuser"></a>CAccessToken::LogonUser  
 Wywołaj tę metodę w celu utworzenia sesji logowania dla użytkownika skojarzonego z danym poświadczeń.  
  
```
bool LogonUser(
    LPCTSTR pszUserName,
    LPCTSTR pszDomain,
    LPCTSTR pszPassword,
    DWORD dwLogonType = LOGON32_LOGON_INTERACTIVE,
    DWORD dwLogonProvider = LOGON32_PROVIDER_DEFAULT) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszUserName`  
 Wskaźnik do zerem ciąg, który określa nazwę użytkownika. Jest to nazwa zalogować się do konta użytkownika.  
  
 *pszDomain*  
 Wskaźnik do zerem ciąg, który określa nazwę domeny lub serwer, którego konto bazy danych zawiera `pszUserName` konta.  
  
 `pszPassword`  
 Wskaźnik do zerem ciąg, który określa hasło konta użytkownika określonego przez zwykłym tekstem `pszUserName`.  
  
 *dwLogonType*  
 Określa typ operacji logowania do wykonania. Zobacz [funkcji LogonUser](http://msdn.microsoft.com/library/windows/desktop/aa378184) więcej szczegółów.  
  
 *dwLogonProvider*  
 Określa dostawcę logowania. Zobacz [funkcji LogonUser](http://msdn.microsoft.com/library/windows/desktop/aa378184) więcej szczegółów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Dostęp tokenu wynikające z logowanie zostaną skojarzone z `CAccessToken`. Tę metodę pomyślnie `CAccessToken` obiektu musi posiadać uprawnienia SE_TCB_NAME, identyfikacji posiadacza jako część zaufany komputer podstawowy. Zobacz [funkcji LogonUser](http://msdn.microsoft.com/library/windows/desktop/aa378184) uzyskać więcej informacji dotyczących uprawnień wymaganych.  
  
##  <a name="opencomclienttoken"></a>CAccessToken::OpenCOMClientToken  
 Wywołanie tej metody z wewnątrz serwer COM, wywołanie z klienta do zainicjowania obsługi `CAccessToken` przy użyciu tokenu dostępu z klienta COM.  
  
```
bool OpenCOMClientToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `dwDesiredAccess`  
 Określa maski dostępu, która określa typy żądany dostęp do tokenu dostępu. Te typy żądany dostęp, są porównywane z listy DACL tokenu, aby określić, które uzyskuje dostęp do udzielono lub odmówiono.  
  
 `bImpersonate`  
 Jeśli PRAWDA, bieżący wątek personifikować klienta wywołującego COM, jeśli to wywołanie zostało ukończone pomyślnie. W przypadku wartości FAŁSZ, będzie można otworzyć tokenu dostępu, ale wątek nie będą miały token personifikacji po zakończeniu tego połączenia.  
  
 `bOpenAsSelf`  
 Wskazuje, czy sprawdzanie dostępu ma zostać wykonane w stosunku do kontekstu zabezpieczeń wywołania wątku [GetThreadToken](http://msdn.microsoft.com/library/windows/desktop/ms683182) metody lub względem procesu wątek wywołujący kontekstu zabezpieczeń.  
  
 Jeśli ten parametr ma wartość false, sprawdzanie dostępu odbywa się przy użyciu kontekstu zabezpieczeń dla wywołania wątku. Jeśli wątek personifikuje klienta, ten kontekst zabezpieczeń może być procesu klienta. Jeśli ten parametr ma wartość true, sprawdzenie dostępu jest wykonywane w kontekście zabezpieczeń procesu, wątku wywołującym.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 [Klasy CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) może służyć do automatycznie odwracamy tokenów dostępu personifikowanej utworzone przez ustawienie `bImpersonate` flaga *true*.  
  
##  <a name="opennamedpipeclienttoken"></a>CAccessToken::OpenNamedPipeClientToken  
 Ta metoda jest wywoływana z wewnątrz serwer żądań pobierania przez nazwany potok zainicjować `CAccessToken` przy użyciu tokenu dostępu z klienta.  
  
```
bool OpenNamedPipeClientToken(
    HANDLE hPipe,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *hPipe*  
 Dojście do nazwanego potoku.  
  
 `dwDesiredAccess`  
 Określa maski dostępu, która określa typy żądany dostęp do tokenu dostępu. Te typy żądany dostęp, są porównywane z listy DACL tokenu, aby określić, które uzyskuje dostęp do udzielono lub odmówiono.  
  
 `bImpersonate`  
 Jeśli PRAWDA, bieżący wątek personifikować klienta wywołującego potoku, jeśli to wywołanie zostało ukończone pomyślnie. W przypadku wartości FAŁSZ, będzie można otworzyć tokenu dostępu, ale wątek nie będą miały token personifikacji po zakończeniu tego połączenia.  
  
 `bOpenAsSelf`  
 Wskazuje, czy sprawdzanie dostępu ma zostać wykonane w stosunku do kontekstu zabezpieczeń wywołania wątku [GetThreadToken](http://msdn.microsoft.com/library/windows/desktop/ms683182) metody lub względem procesu wątek wywołujący kontekstu zabezpieczeń.  
  
 Jeśli ten parametr ma wartość false, sprawdzanie dostępu odbywa się przy użyciu kontekstu zabezpieczeń dla wywołania wątku. Jeśli wątek personifikuje klienta, ten kontekst zabezpieczeń może być procesu klienta. Jeśli ten parametr ma wartość true, sprawdzenie dostępu jest wykonywane w kontekście zabezpieczeń procesu, wątku wywołującym.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 [Klasy CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) może służyć do automatycznie odwracamy tokenów dostępu personifikowanej utworzone przez ustawienie `bImpersonate` flaga *true*.  
  
##  <a name="openrpcclienttoken"></a>CAccessToken::OpenRPCClientToken  
 Wywołanie tej metody z wewnątrz wywołania RPC klienta do zainicjowania obsługi serwera `CAccessToken` przy użyciu tokenu dostępu z klienta.  
  
```
bool OpenRPCClientToken(
    RPC_BINDING_HANDLE BindingHandle,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *BindingHandle*  
 Dojście powiązania na serwerze, który reprezentuje powiązanie do klienta.  
  
 `dwDesiredAccess`  
 Określa maski dostępu, która określa typy żądany dostęp do tokenu dostępu. Te typy żądany dostęp, są porównywane z listy DACL tokenu, aby określić, które uzyskuje dostęp do udzielono lub odmówiono.  
  
 `bImpersonate`  
 Jeśli PRAWDA, bieżący wątek personifikować klienta wywołującego RPC, jeśli to wywołanie zostało ukończone pomyślnie. W przypadku wartości FAŁSZ, będzie można otworzyć tokenu dostępu, ale wątek nie będą miały token personifikacji po zakończeniu tego połączenia.  
  
 `bOpenAsSelf`  
 Wskazuje, czy sprawdzanie dostępu ma zostać wykonane w stosunku do kontekstu zabezpieczeń wywołania wątku [GetThreadToken](http://msdn.microsoft.com/library/windows/desktop/ms683182) metody lub względem procesu wątek wywołujący kontekstu zabezpieczeń.  
  
 Jeśli ten parametr ma wartość false, sprawdzanie dostępu odbywa się przy użyciu kontekstu zabezpieczeń dla wywołania wątku. Jeśli wątek personifikuje klienta, ten kontekst zabezpieczeń może być procesu klienta. Jeśli ten parametr ma wartość true, sprawdzenie dostępu jest wykonywane w kontekście zabezpieczeń procesu, wątku wywołującym.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 [Klasy CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) może służyć do automatycznie odwracamy tokenów dostępu personifikowanej utworzone przez ustawienie `bImpersonate` flaga *true*.  
  
##  <a name="openthreadtoken"></a>CAccessToken::OpenThreadToken  
 Wywołaj tę metodę, aby ustawić poziom personifikacji, a następnie zainicjuj `CAccessToken` przy użyciu tokenu z danym wątku.  
  
```
bool OpenThreadToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `dwDesiredAccess`  
 Określa maski dostępu, która określa typy żądany dostęp do tokenu dostępu. Te typy żądany dostęp, są porównywane z listy DACL tokenu, aby określić, które uzyskuje dostęp do udzielono lub odmówiono.  
  
 `bImpersonate`  
 Jeśli PRAWDA, wątku pozostanie na poziomie żądanego personifikacji po zakończeniu tej metody. W przypadku wartości FAŁSZ wątek powróci do jej oryginalnej poziom personifikacji.  
  
 `bOpenAsSelf`  
 Wskazuje, czy sprawdzanie dostępu ma zostać wykonane w stosunku do kontekstu zabezpieczeń wywołania wątku [GetThreadToken](http://msdn.microsoft.com/library/windows/desktop/ms683182) metody lub względem procesu wątek wywołujący kontekstu zabezpieczeń.  
  
 Jeśli ten parametr ma wartość false, sprawdzanie dostępu odbywa się przy użyciu kontekstu zabezpieczeń dla wywołania wątku. Jeśli wątek personifikuje klienta, ten kontekst zabezpieczeń może być procesu klienta. Jeśli ten parametr ma wartość true, sprawdzenie dostępu jest wykonywane w kontekście zabezpieczeń procesu, wątku wywołującym.  
  
 `sil`  
 Określa [SECURITY_IMPERSONATION_LEVEL](http://msdn.microsoft.com/library/windows/desktop/aa379572) wyliczany typ, który dostarcza poziom personifikacji tokenu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 `OpenThreadToken`przypomina [CAccessToken::GetThreadToken](#getthreadtoken), ale ustawia poziom personifikacji przed inicjowanie `CAccessToken` z wątku tokenu dostępu.  
  
 [Klasy CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) może służyć do automatycznie odwracamy tokenów dostępu personifikowanej utworzone przez ustawienie `bImpersonate` flaga *true*.  
  
##  <a name="privilegecheck"></a>CAccessToken::PrivilegeCheck  
 Wywołanie tej metody, aby określić, czy określony zestaw uprawnień są włączone w **CAccessToken** obiektu.  
  
```
bool PrivilegeCheck(
    PPRIVILEGE_SET RequiredPrivileges,
     bool* pbResult) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *RequiredPrivileges*  
 Wskaźnik do [PRIVILEGE_SET](http://msdn.microsoft.com/library/windows/desktop/aa379307) struktury.  
  
 *pbResult*  
 Wskaźnik do wartości metody ustawia wskazująca, czy niektóre lub wszystkie z określonych uprawnień są włączone w `CAccessToken` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Gdy `PrivilegeCheck` zwraca, **atrybuty** z każdej [LUID_AND_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379263) struktury jest ustawiony na SE_PRIVILEGE_USED_FOR_ACCESS, jeśli jest włączone odpowiednie uprawnienie. Ta metoda wywołuje [PrivilegeCheck](http://msdn.microsoft.com/library/windows/desktop/aa379304) funkcji Win32.  
  
##  <a name="revert"></a>CAccessToken::Revert  
 Wywołaj tę metodę w celu zatrzymania wątku z za pomocą tokenu personifikacji.  
  
```
bool Revert(HANDLE hThread = NULL) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hThread`  
 Dojście do wątku można przywrócić z personifikacji. Jeśli *hThread* ma wartość NULL, zakłada, że bieżący wątek.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Odwrócenie personifikacji tokenów może odbywać się automatycznie przy użyciu [CAutoRevertImpersonation klasy](../../atl/reference/cautorevertimpersonation-class.md).  
  
##  <a name="setdefaultdacl"></a>CAccessToken::SetDefaultDacl  
 Wywołanie tej metody do określania listy DACL `CAccessToken` obiektu.  
  
```
bool SetDefaultDacl(const CDacl& rDacl) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rDacl`  
 Nowym domyślnym [klasy CDacl](../../atl/reference/cdacl-class.md) informacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie lista DACL jest lista DACL używany domyślnie, gdy nowe obiekty są tworzone z tym tokenem dostępu w celu.  
  
##  <a name="setowner"></a>CAccessToken::SetOwner  
 Wywołanie tej metody, aby ustawić właściciela `CAccessToken` obiektu.  
  
```
bool SetOwner(const CSid& rSid) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rSid`  
 [Klasy CSid](../../atl/reference/csid-class.md) obiekt zawierający informacje o właścicielu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Właściciel jest domyślnego właściciela, który służy do nowych obiektów tworzonych ten token dostępu w czasie działania.  
  
##  <a name="setprimarygroup"></a>  CAccessToken::SetPrimaryGroup  
 Wywołanie tej metody, aby ustawić grupą podstawową `CAccessToken` obiektu.  
  
```
bool SetPrimaryGroup(const CSid& rSid) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rSid`  
 [Klasy CSid](../../atl/reference/csid-class.md) obiektu zawierającego informacje grupy podstawowej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true w przypadku powodzenia; wartość false w razie niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Grupy podstawowej to grupa domyślna dla nowych obiektów tworzonych ten token dostępu w czasie działania.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe ATLSecurity](../../visual-cpp-samples.md)   
 [Tokeny dostępu](http://msdn.microsoft.com/library/windows/desktop/aa374909)   
 [Przegląd klas](../../atl/atl-class-overview.md)
