---
title: Klasa CComUnkArray
ms.date: 11/04/2016
f1_keywords:
- CComUnkArray
- ATLCOM/ATL::CComUnkArray
- ATLCOM/ATL::CComUnkArray::CComUnkArray
- ATLCOM/ATL::CComUnkArray::Add
- ATLCOM/ATL::CComUnkArray::begin
- ATLCOM/ATL::CComUnkArray::end
- ATLCOM/ATL::CComUnkArray::GetCookie
- ATLCOM/ATL::CComUnkArray::GetUnknown
- ATLCOM/ATL::CComUnkArray::Remove
helpviewer_keywords:
- connection points [C++], managing
- CComUnkArray class
ms.assetid: 5fd4b378-a7b5-4cc1-8866-8ab72a73639e
ms.openlocfilehash: c1d2f0296394d3979ef4f152e3f902c89adf5b45
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327303"
---
# <a name="ccomunkarray-class"></a>Klasa CComUnkArray

Ta klasa `IUnknown` przechowuje wskaźniki i jest przeznaczony do użycia jako parametr do [iConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) klasy szablonu.

## <a name="syntax"></a>Składnia

```
template<unsigned int nMaxSize>
class CComUnkArray
```

#### <a name="parameters"></a>Parametry

*rozmiar nMaxSize*<br/>
Maksymalna liczba `IUnknown` wskaźników, które mogą być przechowywane w tablicy statycznej.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComUnkArray::CComUnkArray](#ccomunkarray)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComUnkArray::Dodaj](#add)|Wywołanie tej metody, aby dodać `IUnknown` wskaźnik do tablicy.|
|[CComUnkArray::begin](#begin)|Zwraca wskaźnik do `IUnknown` pierwszego wskaźnika w kolekcji.|
|[CComUnkArray::end](#end)|Zwraca wskaźnik do jednego `IUnknown` przeszłości ostatni wskaźnik w kolekcji.|
|[CComUnkArray::GetCookie](#getcookie)|Wywołanie tej metody, aby uzyskać `IUnknown` plik cookie skojarzony z danym wskaźnikiem.|
|[CComUnkArray::GetUnknown](#getunknown)|Wywołanie tej metody, `IUnknown` aby uzyskać wskaźnik skojarzony z danym plikiem cookie.|
|[CComUnkArray::Usuń](#remove)|Wywołanie tej metody, aby usunąć `IUnknown` wskaźnik z tablicy.|

## <a name="remarks"></a>Uwagi

`CComUnkArray`posiada stałą `IUnknown` liczbę wskaźników, z których każdy jest interfejsem w punkcie połączenia. `CComUnkArray`może służyć jako parametr do [iConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) klasy szablonu. `CComUnkArray<1>`jest szablonem `CComUnkArray` specjalizacji, który został zoptymalizowany dla jednego punktu połączenia.

Metody `CComUnkArray` [rozpoczęcia](#begin) i [zakończenia](#end) mogą służyć do pętli przez wszystkie punkty połączenia (na przykład, gdy zdarzenie jest uruchamiane).

Zobacz [Dodawanie punktów połączenia do obiektu, aby](../../atl/adding-connection-points-to-an-object.md) uzyskać szczegółowe informacje na temat automatyzacji tworzenia serwerów proxy punktu połączenia.

> [!NOTE]
> **Uwaga** Klasa [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md) jest używana przez **Kreatora Dodaj klasę** podczas tworzenia formantu, który ma punkty połączenia. Jeśli chcesz ręcznie określić liczbę punktów połączenia, zmień `CComDynamicUnkArray` `CComUnkArray<` odwołanie z *n* `>`, gdzie *n* jest wymaganą liczbą punktów połączenia.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="ccomunkarrayadd"></a><a name="add"></a>CComUnkArray::Dodaj

Wywołanie tej metody, aby dodać `IUnknown` wskaźnik do tablicy.

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>Parametry

*Punk*<br/>
Wywołanie tej metody, aby dodać `IUnknown` wskaźnik do tablicy.

### <a name="return-value"></a>Wartość zwracana

Zwraca plik cookie skojarzony z nowo dodanym wskaźnikiem lub 0, jeśli tablica nie jest wystarczająco duża, aby zawierać nowy wskaźnik.

## <a name="ccomunkarraybegin"></a><a name="begin"></a>CComUnkArray::begin

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

## <a name="ccomunkarrayccomunkarray"></a><a name="ccomunkarray"></a>CComUnkArray::CComUnkArray

Konstruktor.

```
CComUnkArray();
```

### <a name="remarks"></a>Uwagi

Ustawia kolekcję `nMaxSize` `IUnknown` do przechowywania wskaźników i inicjuje wskaźniki do wartości NULL.

## <a name="ccomunkarrayend"></a><a name="end"></a>CComUnkArray::end

Zwraca wskaźnik do jednego `IUnknown` przeszłości ostatni wskaźnik w kolekcji.

```
IUnknown**
    end();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `IUnknown` wskaźnika interfejsu.

### <a name="remarks"></a>Uwagi

Metody `CComUnkArray` `begin` i `end` może służyć do pętli przez wszystkie punkty połączenia, na przykład, gdy zdarzenie jest uruchamiany.

[!code-cpp[NVC_ATL_COM#44](../../atl/codesnippet/cpp/ccomunkarray-class_1.cpp)]

## <a name="ccomunkarraygetcookie"></a><a name="getcookie"></a>CComUnkArray::GetCookie

Wywołanie tej metody, aby uzyskać `IUnknown` plik cookie skojarzony z danym wskaźnikiem.

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>Parametry

*ppFind (dojrzenie)*<br/>
Wskaźnik, `IUnknown` dla którego wymagany jest skojarzony plik cookie.

### <a name="return-value"></a>Wartość zwracana

Zwraca plik cookie skojarzony ze wskaźnikiem `IUnknown` lub `IUnknown` 0, jeśli nie znaleziono pasującego wskaźnika.

### <a name="remarks"></a>Uwagi

Jeśli istnieje więcej niż jedno `IUnknown` wystąpienie tego samego wskaźnika, ta funkcja zwraca plik cookie dla pierwszego.

## <a name="ccomunkarraygetunknown"></a><a name="getunknown"></a>CComUnkArray::GetUnknown

Wywołanie tej metody, `IUnknown` aby uzyskać wskaźnik skojarzony z danym plikiem cookie.

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>Parametry

*dwCookie (właśc.*<br/>
Plik cookie, dla `IUnknown` którego wymagany jest skojarzony wskaźnik.

### <a name="return-value"></a>Wartość zwracana

Zwraca `IUnknown` wskaźnik lub null, jeśli nie znaleziono pasującego pliku cookie.

## <a name="ccomunkarrayremove"></a><a name="remove"></a>CComUnkArray::Usuń

Wywołanie tej metody, aby usunąć `IUnknown` wskaźnik z tablicy.

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>Parametry

*dwCookie (właśc.*<br/>
Plik cookie odwołujący się do wskaźnika, `IUnknown` który ma zostać usunięty z tablicy.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli wskaźnik zostanie usunięty, w przeciwnym razie wartość FAŁsz.

## <a name="see-also"></a>Zobacz też

[Klasa CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
