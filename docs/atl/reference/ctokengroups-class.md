---
title: Klasa CTokenGroups
ms.date: 11/04/2016
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
helpviewer_keywords:
- CTokenGroups class
ms.assetid: 2ab08076-4b08-4487-bc70-ec6dee304190
ms.openlocfilehash: 4e5d06ca01201bf415afedbe6f6e5bca096f68fa
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915580"
---
# <a name="ctokengroups-class"></a>Klasa CTokenGroups

Ta klasa jest otoką dla `TOKEN_GROUPS` struktury.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

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
|[CTokenGroups:: Add](#add)|Dodaje lub istniejącą `TOKEN_GROUPS` strukturę do `CTokenGroups` obiektu. `CSid`|
|[CTokenGroups::D Usuń](#delete)|`CSid` Usuwa zobiektui`CTokenGroups` skojarzone z nim atrybuty.|
|[CTokenGroups::DeleteAll](#deleteall)|Usuwa wszystkie `CSid` obiekty i skojarzone `CTokenGroups` z nimi atrybuty z obiektu.|
|[CTokenGroups:: GetCount](#getcount)|Zwraca liczbę `CSid` obiektów i skojarzonych `CTokenGroups` z nimi atrybutów zawartych w obiekcie.|
|[CTokenGroups::GetLength](#getlength)|Zwraca rozmiar `CTokenGroups` obiektu.|
|[CTokenGroups::GetPTOKEN_GROUPS](#getptoken_groups)|Pobiera wskaźnik do `TOKEN_GROUPS` struktury.|
|[CTokenGroups::GetSidsAndAttributes](#getsidsandattributes)|Pobiera obiekty i atrybuty należące `CTokenGroups` do obiektu. `CSid`|
|[CTokenGroups::LookupSid](#lookupsid)|Pobiera atrybuty skojarzone z `CSid` obiektem.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTokenGroups:: operator const TOKEN_GROUPS *](#operator_const_token_groups__star)|Rzutuje `TOKEN_GROUPS` obiekt na wskaźnik do struktury. `CTokenGroups`|
|[CTokenGroups:: operator =](#operator_eq)|Operator przypisania.|

## <a name="remarks"></a>Uwagi

[Token dostępu](/windows/desktop/SecAuthZ/access-tokens) jest obiektem opisującym kontekst zabezpieczeń procesu lub wątku i jest przypisywany do każdego użytkownika zalogowanego w systemie Windows.

Klasa to otoka struktury TOKEN_GROUPS, zawierająca informacje o identyfikatorach zabezpieczeń grupy (SID) w tokenie dostępu. [](/windows/desktop/api/winnt/ns-winnt-token_groups) `CTokenGroups`

Aby zapoznać się z wprowadzeniem do modelu kontroli dostępu w systemie Windows, zobacz [Access Control](/windows/desktop/SecAuthZ/access-control) w Windows SDK.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity. h

##  <a name="add"></a>CTokenGroups:: Add

Dodaje lub istniejącą `TOKEN_GROUPS` strukturę do `CTokenGroups` obiektu. `CSid`

```
void Add(const CSid& rSid, DWORD dwAttributes) throw(... );
void Add(const TOKEN_GROUPS& rTokenGroups) throw(...);
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
Obiekt [CSid](../../atl/reference/csid-class.md) .

*dwAttributes*<br/>
Atrybuty, które mają zostać skojarzone `CSid` z obiektem.

*rTokenGroups*<br/>
Struktura [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-token_groups) .

### <a name="remarks"></a>Uwagi

Te metody dodają jeden lub `CSid` więcej obiektów i skojarzonych `CTokenGroups` z nimi atrybutów do obiektu.

##  <a name="ctokengroups"></a>CTokenGroups::CTokenGroups

Konstruktor.

```
CTokenGroups() throw();
CTokenGroups(const CTokenGroups& rhs) throw(... );
CTokenGroups(const TOKEN_GROUPS& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*RHS*<br/>
Struktura obiektu lub [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-token_groups) , z `CTokenGroups` którym ma zostać skonstruowany obiekt. `CTokenGroups`

### <a name="remarks"></a>Uwagi

Obiekt można opcjonalnie utworzyć `TOKEN_GROUPS` przy użyciu struktury lub wcześniej zdefiniowanego `CTokenGroups` obiektu. `CTokenGroups`

##  <a name="dtor"></a>CTokenGroups:: ~ CTokenGroups

Destruktor.

```
virtual ~CTokenGroups() throw();
```

### <a name="remarks"></a>Uwagi

Destruktor zwalnia wszystkie przydzieloną zasoby.

##  <a name="delete"></a>CTokenGroups::D Usuń

`CSid` Usuwa zobiektui`CTokenGroups` skojarzone z nim atrybuty.

```
bool Delete(const CSid& rSid) throw();
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
Obiekt [CSid](../../atl/reference/csid-class.md) , dla którego należy usunąć identyfikator zabezpieczeń (SID) i atrybuty.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, `CSid` jeśli jest usuwany, w przeciwnym razie false.

##  <a name="deleteall"></a>  CTokenGroups::DeleteAll

Usuwa wszystkie `CSid` obiekty i skojarzone `CTokenGroups` z nimi atrybuty z obiektu.

```
void DeleteAll() throw();
```

##  <a name="getcount"></a>CTokenGroups:: GetCount

Zwraca liczbę `CSid` obiektów zawartych w `CTokenGroups`elemencie.

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę obiektów [CSid](../../atl/reference/csid-class.md) i skojarzonych z nimi atrybutów zawartych w `CTokenGroups` obiekcie.

##  <a name="getlength"></a>CTokenGroups:: GetLength

Zwraca rozmiar `CTokenGroup` obiektu.

```
UINT GetLength() const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca łączny rozmiar `CTokenGroup` obiektu w bajtach.

##  <a name="getptoken_groups"></a>CTokenGroups::GetPTOKEN_GROUPS

Pobiera wskaźnik do `TOKEN_GROUPS` struktury.

```
const TOKEN_GROUPS* GetPTOKEN_GROUPS() const throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Pobiera wskaźnik do struktury [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-token_groups) należącej do `CTokenGroups` obiektu tokenu dostępu.

##  <a name="getsidsandattributes"></a>CTokenGroups::GetSidsAndAttributes

Pobiera obiekty i (opcjonalnie) atrybuty należące `CTokenGroups` do obiektu. `CSid`

```
void GetSidsAndAttributes(
    CSid::CSidArray* pSids,
    CAtlArray<DWORD>* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSids*<br/>
Wskaźnik do tablicy obiektów [CSid](../../atl/reference/csid-class.md) .

*pAttributes*<br/>
Wskaźnik na tablicę wartości typu DWORD. Jeśli ten parametr zostanie pominięty lub ma wartość NULL, atrybuty nie zostaną pobrane.

### <a name="remarks"></a>Uwagi

Ta metoda spowoduje Wyliczenie wszystkich `CSid` obiektów zawartych `CTokenGroups` w obiekcie i umieszczenie ich oraz (opcjonalnie) flag atrybutów w obiektach Array.

##  <a name="lookupsid"></a>CTokenGroups::LookupSid

Pobiera atrybuty skojarzone z `CSid` obiektem.

```
bool LookupSid(
    const CSid& rSid,
    DWORD* pdwAttributes = NULL) const throw();
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
Obiekt [CSid](../../atl/reference/csid-class.md) .

*pdwAttributes*<br/>
Wskaźnik na wartość typu DWORD, która będzie `CSid` akceptować atrybut obiektu. W przypadku pominięcia lub wartości NULL atrybut nie zostanie pobrany.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, `CSid` jeśli znaleziono, w przeciwnym razie false.

### <a name="remarks"></a>Uwagi

Ustawienie *pdwAttributes* na null umożliwia potwierdzenie istnienia `CSid` bez uzyskiwania dostępu do atrybutu. Należy zauważyć, że tej metody nie należy używać do sprawdzania praw dostępu. Aplikacje powinny zamiast tego używać metody [CAccessToken:: CheckTokenMembership](../../atl/reference/caccesstoken-class.md#checktokenmembership) .

##  <a name="operator_eq"></a>CTokenGroups:: operator =

Operator przypisania.

```
CTokenGroups& operator= (const TOKEN_GROUPS& rhs) throw(...);
CTokenGroups& operator= (const CTokenGroups& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*RHS*<br/>
Obiekt lub struktura [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-token_groups) `CTokenGroups` do przypisania do obiektu. `CTokenGroups`

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CTokenGroups` obiekt.

##  <a name="operator_const_token_groups__star"></a>CTokenGroups:: operator const TOKEN_GROUPS *

Rzutuje wartość na wskaźnik do `TOKEN_GROUPS` struktury.

```
operator const TOKEN_GROUPS *() const throw(...);
```

### <a name="remarks"></a>Uwagi

Rzutuje wartość na wskaźnik do struktury [TOKEN_GROUPS](/windows/desktop/api/winnt/ns-winnt-token_groups) .

## <a name="see-also"></a>Zobacz także

[Przykład zabezpieczeń](../../overview/visual-cpp-samples.md)<br/>
[Klasa CSid](../../atl/reference/csid-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Funkcje globalne zabezpieczeń](../../atl/reference/security-global-functions.md)
