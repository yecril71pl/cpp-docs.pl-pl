---
title: Klasa CTokenGroups | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CTokenGroups
- ATLSECURITY/ATL::CTokenGroups
- ATLSECURITY/ATL::CTokenGroups::CTokenGroups
- ATLSECURITY/ATL::CTokenGroups::Add
- ATLSECURITY/ATL::CTokenGroups::Delete
- ATLSECURITY/ATL::CTokenGroups::DeleteAll
- ATLSECURITY/ATL::CTokenGroups::GetCount
- ATLSECURITY/ATL::CTokenGroups::GetLength
- ATLSECURITY/ATL::CTokenGroups::GetPTOKEN_GROUPS
- ATLSECURITY/ATL::CTokenGroups::GetSidsAndAttributes
- ATLSECURITY/ATL::CTokenGroups::LookupSid
dev_langs:
- C++
helpviewer_keywords:
- CTokenGroups class
ms.assetid: 2ab08076-4b08-4487-bc70-ec6dee304190
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae36ce81d51c3fc66941bfd3c8755c4bcdcc98fe
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077210"
---
# <a name="ctokengroups-class"></a>Klasa CTokenGroups

Ta klasa jest otoką `TOKEN_GROUPS` struktury.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
class CTokenGroups
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTokenGroups::CTokenGroups](#ctokengroups)|Konstruktor.|
|[CTokenGroups:: ~ CTokenGroups](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTokenGroups::Add](#add)|Dodaje `CSid` lub istniejące `TOKEN_GROUPS` struktury do `CTokenGroups` obiektu.|
|[CTokenGroups::Delete](#delete)|Usuwa `CSid` i jego atrybuty skojarzone z `CTokenGroups` obiektu.|
|[CTokenGroups::DeleteAll](#deleteall)|Usuwa wszystkie `CSid` obiektów i ich atrybuty skojarzone z `CTokenGroups` obiektu.|
|[CTokenGroups::GetCount](#getcount)|Zwraca liczbę `CSid` obiektów i atrybuty skojarzone zawarte w `CTokenGroups` obiektu.|
|[CTokenGroups::GetLength](#getlength)|Zwraca rozmiar `CTokenGroups` obiektu.|
|[CTokenGroups::GetPTOKEN_GROUPS](#getptoken_groups)|Pobiera wskaźnik do `TOKEN_GROUPS` struktury.|
|[CTokenGroups::GetSidsAndAttributes](#getsidsandattributes)|Pobiera `CSid` obiektów i atrybuty należące do `CTokenGroups` obiektu.|
|[CTokenGroups::LookupSid](#lookupsid)|Pobiera atrybuty skojarzone z `CSid` obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTokenGroups::operator const TOKEN_GROUPS *](#operator_const_token_groups__star)|Rzutowania `CTokenGroups` obiektu na wskaźnik do `TOKEN_GROUPS` struktury.|
|[CTokenGroups::operator =](#operator_eq)|Operator przypisania.|

## <a name="remarks"></a>Uwagi

[Token dostępu](/windows/desktop/SecAuthZ/access-tokens) jest obiektem, w tym artykule opisano proces lub wątek kontekstu zabezpieczeń, która jest przydzielona do każdego użytkownika zalogowanego w systemie Windows.

`CTokenGroups` Klasy jest otoką [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups) struktury, zawierający informacje o grupie identyfikatory zabezpieczeń (SID) w wyniku token dostępu.

Wprowadzenie do modelu kontroli dostępu w Windows, zobacz [kontroli dostępu](/windows/desktop/SecAuthZ/access-control) w zestawie Windows SDK.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

##  <a name="add"></a>  CTokenGroups::Add

Dodaje `CSid` lub istniejące `TOKEN_GROUPS` struktury do `CTokenGroups` obiektu.

```
void Add(const CSid& rSid, DWORD dwAttributes) throw(... );
void Add(const TOKEN_GROUPS& rTokenGroups) throw(...);
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
A [CSid](../../atl/reference/csid-class.md) obiektu.

*dwAttributes*<br/>
Atrybuty do skojarzenia z `CSid` obiektu.

*rTokenGroups*<br/>
A [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups) struktury.

### <a name="remarks"></a>Uwagi

Te metody Dodaj jeden lub kilka `CSid` obiektów i ich skojarzone atrybutów do `CTokenGroups` obiektu.

##  <a name="ctokengroups"></a>  CTokenGroups::CTokenGroups

Konstruktor.

```
CTokenGroups() throw();
CTokenGroups(const CTokenGroups& rhs) throw(... );
CTokenGroups(const TOKEN_GROUPS& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*RHS*<br/>
`CTokenGroups` Obiektu lub [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups) struktury za pomocą którego do konstruowania `CTokenGroups` obiektu.

### <a name="remarks"></a>Uwagi

`CTokenGroups` Opcjonalnie można utworzyć obiekt przy użyciu `TOKEN_GROUPS` struktury lub uprzednio zdefiniowany `CTokenGroups` obiektu.

##  <a name="dtor"></a>  CTokenGroups:: ~ CTokenGroups

Destruktor.

```
virtual ~CTokenGroups() throw();
```

### <a name="remarks"></a>Uwagi

Destruktor zwalnia wszystkie przydzielone zasoby.

##  <a name="delete"></a>  CTokenGroups::Delete

Usuwa `CSid` i jego atrybuty skojarzone z `CTokenGroups` obiektu.

```
bool Delete(const CSid& rSid) throw();
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
[CSid](../../atl/reference/csid-class.md) obiektu, którego identyfikator zabezpieczeń (SID) i atrybuty powinny zostać usunięte.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli `CSid` zostanie usunięty, wartość false w przeciwnym razie.

##  <a name="deleteall"></a>  CTokenGroups::DeleteAll

Usuwa wszystkie `CSid` obiektów i ich atrybuty skojarzone z `CTokenGroups` obiektu.

```
void DeleteAll() throw();
```

##  <a name="getcount"></a>  CTokenGroups::GetCount

Zwraca liczbę `CSid` obiektów zawartych w `CTokenGroups`.

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę [CSid](../../atl/reference/csid-class.md) obiektów i ich skojarzonych z nimi atrybutów znajdujących się w `CTokenGroups` obiektu.

##  <a name="getlength"></a>  CTokenGroups::GetLength

Zwraca rozmiar `CTokenGroup` obiektu.

```
UINT GetLength() const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca całkowity rozmiar `CTokenGroup` obiektu, w bajtach.

##  <a name="getptoken_groups"></a>  CTokenGroups::GetPTOKEN_GROUPS

Pobiera wskaźnik do `TOKEN_GROUPS` struktury.

```
const TOKEN_GROUPS* GetPTOKEN_GROUPS() const throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Pobiera wskaźnik do [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups) należących do struktury `CTokenGroups` obiektu tokenu dostępu.

##  <a name="getsidsandattributes"></a>  CTokenGroups::GetSidsAndAttributes

Pobiera `CSid` obiektów i (opcjonalnie) atrybuty należące do `CTokenGroups` obiektu.

```
void GetSidsAndAttributes(
    CSid::CSidArray* pSids,
    CAtlArray<DWORD>* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSids*<br/>
Wskaźnik do tablicy [CSid](../../atl/reference/csid-class.md) obiektów.

*pAttributes*<br/>
Wskaźnik do tablicy słów podwójnych. Jeśli ten parametr jest pominięty lub ma wartość NULL, atrybuty nie są pobierane.

### <a name="remarks"></a>Uwagi

Ta metoda powoduje wyliczenie wszystkich `CSid` obiektów zawartych w `CTokenGroups` obiektu i umieść je i (opcjonalnie flagi atrybutów) do obiektów w tablicy.

##  <a name="lookupsid"></a>  CTokenGroups::LookupSid

Pobiera atrybuty skojarzone z `CSid` obiektu.

```
bool LookupSid(
    const CSid& rSid,
    DWORD* pdwAttributes = NULL) const throw();
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
[CSid](../../atl/reference/csid-class.md) obiektu.

*pdwAttributes*<br/>
Wskaźnik do typu DWORD, która będzie akceptować `CSid` atrybutu obiektu. Jeśli pominięty lub wartość NULL, nie można pobrać atrybutu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli `CSid` zostanie znaleziony, wartość false w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Ustawienie *pdwAttributes* do wartości NULL stanowi sposób potwierdzające istnienie `CSid` bez uzyskiwania dostępu do atrybutu. Należy pamiętać, że ta metoda nie należy sprawdzić prawa dostępu. Aplikacje w zamian użyć [CAccessToken::CheckTokenMembership](../../atl/reference/caccesstoken-class.md#checktokenmembership) metody.

##  <a name="operator_eq"></a>  CTokenGroups::operator =

Operator przypisania.

```
CTokenGroups& operator= (const TOKEN_GROUPS& rhs) throw(...);
CTokenGroups& operator= (const CTokenGroups& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*RHS*<br/>
`CTokenGroups` Obiektu lub [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups) struktury do przypisania do `CTokenGroups` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CTokenGroups` obiektu.

##  <a name="operator_const_token_groups__star"></a>  CTokenGroups::operator const TOKEN_GROUPS *

Rzutuje na wskaźnik do wartości `TOKEN_GROUPS` struktury.

```
operator const TOKEN_GROUPS *() const throw(...);
```

### <a name="remarks"></a>Uwagi

Rzutuje na wskaźnik do wartości [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-_token_groups) struktury.

## <a name="see-also"></a>Zobacz też

[Zabezpieczenia — przykład](../../visual-cpp-samples.md)<br/>
[Klasa CSid](../../atl/reference/csid-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Funkcje globalne zabezpieczeń](../../atl/reference/security-global-functions.md)
