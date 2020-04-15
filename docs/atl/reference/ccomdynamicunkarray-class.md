---
title: Klasa CComDynamicUnkArray
ms.date: 11/04/2016
f1_keywords:
- CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::Add
- ATLCOM/ATL::CComDynamicUnkArray::begin
- ATLCOM/ATL::CComDynamicUnkArray::clear
- ATLCOM/ATL::CComDynamicUnkArray::end
- ATLCOM/ATL::CComDynamicUnkArray::GetAt
- ATLCOM/ATL::CComDynamicUnkArray::GetCookie
- ATLCOM/ATL::CComDynamicUnkArray::GetSize
- ATLCOM/ATL::CComDynamicUnkArray::GetUnknown
- ATLCOM/ATL::CComDynamicUnkArray::Remove
helpviewer_keywords:
- connection points [C++], managing
- CComDynamicUnkArray class
ms.assetid: 202470d7-9a1b-498f-b96d-659d681acd65
ms.openlocfilehash: 57383823897a434f649c6c4af78e71fe6ff66a6a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327900"
---
# <a name="ccomdynamicunkarray-class"></a>Klasa CComDynamicUnkArray

Ta klasa przechowuje `IUnknown` tablicę wskaźników.

## <a name="syntax"></a>Składnia

```
class CComDynamicUnkArray
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComDynamicUnkArray::CComDynamicUnkArray](#ccomdynamicunkarray)|Konstruktor. Inicjuje wartości kolekcji do wartości NULL i rozmiar kolekcji do zera.|
|[CComDynamicUnkArray::~CComDynamicUnkArray](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComDynamicUnkArray::Dodaj](#add)|Wywołanie tej metody, aby dodać `IUnknown` wskaźnik do tablicy.|
|[CComDynamicUnkArray::begin](#begin)|Zwraca wskaźnik do `IUnknown` pierwszego wskaźnika w kolekcji.|
|[CComDynamicUnkArray::jasne](#clear)|Opróżnia tablicę.|
|[CComDynamicUnkArray::end](#end)|Zwraca wskaźnik do jednego `IUnknown` przeszłości ostatni wskaźnik w kolekcji.|
|[CComDynamicUnkArray::GetAt](#getat)|Pobiera element w określonym indeksie.|
|[CComDynamicUnkArray::GetCookie](#getcookie)|Wywołanie tej metody, aby uzyskać `IUnknown` plik cookie skojarzony z danym wskaźnikiem.|
|[CComDynamicUnkArray::GetSize](#getsize)|Zwraca długość tablicy.|
|[CComDynamicUnkArray::GetUnknown](#getunknown)|Wywołanie tej metody, `IUnknown` aby uzyskać wskaźnik skojarzony z danym plikiem cookie.|
|[CComDynamicUnkArray::Usuń](#remove)|Wywołanie tej metody, aby usunąć `IUnknown` wskaźnik z tablicy.|

## <a name="remarks"></a>Uwagi

`CComDynamicUnkArray`zawiera dynamicznie przydzieloną `IUnknown` tablicę wskaźników, z których każdy jest interfejsem w punkcie połączenia. `CComDynamicUnkArray`może służyć jako parametr do [iConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) klasy szablonu.

Metody `CComDynamicUnkArray` [rozpoczęcia](#begin) i [zakończenia](#end) mogą służyć do pętli przez wszystkie punkty połączenia (na przykład, gdy zdarzenie jest uruchamiane).

Zobacz [Dodawanie punktów połączenia do obiektu, aby](../../atl/adding-connection-points-to-an-object.md) uzyskać szczegółowe informacje na temat automatyzacji tworzenia serwerów proxy punktu połączenia.

> [!NOTE]
> **Uwaga** Klasa `CComDynamicUnkArray` jest używana przez **Kreatora Dodaj klasę** podczas tworzenia formantu, który ma punkty połączenia. Jeśli chcesz ręcznie określić liczbę punktów połączenia, zmień `CComDynamicUnkArray` `CComUnkArray<` odwołanie z *n* `>`, gdzie *n* jest wymaganą liczbą punktów połączenia.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="ccomdynamicunkarrayadd"></a><a name="add"></a>CComDynamicUnkArray::Dodaj

Wywołanie tej metody, aby dodać `IUnknown` wskaźnik do tablicy.

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>Parametry

*Punk*<br/>
Wskaźnik, `IUnknown` aby dodać do tablicy.

### <a name="return-value"></a>Wartość zwracana

Zwraca plik cookie skojarzony z nowo dodanym wskaźnikiem.

## <a name="ccomdynamicunkarraybegin"></a><a name="begin"></a>CComDynamicUnkArray::begin

Zwraca wskaźnik na początku kolekcji `IUnknown` wskaźników interfejsu.

```
IUnknown**
    begin();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `IUnknown` wskaźnika interfejsu.

