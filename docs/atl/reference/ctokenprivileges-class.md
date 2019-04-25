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
ms.openlocfilehash: 8bca3e1d45d0a85d1d4ceac4ffdf7b11091020f6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62277308"
---
# <a name="ctokenprivileges-class"></a>Klasa CTokenPrivileges

Ta klasa jest otoką `TOKEN_PRIVILEGES` struktury.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

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
|[CTokenPrivileges::Add](#add)|Dodaje co najmniej uprawnienia do `CTokenPrivileges` obiektu.|
|[CTokenPrivileges::Delete](#delete)|Usuwa uprawnień z `CTokenPrivileges` obiektu.|
|[CTokenPrivileges::DeleteAll](#deleteall)|Usuwa wszystkie uprawnienia z `CTokenPrivileges` obiektu.|
|[CTokenPrivileges::GetCount](#getcount)|Zwraca liczbę wpisy uprawnień w `CTokenPrivileges` obiektu.|
|[CTokenPrivileges::GetDisplayNames](#getdisplaynames)|Pobiera wyświetlane nazwy uprawnień zawarty w `CTokenPrivileges` obiektu.|
|[CTokenPrivileges::GetLength](#getlength)|Zwraca rozmiar buforu w bajtach wymaganych do przechowywania `TOKEN_PRIVILEGES` struktury reprezentowany przez `CTokenPrivileges` obiektu.|
|[CTokenPrivileges::GetLuidsAndAttributes](#getluidsandattributes)|Pobiera lokalne unikatowe identyfikatory (LUID) i atrybut flag z `CTokenPrivileges` obiektu.|
|[CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes)|Pobiera nazwy uprawnień i atrybut flag z `CTokenPrivileges` obiektu.|
|[CTokenPrivileges::GetPTOKEN_PRIVILEGES](#getptoken_privileges)|Zwraca wskaźnik do `TOKEN_PRIVILEGES` struktury.|
|[CTokenPrivileges::LookupPrivilege](#lookupprivilege)|Pobiera atrybut skojarzony z nazwę danego uprawnienia.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTokenPrivileges::operator const TOKEN_PRIVILEGES *](#operator_const_token_privileges__star)|Rzutuje na wskaźnik do wartości `TOKEN_PRIVILEGES` struktury.|
|[CTokenPrivileges::operator =](#operator_eq)|Operator przypisania.|

## <a name="remarks"></a>Uwagi

[Token dostępu](/windows/desktop/SecAuthZ/access-tokens) jest obiektem, w tym artykule opisano proces lub wątek kontekstu zabezpieczeń, która jest przydzielona do każdego użytkownika zalogowanego w systemie Windows.

Token dostępu jest używany do opisania różnych przyznane każdemu użytkownikowi uprawnienia zabezpieczeń. Uprawnienia składa się z 64-bitowa liczba, o nazwie lokalnie unikatowy identyfikator ( [LUID](/windows/desktop/api/winnt/ns-winnt-_luid)) i ciągu deskryptora.

`CTokenPrivileges` Klasy jest otoką [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges) struktury i zawiera 0 lub wyższego poziomu uprawnień. Uprawnienia mogą być dodawane, usunięty lub kwerendy, przy użyciu metody podanej klasy.

Wprowadzenie do modelu kontroli dostępu w Windows, zobacz [kontroli dostępu](/windows/desktop/SecAuthZ/access-control) w zestawie Windows SDK.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

##  <a name="add"></a>  CTokenPrivileges::Add

Dodaje co najmniej uprawnienia do `CTokenPrivileges` obiektu tokenu dostępu.

```
bool Add(LPCTSTR pszPrivilege, bool bEnable) throw(...);
void Add(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>Parametry

*pszPrivilege*<br/>
Wskaźnik Określa nazwę uprawnienia, zgodnie z definicją w WINNT ciąg zakończony znakiem null. Plik nagłówkowy H.

*bWłączenie*<br/>
W przypadku opcji true jest włączone uprawnienia. W przypadku wartości FAŁSZ uprawnienie jest wyłączone.

*rPrivileges*<br/>
Odwołanie do [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges) struktury. Uprawnienia i atrybuty są kopiowane z tej struktury i dodawane do `CTokenPrivileges` obiektu.

### <a name="return-value"></a>Wartość zwracana

Pierwszy formularz ta metoda zwraca wartość true, jeśli uprawnienia zostaną pomyślnie dodane, wartość false w przeciwnym razie.

##  <a name="ctokenprivileges"></a>  CTokenPrivileges::CTokenPrivileges

Konstruktor.

```
CTokenPrivileges() throw();
CTokenPrivileges(const CTokenPrivileges& rhs) throw(... );
CTokenPrivileges(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>Parametry

*RHS*<br/>
`CTokenPrivileges` Obiekt można przypisać do nowego obiektu.

*rPrivileges*<br/>
[TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges) struktury można przypisać do nowego `CTokenPrivileges` obiektu.

### <a name="remarks"></a>Uwagi

`CTokenPrivileges` Opcjonalnie można utworzyć obiekt przy użyciu `TOKEN_PRIVILEGES` struktury lub uprzednio zdefiniowany `CTokenPrivileges` obiektu.

##  <a name="dtor"></a>  CTokenPrivileges::~CTokenPrivileges

Destruktor.

```
virtual ~CTokenPrivileges() throw();
```

### <a name="remarks"></a>Uwagi

Destruktor zwalnia wszystkie przydzielone zasoby.

##  <a name="delete"></a>  CTokenPrivileges::Delete

Usuwa uprawnień z `CTokenPrivileges` obiektu tokenu dostępu.

```
bool Delete(LPCTSTR pszPrivilege) throw();
```

### <a name="parameters"></a>Parametry

*pszPrivilege*<br/>
Wskaźnik Określa nazwę uprawnienia, zgodnie z definicją w WINNT ciąg zakończony znakiem null. Plik nagłówkowy H. Na przykład ten parametr można określić stałą SE_SECURITY_NAME lub jej odpowiedni ciąg "SeSecurityPrivilege."

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli uprawnienie zostało pomyślnie usunięte, wartość false w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Ta metoda jest przydatna jako narzędzie do tworzenia tokenów ograniczone.

##  <a name="deleteall"></a>  CTokenPrivileges::DeleteAll

Usuwa wszystkie uprawnienia z `CTokenPrivileges` obiektu tokenu dostępu.

```
void DeleteAll() throw();
```

### <a name="remarks"></a>Uwagi

Usuwa wszystkie uprawnienia zawarte w `CTokenPrivileges` obiektu tokenu dostępu.

##  <a name="getdisplaynames"></a>  CTokenPrivileges::GetDisplayNames

Pobiera wyświetlane nazwy uprawnień zawarty w `CTokenPrivileges` obiektu tokenu dostępu.

```
void GetDisplayNames(CNames* pDisplayNames) const throw(...);
```

### <a name="parameters"></a>Parametry

*pDisplayNames*<br/>
Wskaźnik do tablicy `CString` obiektów. `CNames` jest zdefiniowany jako element typedef: `CTokenPrivileges::CAtlArray<CString>`.

### <a name="remarks"></a>Uwagi

Parametr `pDisplayNames` jest wskaźnikiem do tablicy `CString` obiekty, które będą odbierać nazw wyświetlanych odpowiadający uprawnień zawarty w `CTokenPrivileges` obiektu. Ta metoda umożliwia pobranie nazwy wyświetlane tylko w przypadku uprawnienia określone w sekcji uprawnień zdefiniowane Windows NT. H.

Ta metoda umożliwia pobranie nazwy wyświetlanej: na przykład, jeśli nazwa atrybutu jest SE_REMOTE_SHUTDOWN_NAME, jego nazwa jest "Wymuszanie zamknięcia systemu z systemu zdalnego". Aby uzyskać nazwę systemu, należy użyć [CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes).

##  <a name="getcount"></a>  CTokenPrivileges::GetCount

Zwraca liczbę wpisy uprawnień w `CTokenPrivileges` obiektu.

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę uprawnień zawarty w `CTokenPrivileges` obiektu.

##  <a name="getlength"></a>  CTokenPrivileges::GetLength

Zwraca długość `CTokenPrivileges` obiektu.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę bajtów potrzebną do przechowania `TOKEN_PRIVILEGES` struktury reprezentowany przez `CTokenPrivileges` obiekt, w tym wszystkie wpisy uprawnień, które zawiera.

##  <a name="getluidsandattributes"></a>  CTokenPrivileges::GetLuidsAndAttributes

Pobiera lokalne unikatowe identyfikatory (LUID) i atrybut flag z `CTokenPrivileges` obiektu.

```
void GetLuidsAndAttributes(
    CLUIDArray* pPrivileges,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pPrivileges*<br/>
Wskaźnik do tablicy [LUID](/windows/desktop/api/winnt/ns-winnt-_luid) obiektów. `CLUIDArray` element typedef jest zdefiniowany jako `CAtlArray<LUID> CLUIDArray`.

*pAttributes*<br/>
Wskaźnik do tablicy obiektów typu DWORD. Jeśli ten parametr jest pominięty lub ma wartość NULL, atrybuty nie są pobierane. `CAttributes` element typedef jest zdefiniowany jako `CAtlArray <DWORD> CAttributes`.

### <a name="remarks"></a>Uwagi

Ta metoda powoduje wyliczenie wszystkich uprawnień zawarty w `CTokenPrivileges` dostęp do obiektu tokenu i umieszczenie poszczególnych LUID i (opcjonalnie) flagi atrybutów w tablicy obiektów.

##  <a name="getnamesandattributes"></a>  CTokenPrivileges::GetNamesAndAttributes

Pobiera nazwę i atrybut flag z `CTokenPrivileges` obiektu.

```
void GetNamesAndAttributes(
    CNames* pNames,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pNames*<br/>
Wskaźnik do tablicy `CString` obiektów. `CNames` element typedef jest zdefiniowany jako `CAtlArray <CString> CNames`.

*pAttributes*<br/>
Wskaźnik do tablicy obiektów typu DWORD. Jeśli ten parametr jest pominięty lub ma wartość NULL, atrybuty nie są pobierane. `CAttributes` element typedef jest zdefiniowany jako `CAtlArray <DWORD> CAttributes`.

### <a name="remarks"></a>Uwagi

Ta metoda powoduje wyliczenie wszystkich uprawnień zawarty w `CTokenPrivileges` obiektu, umieszczając nazwę i (opcjonalnie) flagi atrybutów na tablicy obiektów.

Ta metoda umożliwia pobranie nazwy atrybutu, a nie nazwy wyświetlanej: na przykład, jeśli nazwa atrybutu jest SE_REMOTE_SHUTDOWN_NAME, nazwa systemowa jest "SeRemoteShutdownPrivilege w odniesieniu." Aby uzyskać jego nazwa, należy użyć metody [CTokenPrivileges::GetDisplayNames](#getdisplaynames).

##  <a name="getptoken_privileges"></a>  CTokenPrivileges::GetPTOKEN_PRIVILEGES

Zwraca wskaźnik do `TOKEN_PRIVILEGES` struktury.

```
const TOKEN_PRIVILEGES* GetPTOKEN_PRIVILEGES() const throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges) struktury.

##  <a name="lookupprivilege"></a>  CTokenPrivileges::LookupPrivilege

Pobiera atrybut skojarzony z nazwę danego uprawnienia.

```
bool LookupPrivilege(
    LPCTSTR pszPrivilege,
    DWORD* pdwAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pszPrivilege*<br/>
Wskaźnik Określa nazwę uprawnienia, zgodnie z definicją w WINNT ciąg zakończony znakiem null. Plik nagłówkowy H. Na przykład ten parametr można określić stałą SE_SECURITY_NAME lub jej odpowiedni ciąg "SeSecurityPrivilege."

*pdwAttributes*<br/>
Wskaźnik do zmiennej, która odbiera atrybutów.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli atrybut jest pomyślnie pobrać, wartość false w przeciwnym razie.

##  <a name="operator_eq"></a>  CTokenPrivileges::operator =

Operator przypisania.

```
CTokenPrivileges& operator= (const TOKEN_PRIVILEGES& rPrivileges) throw(...);
CTokenPrivileges& operator= (const CTokenPrivileges& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*rPrivileges*<br/>
[TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges) struktury do przypisania do `CTokenPrivileges` obiektu.

*RHS*<br/>
`CTokenPrivileges` Obiekt można przypisać do obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CTokenPrivileges` obiektu.

##  <a name="operator_const_token_privileges__star"></a>  CTokenPrivileges::operator const TOKEN_PRIVILEGES \*

Rzutuje na wskaźnik do wartości `TOKEN_PRIVILEGES` struktury.

```
operator const TOKEN_PRIVILEGES *() const throw(...);
```

### <a name="remarks"></a>Uwagi

Rzutuje na wskaźnik do wartości [TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges) struktury.

## <a name="see-also"></a>Zobacz także

[Zabezpieczenia — przykład](../../overview/visual-cpp-samples.md)<br/>
[TOKEN_PRIVILEGES](/windows/desktop/api/winnt/ns-winnt-_token_privileges)<br/>
[LUID](/windows/desktop/api/winnt/ns-winnt-_luid)<br/>
[LUID_AND_ATTRIBUTES](/windows/desktop/api/winnt/ns-winnt-_luid_and_attributes)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Funkcje globalne zabezpieczeń](../../atl/reference/security-global-functions.md)
