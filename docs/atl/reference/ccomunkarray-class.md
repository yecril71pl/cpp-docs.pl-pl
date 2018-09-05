---
title: Klasa CComUnkArray | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], managing
- CComUnkArray class
ms.assetid: 5fd4b378-a7b5-4cc1-8866-8ab72a73639e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9b977875655182f1cbc822540cf021635f525f7e
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43756421"
---
# <a name="ccomunkarray-class"></a>Klasa CComUnkArray

Ta klasa przechowuje `IUnknown` wskaźników i jest przeznaczony do użycia jako parametr do [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) klasy szablonu.

## <a name="syntax"></a>Składnia

```
template<unsigned int nMaxSize>
class CComUnkArray
```

#### <a name="parameters"></a>Parametry

*nMaxSize*  
Maksymalna liczba `IUnknown` wskaźników, które mogą być przechowywane w tablicy statycznej.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComUnkArray::CComUnkArray](#ccomunkarray)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComUnkArray::Add](#add)|Wywołaj tę metodę, aby dodać `IUnknown` wskaźnika do tablicy.|
|[CComUnkArray::begin](#begin)|Zwraca wskaźnik do pierwszego `IUnknown` wskaźnika w kolekcji.|
|[CComUnkArray::end](#end)|Zwraca wskaźnik do pierwszego do ostatniego `IUnknown` wskaźnika w kolekcji.|
|[CComUnkArray::GetCookie](#getcookie)|Wywołaj tę metodę, aby pobrać plik cookie skojarzone z danym `IUnknown` wskaźnika.|
|[CComUnkArray::GetUnknown](#getunknown)|Wywołaj tę metodę, aby uzyskać `IUnknown` kursor skojarzony z danym pliku cookie.|
|[CComUnkArray::Remove](#remove)|Wywołaj tę metodę, aby usunąć `IUnknown` wskaźnika z tablicy.|

## <a name="remarks"></a>Uwagi

`CComUnkArray` zawiera stałą liczbą `IUnknown` wskaźników, każdy punkt interfejsu połączenia. `CComUnkArray` może służyć jako parametr do [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) klasy szablonu. `CComUnkArray<1>` jest specjalizacją szablonu `CComUnkArray` , został zoptymalizowany dla punktu jedno połączenie.

`CComUnkArray` Metody [rozpocząć](#begin) i [zakończenia](#end) może służyć do pętli wszystkich punktów połączenia (na przykład, gdy zdarzenie jest wyzwalane).

Zobacz [Dodawanie punktów połączenia do obiektu](../../atl/adding-connection-points-to-an-object.md) szczegółowe informacje dotyczące automatyzacji tworzenia połączenia punktu proxy.

> [!NOTE]
> **Uwaga** klasy [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md) jest używany przez **Dodaj klasę** kreatora podczas tworzenia kontrolki, która ma punkty połączenia. Jeśli chcesz ręcznie określić liczbę punktów połączenia, zmień odwołanie z `CComDynamicUnkArray` do `CComUnkArray<` *n* `>`, gdzie *n* liczbę punktów połączenia Wymagane.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="add"></a>  CComUnkArray::Add

Wywołaj tę metodę, aby dodać `IUnknown` wskaźnika do tablicy.

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>Parametry

*pUnk*  
Wywołaj tę metodę, aby dodać `IUnknown` wskaźnika do tablicy.

### <a name="return-value"></a>Wartość zwracana

Zwraca plik cookie skojarzone z wskaźnik nowo dodanych lub 0, jeśli tablica nie jest wystarczająco duży, aby zawierała nowy wskaźnik.

##  <a name="begin"></a>  CComUnkArray::begin

Zwraca wskaźnik do początku kolekcji `IUnknown` wskaźniki interfejsu.

```
IUnknown**
    begin();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `IUnknown` wskaźnika interfejsu.

### <a name="remarks"></a>Uwagi

Kolekcja zawiera wskaźniki do interfejsów przechowywane lokalnie, jak `IUnknown`. Każdy rzutowania `IUnknown` interfejs do typu rzeczywistego interfejsu, a następnie wywołać przy jego użyciu. Nie trzeba najpierw wyszukać interfejsu.

Przed rozpoczęciem korzystania z `IUnknown` interfejsu, należy sprawdzić, czy nie ma wartość NULL.

##  <a name="ccomunkarray"></a>  CComUnkArray::CComUnkArray

Konstruktor.

```
CComUnkArray();
```

### <a name="remarks"></a>Uwagi

Ustawia kolekcję zawierającą `nMaxSize` `IUnknown` wskaźników i inicjuje wskaźniki do wartości NULL.

##  <a name="end"></a>  CComUnkArray::end

Zwraca wskaźnik do pierwszego do ostatniego `IUnknown` wskaźnika w kolekcji.

```
IUnknown**
    end();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `IUnknown` wskaźnika interfejsu.

### <a name="remarks"></a>Uwagi

`CComUnkArray` Metody `begin` i `end` może służyć do pętli wszystkich punktów połączenia, na przykład, gdy zdarzenie jest wywoływane.

[!code-cpp[NVC_ATL_COM#44](../../atl/codesnippet/cpp/ccomunkarray-class_1.cpp)]

##  <a name="getcookie"></a>  CComUnkArray::GetCookie

Wywołaj tę metodę, aby pobrać plik cookie skojarzone z danym `IUnknown` wskaźnika.

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>Parametry

*ppFind*  
`IUnknown` Wskaźnika, dla których skojarzone pliki cookie jest wymagana.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość pliku cookie skojarzona z `IUnknown` wskaźnika lub 0, jeśli brak zgodności `IUnknown` znajduje się kursor.

### <a name="remarks"></a>Uwagi

Jeśli istnieje więcej niż jedno wystąpienie tego samego `IUnknown` wskaźnikiem, funkcja zwraca wartość pliku cookie dla pierwszej.

##  <a name="getunknown"></a>  CComUnkArray::GetUnknown

Wywołaj tę metodę, aby uzyskać `IUnknown` kursor skojarzony z danym pliku cookie.

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>Parametry

*dwCookie*  
Plik cookie, dla którego skojarzonego `IUnknown` wskaźnika jest wymagana.

### <a name="return-value"></a>Wartość zwracana

Zwraca `IUnknown` wskaźnika lub wartość NULL, jeśli znaleziono nie pasującego pliku cookie.

##  <a name="remove"></a>  CComUnkArray::Remove

Wywołaj tę metodę, aby usunąć `IUnknown` wskaźnika z tablicy.

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>Parametry

*dwCookie*  
Odwołanie do pliku cookie `IUnknown` wskaźnika do usunięcia z tablicy.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli wskaźnik jest usunięte, wartość FALSE w przeciwnym razie.

## <a name="see-also"></a>Zobacz też

[Klasa CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)   
[Klasa — Przegląd](../../atl/atl-class-overview.md)