### <a name="remarks"></a>Uwagi

Kolekcja zawiera wskaźniki do interfejsów przechowywanych lokalnie jako `IUnknown`. Rzutujesz `IUnknown` każdy interfejs do rzeczywistego typu interfejsu, a następnie wywołać za jego pośrednictwem. Nie trzeba najpierw wykonywać zapytań o interfejs.

Przed użyciem `IUnknown` interfejsu należy sprawdzić, czy nie jest null.

## <a name="ccomdynamicunkarrayclear"></a><a name="clear"></a>CComDynamicUnkArray::jasne

Opróżnia tablicę.

```
void clear();
```

## <a name="ccomdynamicunkarrayccomdynamicunkarray"></a><a name="ccomdynamicunkarray"></a>CComDynamicUnkArray::CComDynamicUnkArray

Konstruktor.

```
CComDynamicUnkArray();
```

### <a name="remarks"></a>Uwagi

Ustawia rozmiar kolekcji na zero i inicjuje wartości na WARTOŚĆ NULL. Destruktor zwalnia kolekcji, jeśli to konieczne.

## <a name="ccomdynamicunkarrayccomdynamicunkarray"></a><a name="dtor"></a>CComDynamicUnkArray::~CComDynamicUnkArray

Destruktor.

```
~CComDynamicUnkArray();
```

### <a name="remarks"></a>Uwagi

Zwalnia zasoby przydzielone przez konstruktora klasy.

## <a name="ccomdynamicunkarrayend"></a><a name="end"></a>CComDynamicUnkArray::end

Zwraca wskaźnik do jednego `IUnknown` przeszłości ostatni wskaźnik w kolekcji.

```
IUnknown**
    end();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `IUnknown` wskaźnika interfejsu.

## <a name="ccomdynamicunkarraygetat"></a><a name="getat"></a>CComDynamicUnkArray::GetAt

Pobiera element w określonym indeksie.

```
IUnknown* GetAt(int nIndex);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks elementu do pobrania.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu [IUnknown.](/windows/win32/api/unknwn/nn-unknwn-iunknown)

## <a name="ccomdynamicunkarraygetcookie"></a><a name="getcookie"></a>CComDynamicUnkArray::GetCookie

Wywołanie tej metody, aby uzyskać `IUnknown` plik cookie skojarzony z danym wskaźnikiem.

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>Parametry

*ppFind (dojrzenie)*<br/>
Wskaźnik, `IUnknown` dla którego wymagany jest skojarzony plik cookie.

### <a name="return-value"></a>Wartość zwracana

Zwraca plik cookie skojarzony ze wskaźnikiem `IUnknown` `IUnknown` lub zero, jeśli nie znaleziono pasującego wskaźnika.

### <a name="remarks"></a>Uwagi

Jeśli istnieje więcej niż jedno `IUnknown` wystąpienie tego samego wskaźnika, ta funkcja zwraca plik cookie dla pierwszego.

## <a name="ccomdynamicunkarraygetsize"></a><a name="getsize"></a>CComDynamicUnkArray::GetSize

Zwraca długość tablicy.

```
int GetSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Długość tablicy.

## <a name="ccomdynamicunkarraygetunknown"></a><a name="getunknown"></a>CComDynamicUnkArray::GetUnknown

Wywołanie tej metody, `IUnknown` aby uzyskać wskaźnik skojarzony z danym plikiem cookie.

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>Parametry

*dwCookie (właśc.*<br/>
Plik cookie, dla `IUnknown` którego wymagany jest skojarzony wskaźnik.

### <a name="return-value"></a>Wartość zwracana

Zwraca `IUnknown` wskaźnik lub null, jeśli nie znaleziono pasującego pliku cookie.

## <a name="ccomdynamicunkarrayremove"></a><a name="remove"></a>CComDynamicUnkArray::Usuń

Wywołanie tej metody, aby usunąć `IUnknown` wskaźnik z tablicy.

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>Parametry

*dwCookie (właśc.*<br/>
Plik cookie odwołujący się do wskaźnika, `IUnknown` który ma zostać usunięty z tablicy.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli wskaźnik zostanie usunięty; w przeciwnym razie FALSE.

## <a name="see-also"></a>Zobacz też

[Klasa CComUnkArray](../../atl/reference/ccomunkarray-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
