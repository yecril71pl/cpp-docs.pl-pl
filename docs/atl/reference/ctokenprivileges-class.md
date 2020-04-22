---
title: Klasa CTokenPrivileges
ms.date: 11/04/2016
f1_keywords:
- CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::Add
- ATLSECURITY/ATL::CTokenPrivileges::Delete
- ATLSECURITY/ATL::CTokenPrivileges::DeleteAll
- ATLSECURITY/ATL::CTokenPrivileges::GetCount
- ATLSECURITY/ATL::CTokenPrivileges::GetDisplayNames
- ATLSECURITY/ATL::CTokenPrivileges::GetLength
- ATLSECURITY/ATL::CTokenPrivileges::GetLuidsAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetNamesAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetPTOKEN_PRIVILEGES
- ATLSECURITY/ATL::CTokenPrivileges::LookupPrivilege
helpviewer_keywords:
- CTokenPrivileges class
ms.assetid: 89590105-f001-4014-870d-142926091231
ms.openlocfilehash: 75c09f723860540aa54cf3744cde7e61d9202f79
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747363"
---
# <a name="ctokenprivileges-class"></a>Klasa CTokenPrivileges

Ta klasa jest otoką `TOKEN_PRIVILEGES` dla struktury.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class CTokenPrivileges
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTokenPrivileges::CTokenPrivileges](#ctokenprivileges)|Konstruktor.|
|[CTokenPrivileges::~CTokenPrivileges](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTokenPrivileges::Dodaj](#add)|Dodaje jeden lub więcej `CTokenPrivileges` uprawnień do obiektu.|
|[CTokenPrivileges::Delete](#delete)|Usuwa uprawnienia z `CTokenPrivileges` obiektu.|
|[CTokenPrivileges::DeleteAll](#deleteall)|Usuwa wszystkie uprawnienia z `CTokenPrivileges` obiektu.|
|[CTokenPrivileges::GetCount](#getcount)|Zwraca liczbę wpisów uprawnień `CTokenPrivileges` w obiekcie.|
|[CTokenPrivileges::GetDisplayNames](#getdisplaynames)|Pobiera nazwy wyświetlane dla uprawnień zawartych w `CTokenPrivileges` obiekcie.|
|[CTokenPrivileges::GetLength](#getlength)|Zwraca rozmiar buforu w bajtach `TOKEN_PRIVILEGES` wymaganych do `CTokenPrivileges` przechowywania struktury reprezentowane przez obiekt.|
|[CTokenPrivileges::GetLuidsAndAttributes](#getluidsandattributes)|Pobiera lokalnie unikatowe identyfikatory (LUID) i flagi `CTokenPrivileges` atrybutów z obiektu.|
|[CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes)|Pobiera nazwy uprawnień i flagi `CTokenPrivileges` atrybutów z obiektu.|
|[CTokenPrivileges::GetPTOKEN_PRIVILEGES](#getptoken_privileges)|Zwraca wskaźnik do `TOKEN_PRIVILEGES` struktury.|
|[CTokenPrivileges::LookupPrivilege](#lookupprivilege)|Pobiera atrybut skojarzony z daną nazwą uprawnień.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTokenPrivileges::operator const TOKEN_PRIVILEGES *](#operator_const_token_privileges__star)|Rzutuje wartość do wskaźnika `TOKEN_PRIVILEGES` do struktury.|
|[CTokenPrivileges::operator =](#operator_eq)|Operator przypisania.|

## <a name="remarks"></a>Uwagi

[Token dostępu](/windows/win32/SecAuthZ/access-tokens) jest obiektem opisującym kontekst zabezpieczeń procesu lub wątku i przydzielanym każdemu użytkownikowi zalogowanym do systemu Windows.

Token dostępu służy do opisywania różnych uprawnień zabezpieczeń przyznanych każdemu użytkownikowi. Uprawnienie składa się z 64-bitowego numeru o nazwie lokalnie unikatowy identyfikator [(LUID)](/windows/win32/api/winnt/ns-winnt-luid)i ciągu deskryptora.

Klasa `CTokenPrivileges` jest otoką dla [struktury TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges) i zawiera 0 lub więcej uprawnień. Uprawnienia mogą być dodawane, usuwane lub wyszukiwane przy użyciu podanych metod klasy.

Aby zapoznać się z wprowadzeniem do modelu kontroli dostępu w systemie Windows, zobacz [Kontrola dostępu](/windows/win32/SecAuthZ/access-control) w zestaw Windows SDK.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

## <a name="ctokenprivilegesadd"></a><a name="add"></a>CTokenPrivileges::Dodaj

Dodaje co najmniej jeden `CTokenPrivileges` uprawnienia do obiektu tokenu dostępu.

```
bool Add(LPCTSTR pszPrivilege, bool bEnable) throw(...);
void Add(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>Parametry

*pszPrivilege*<br/>
Wskaźnik do ciągu zakończonego zerem, który określa nazwę uprawnienia, zgodnie z definicją w WINNT. H.

*bWłaszą*<br/>
Jeśli true, uprawnienie jest włączone. Jeśli false, uprawnienie jest wyłączone.

*rPrivileges*<br/>
Odwołanie do [struktury TOKEN_PRIVILEGES.](/windows/win32/api/winnt/ns-winnt-token_privileges) Uprawnienia i atrybuty są kopiowane z tej `CTokenPrivileges` struktury i dodawane do obiektu.

### <a name="return-value"></a>Wartość zwracana

Pierwsza forma tej metody zwraca wartość true, jeśli uprawnienia są pomyślnie dodane, false w przeciwnym razie.

## <a name="ctokenprivilegesctokenprivileges"></a><a name="ctokenprivileges"></a>CTokenPrivileges::CTokenPrivileges

Konstruktor.

```
CTokenPrivileges() throw();
CTokenPrivileges(const CTokenPrivileges& rhs) throw(... );
CTokenPrivileges(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>Parametry

*Rhs*<br/>
Obiekt `CTokenPrivileges` do przypisania do nowego obiektu.

*rPrivileges*<br/>
[Struktura TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges) do przypisania do `CTokenPrivileges` nowego obiektu.

### <a name="remarks"></a>Uwagi

Obiekt `CTokenPrivileges` można opcjonalnie utworzyć `TOKEN_PRIVILEGES` przy użyciu struktury `CTokenPrivileges` lub uprzednio zdefiniowanego obiektu.

## <a name="ctokenprivilegesctokenprivileges"></a><a name="dtor"></a>CTokenPrivileges::~CTokenPrivileges

Destruktor.

```
virtual ~CTokenPrivileges() throw();
```

### <a name="remarks"></a>Uwagi

Destruktor zwalnia wszystkie przydzielone zasoby.

## <a name="ctokenprivilegesdelete"></a><a name="delete"></a>CTokenPrivileges::Delete

Usuwa uprawnienia z `CTokenPrivileges` obiektu tokenu dostępu.

```
bool Delete(LPCTSTR pszPrivilege) throw();
```

### <a name="parameters"></a>Parametry

*pszPrivilege*<br/>
Wskaźnik do ciągu zakończonego zerem, który określa nazwę uprawnienia, zgodnie z definicją w WINNT. H. Na przykład ten parametr może określić stałą SE_SECURITY_NAME lub odpowiadający jej ciąg "SeSecurityPrivilege".

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli uprawnienie zostało pomyślnie usunięte, false w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Ta metoda jest przydatna jako narzędzie do tworzenia tokenów z ograniczeniami.

## <a name="ctokenprivilegesdeleteall"></a><a name="deleteall"></a>CTokenPrivileges::DeleteAll

Usuwa wszystkie uprawnienia z `CTokenPrivileges` obiektu tokenu dostępu.

```cpp
void DeleteAll() throw();
```

### <a name="remarks"></a>Uwagi

Usuwa wszystkie uprawnienia zawarte w `CTokenPrivileges` obiekcie tokenu dostępu.

## <a name="ctokenprivilegesgetdisplaynames"></a><a name="getdisplaynames"></a>CTokenPrivileges::GetDisplayNames

Pobiera nazwy wyświetlane dla uprawnień zawartych w obiekcie tokenu `CTokenPrivileges` dostępu.

```cpp
void GetDisplayNames(CNames* pDisplayNames) const throw(...);
```

### <a name="parameters"></a>Parametry

*pWyświetlane nazwy*<br/>
Wskaźnik do tablicy `CString` obiektów. `CNames`jest zdefiniowany jako `CTokenPrivileges::CAtlArray<CString>`typedef: .

### <a name="remarks"></a>Uwagi

Parametr `pDisplayNames` jest wskaźnikiem do `CString` tablicy obiektów, które otrzymają wyświetlane nazwy odpowiadające uprawnieniam zawartym `CTokenPrivileges` w obiekcie. Ta metoda pobiera nazwy wyświetlane tylko dla uprawnień określonych w sekcji Zdefiniowane uprawnienia WINNT. H.

Ta metoda pobiera wyświetlaną nazwę: na przykład, jeśli nazwa atrybutu jest SE_REMOTE_SHUTDOWN_NAME, wyświetlana nazwa to "Wymuś zamknięcie z systemu zdalnego". Aby uzyskać nazwę systemu, należy użyć [CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes).

## <a name="ctokenprivilegesgetcount"></a><a name="getcount"></a>CTokenPrivileges::GetCount

Zwraca liczbę wpisów uprawnień `CTokenPrivileges` w obiekcie.

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę uprawnień zawartych `CTokenPrivileges` w obiekcie.

## <a name="ctokenprivilegesgetlength"></a><a name="getlength"></a>CTokenPrivileges::GetLength

Zwraca długość `CTokenPrivileges` obiektu.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę bajtów wymaganych `TOKEN_PRIVILEGES` do przechowywania struktury `CTokenPrivileges` reprezentowanej przez obiekt, w tym wszystkie wpisy uprawnień, które zawiera.

## <a name="ctokenprivilegesgetluidsandattributes"></a><a name="getluidsandattributes"></a>CTokenPrivileges::GetLuidsAndAttributes

Pobiera lokalnie unikatowe identyfikatory (LUID) i flagi `CTokenPrivileges` atrybutów z obiektu.

```cpp
void GetLuidsAndAttributes(
    CLUIDArray* pPrivileges,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pPrivileges*<br/>
Wskaźnik do tablicy obiektów [LUID.](/windows/win32/api/winnt/ns-winnt-luid) `CLUIDArray`jest typedef zdefiniowane jako `CAtlArray<LUID> CLUIDArray`.

*pAttributes (właso)*<br/>
Wskaźnik do tablicy obiektów DWORD. Jeśli ten parametr zostanie pominięty lub NULL, atrybuty nie są pobierane. `CAttributes`jest typedef zdefiniowane jako `CAtlArray <DWORD> CAttributes`.

### <a name="remarks"></a>Uwagi

Ta metoda wyliczy wszystkie uprawnienia zawarte w `CTokenPrivileges` obiekcie tokenu dostępu i umieścić poszczególne identyfikatory LUID i (opcjonalnie) flagi atrybutu do obiektów tablicy.

## <a name="ctokenprivilegesgetnamesandattributes"></a><a name="getnamesandattributes"></a>CTokenPrivileges::GetNamesAndAttributes

Pobiera flagi nazwy i atrybutu `CTokenPrivileges` z obiektu.

```cpp
void GetNamesAndAttributes(
    CNames* pNames,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pNazna*<br/>
Wskaźnik do tablicy `CString` obiektów. `CNames`jest typedef zdefiniowane jako `CAtlArray <CString> CNames`.

*pAttributes (właso)*<br/>
Wskaźnik do tablicy obiektów DWORD. Jeśli ten parametr zostanie pominięty lub NULL, atrybuty nie są pobierane. `CAttributes`jest typedef zdefiniowane jako `CAtlArray <DWORD> CAttributes`.

### <a name="remarks"></a>Uwagi

Ta metoda będzie wyliczać wszystkie uprawnienia `CTokenPrivileges` zawarte w obiekcie, umieszczając nazwę i (opcjonalnie) flagi atrybutu w obiektach tablicy.

Ta metoda pobiera nazwę atrybutu, a nie wyświetlaną nazwę: na przykład, jeśli nazwa atrybutu jest SE_REMOTE_SHUTDOWN_NAME, nazwa systemu jest "SeRemoteShutdownPrivilege". Aby uzyskać wyświetlaną nazwę, należy użyć metody [CTokenPrivileges::GetDisplayNames](#getdisplaynames).

## <a name="ctokenprivilegesgetptoken_privileges"></a><a name="getptoken_privileges"></a>CTokenPrivileges::GetPTOKEN_PRIVILEGES

Zwraca wskaźnik do `TOKEN_PRIVILEGES` struktury.

```
const TOKEN_PRIVILEGES* GetPTOKEN_PRIVILEGES() const throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do struktury [TOKEN_PRIVILEGES.](/windows/win32/api/winnt/ns-winnt-token_privileges)

## <a name="ctokenprivilegeslookupprivilege"></a><a name="lookupprivilege"></a>CTokenPrivileges::LookupPrivilege

Pobiera atrybut skojarzony z daną nazwą uprawnień.

```
bool LookupPrivilege(
    LPCTSTR pszPrivilege,
    DWORD* pdwAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pszPrivilege*<br/>
Wskaźnik do ciągu zakończonego zerem, który określa nazwę uprawnienia, zgodnie z definicją w WINNT. H. Na przykład ten parametr może określić stałą SE_SECURITY_NAME lub odpowiadający jej ciąg "SeSecurityPrivilege".

*pdwPrzyszłanie*<br/>
Wskaźnik do zmiennej, która odbiera atrybuty.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli atrybut zostanie pomyślnie pobrany, false inaczej.

## <a name="ctokenprivilegesoperator-"></a><a name="operator_eq"></a>CTokenPrivileges::operator =

Operator przypisania.

```
CTokenPrivileges& operator= (const TOKEN_PRIVILEGES& rPrivileges) throw(...);
CTokenPrivileges& operator= (const CTokenPrivileges& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*rPrivileges*<br/>
Struktura [TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges) do przypisania do `CTokenPrivileges` obiektu.

*Rhs*<br/>
Obiekt `CTokenPrivileges` do przypisania do obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CTokenPrivileges` obiekt.

## <a name="ctokenprivilegesoperator-const-token_privileges-"></a><a name="operator_const_token_privileges__star"></a>CTokenPrivileges::operator const TOKEN_PRIVILEGES\*

Rzutuje wartość do wskaźnika `TOKEN_PRIVILEGES` do struktury.

```
operator const TOKEN_PRIVILEGES *() const throw(...);
```

### <a name="remarks"></a>Uwagi

Rzutuje wartość do wskaźnika do [TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges) struktury.

## <a name="see-also"></a>Zobacz też

[Przykład zabezpieczeń](../../overview/visual-cpp-samples.md)<br/>
[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges)<br/>
[Luid](/windows/win32/api/winnt/ns-winnt-luid)<br/>
[LUID_AND_ATTRIBUTES](/windows/win32/api/winnt/ns-winnt-luid_and_attributes)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Globalne funkcje zabezpieczeń](../../atl/reference/security-global-functions.md)
