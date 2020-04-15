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
ms.openlocfilehash: 1e9d21c59eb5efabf036fbc938a40de2c4b7a0b7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330548"
---
# <a name="ctokengroups-class"></a>Klasa CTokenGroups

Ta klasa jest otoką `TOKEN_GROUPS` dla struktury.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class CTokenGroups
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTokenGroups::CTokenGroups](#ctokengroups)|Konstruktor.|
|[CTokenGroups::~CTokenGroups](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTokenGroups::Dodaj](#add)|Dodaje `CSid` lub `TOKEN_GROUPS` istniejącą `CTokenGroups` strukturę do obiektu.|
|[CTokenGroups::Delete](#delete)|Usuwa `CSid` a i jego skojarzone `CTokenGroups` atrybuty z obiektu.|
|[CTokenGroups::DeleteAll](#deleteall)|Usuwa wszystkie `CSid` obiekty i skojarzone `CTokenGroups` z nimi atrybuty z obiektu.|
|[CTokenGroups::GetCount](#getcount)|Zwraca liczbę `CSid` obiektów i skojarzonych atrybutów `CTokenGroups` zawartych w obiekcie.|
|[CTokenGroups::GetLength](#getlength)|Zwraca rozmiar `CTokenGroups` obiektu.|
|[CTokenGroups::GetPTOKEN_GROUPS](#getptoken_groups)|Pobiera wskaźnik do `TOKEN_GROUPS` struktury.|
|[CTokenGroups::GetSidsAndAttributes](#getsidsandattributes)|Pobiera `CSid` obiekty i atrybuty `CTokenGroups` należące do obiektu.|
|[CTokenGroups::OdnośniKSydowy](#lookupsid)|Pobiera atrybuty skojarzone `CSid` z obiektem.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTokenGroups::operator const TOKEN_GROUPS *](#operator_const_token_groups__star)|Rzutuje `CTokenGroups` obiekt na wskaźnik `TOKEN_GROUPS` do struktury.|
|[CTokenGroups::operator =](#operator_eq)|Operator przypisania.|

## <a name="remarks"></a>Uwagi

[Token dostępu](/windows/win32/SecAuthZ/access-tokens) jest obiektem opisującym kontekst zabezpieczeń procesu lub wątku i przydzielanym każdemu użytkownikowi zalogowanym do systemu Windows.

Klasa `CTokenGroups` jest otoką dla struktury [TOKEN_GROUPS,](/windows/win32/api/winnt/ns-winnt-token_groups) zawierającą informacje o identyfikatorach zabezpieczeń grupy (IDENTYFIKATORY SID) w tokenie dostępu.

Aby zapoznać się z wprowadzeniem do modelu kontroli dostępu w systemie Windows, zobacz [Kontrola dostępu](/windows/win32/SecAuthZ/access-control) w zestaw Windows SDK.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

## <a name="ctokengroupsadd"></a><a name="add"></a>CTokenGroups::Dodaj

Dodaje `CSid` lub `TOKEN_GROUPS` istniejącą `CTokenGroups` strukturę do obiektu.

```
void Add(const CSid& rSid, DWORD dwAttributes) throw(... );
void Add(const TOKEN_GROUPS& rTokenGroups) throw(...);
```

### <a name="parameters"></a>Parametry

*rSid (wyd.*<br/>
Obiekt [CSid.](../../atl/reference/csid-class.md)

*dwAttributes (przyw.*<br/>
Atrybuty do skojarzenia z obiektem. `CSid`

*grupy rToken*<br/>
Struktura [TOKEN_GROUPS.](/windows/win32/api/winnt/ns-winnt-token_groups)

### <a name="remarks"></a>Uwagi

Metody te dodają `CSid` jeden lub więcej obiektów `CTokenGroups` i ich skojarzone atrybuty do obiektu.

## <a name="ctokengroupsctokengroups"></a><a name="ctokengroups"></a>CTokenGroups::CTokenGroups

Konstruktor.

```
CTokenGroups() throw();
CTokenGroups(const CTokenGroups& rhs) throw(... );
CTokenGroups(const TOKEN_GROUPS& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*Rhs*<br/>
Obiekt `CTokenGroups` lub [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) strukturę, za pomocą `CTokenGroups` której ma być konstruowanie obiektu.

### <a name="remarks"></a>Uwagi

Obiekt `CTokenGroups` można opcjonalnie utworzyć `TOKEN_GROUPS` przy użyciu struktury `CTokenGroups` lub uprzednio zdefiniowanego obiektu.

## <a name="ctokengroupsctokengroups"></a><a name="dtor"></a>CTokenGroups::~CTokenGroups

Destruktor.

```
virtual ~CTokenGroups() throw();
```

### <a name="remarks"></a>Uwagi

Destruktor zwalnia wszystkie przydzielone zasoby.

## <a name="ctokengroupsdelete"></a><a name="delete"></a>CTokenGroups::Delete

Usuwa `CSid` a i jego skojarzone `CTokenGroups` atrybuty z obiektu.

```
bool Delete(const CSid& rSid) throw();
```

### <a name="parameters"></a>Parametry

*rSid (wyd.*<br/>
[Obiekt CSid,](../../atl/reference/csid-class.md) dla którego należy usunąć identyfikator zabezpieczeń (SID) i atrybuty.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość `CSid` true, jeśli jest usuwany, false inaczej.

## <a name="ctokengroupsdeleteall"></a><a name="deleteall"></a>CTokenGroups::DeleteAll

Usuwa wszystkie `CSid` obiekty i skojarzone `CTokenGroups` z nimi atrybuty z obiektu.

```
void DeleteAll() throw();
```

## <a name="ctokengroupsgetcount"></a><a name="getcount"></a>CTokenGroups::GetCount

Zwraca liczbę `CSid` obiektów zawartych `CTokenGroups`w pliku .

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę obiektów [CSid](../../atl/reference/csid-class.md) i skojarzone z `CTokenGroups` nimi atrybuty zawarte w obiekcie.

## <a name="ctokengroupsgetlength"></a><a name="getlength"></a>CTokenGroups::GetLength

Zwraca rozmiar `CTokenGroup` obiektu.

```
UINT GetLength() const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca całkowity rozmiar `CTokenGroup` obiektu w bajtach.

## <a name="ctokengroupsgetptoken_groups"></a><a name="getptoken_groups"></a>CTokenGroups::GetPTOKEN_GROUPS

Pobiera wskaźnik do `TOKEN_GROUPS` struktury.

```
const TOKEN_GROUPS* GetPTOKEN_GROUPS() const throw(...);
```

### <a name="return-value"></a>Wartość zwracana

Pobiera wskaźnik do [struktury TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) należącej do `CTokenGroups` obiektu tokenu dostępu.

## <a name="ctokengroupsgetsidsandattributes"></a><a name="getsidsandattributes"></a>CTokenGroups::GetSidsAndAttributes

Pobiera `CSid` obiekty i (opcjonalnie) atrybuty `CTokenGroups` należące do obiektu.

```
void GetSidsAndAttributes(
    CSid::CSidArray* pSids,
    CAtlArray<DWORD>* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*PSydy*<br/>
Wskaźnik do tablicy obiektów [CSid.](../../atl/reference/csid-class.md)

*pAttributes (właso)*<br/>
Wskaźnik do tablicy DWORDs. Jeśli ten parametr zostanie pominięty lub NULL, atrybuty nie są pobierane.

### <a name="remarks"></a>Uwagi

Ta metoda wyliczy wszystkie `CSid` obiekty zawarte `CTokenGroups` w obiekcie i umieścić je i (opcjonalnie) flagi atrybutu do obiektów tablicy.

## <a name="ctokengroupslookupsid"></a><a name="lookupsid"></a>CTokenGroups::OdnośniKSydowy

Pobiera atrybuty skojarzone `CSid` z obiektem.

```
bool LookupSid(
    const CSid& rSid,
    DWORD* pdwAttributes = NULL) const throw();
```

### <a name="parameters"></a>Parametry

*rSid (wyd.*<br/>
Obiekt [CSid.](../../atl/reference/csid-class.md)

*pdwPrzyszłanie*<br/>
Wskaźnik do DWORD, który `CSid` zaakceptuje atrybut obiektu. Jeśli pominięto lub NULL, atrybut nie zostanie pobrany.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość `CSid` true, jeśli zostanie znaleziony, false inaczej.

### <a name="remarks"></a>Uwagi

Ustawienie *pdwAttributes* do NULL umożliwia potwierdzenie istnienia `CSid` bez dostępu do atrybutu. Należy zauważyć, że ta metoda nie powinna służyć do sprawdzania praw dostępu. Aplikacje powinny zamiast tego używać [CAccessToken::CheckTokenMembership](../../atl/reference/caccesstoken-class.md#checktokenmembership) metody.

## <a name="ctokengroupsoperator-"></a><a name="operator_eq"></a>CTokenGroups::operator =

Operator przypisania.

```
CTokenGroups& operator= (const TOKEN_GROUPS& rhs) throw(...);
CTokenGroups& operator= (const CTokenGroups& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*Rhs*<br/>
Obiekt `CTokenGroups` lub [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) strukturę do przypisania do `CTokenGroups` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CTokenGroups` obiekt.

## <a name="ctokengroupsoperator-const-token_groups-"></a><a name="operator_const_token_groups__star"></a>CTokenGroups::operator const TOKEN_GROUPS *

Rzutuje wartość do wskaźnika `TOKEN_GROUPS` do struktury.

```
operator const TOKEN_GROUPS *() const throw(...);
```

### <a name="remarks"></a>Uwagi

Rzutuje wartość do wskaźnika do [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) struktury.

## <a name="see-also"></a>Zobacz też

[Przykład zabezpieczeń](../../overview/visual-cpp-samples.md)<br/>
[Klasa CSid](../../atl/reference/csid-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Globalne funkcje zabezpieczeń](../../atl/reference/security-global-functions.md)
