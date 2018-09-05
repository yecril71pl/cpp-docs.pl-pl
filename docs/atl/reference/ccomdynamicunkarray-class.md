---
title: Klasa CComDynamicUnkArray | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], managing
- CComDynamicUnkArray class
ms.assetid: 202470d7-9a1b-498f-b96d-659d681acd65
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71b36f19cc6e3deddbd5984e63b70c61a0ca8ea8
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762772"
---
# <a name="ccomdynamicunkarray-class"></a>Klasa CComDynamicUnkArray

Ta klasa przechowuje tablicę `IUnknown` wskaźników.

## <a name="syntax"></a>Składnia

```
class CComDynamicUnkArray
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComDynamicUnkArray::CComDynamicUnkArray](#ccomdynamicunkarray)|Konstruktor. Inicjuje wartości kolekcji, które mają wartość NULL i rozmiar kolekcji do zera.|
|[CComDynamicUnkArray:: ~ CComDynamicUnkArray](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComDynamicUnkArray::Add](#add)|Wywołaj tę metodę, aby dodać `IUnknown` wskaźnika do tablicy.|
|[CComDynamicUnkArray::begin](#begin)|Zwraca wskaźnik do pierwszego `IUnknown` wskaźnika w kolekcji.|
|[CComDynamicUnkArray::clear](#clear)|Opróżnia tablicy.|
|[CComDynamicUnkArray::end](#end)|Zwraca wskaźnik do pierwszego do ostatniego `IUnknown` wskaźnika w kolekcji.|
|[CComDynamicUnkArray::GetAt](#getat)|Pobiera element pod określonym indeksem.|
|[CComDynamicUnkArray::GetCookie](#getcookie)|Wywołaj tę metodę, aby pobrać plik cookie skojarzone z danym `IUnknown` wskaźnika.|
|[CComDynamicUnkArray::GetSize](#getsize)|Zwraca długość tablicy.|
|[CComDynamicUnkArray::GetUnknown](#getunknown)|Wywołaj tę metodę, aby uzyskać `IUnknown` kursor skojarzony z danym pliku cookie.|
|[CComDynamicUnkArray::Remove](#remove)|Wywołaj tę metodę, aby usunąć `IUnknown` wskaźnika z tablicy.|

## <a name="remarks"></a>Uwagi

`CComDynamicUnkArray` przechowuje dynamicznie przydzielanej tablicy `IUnknown` wskaźników, każdy punkt interfejsu połączenia. `CComDynamicUnkArray` może służyć jako parametr do [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) klasy szablonu.

`CComDynamicUnkArray` Metody [rozpocząć](#begin) i [zakończenia](#end) może służyć do pętli wszystkich punktów połączenia (na przykład, gdy zdarzenie jest wyzwalane).

Zobacz [Dodawanie punktów połączenia do obiektu](../../atl/adding-connection-points-to-an-object.md) szczegółowe informacje dotyczące automatyzacji tworzenia połączenia punktu proxy.

> [!NOTE]
> **Uwaga** klasy `CComDynamicUnkArray` jest używany przez **Dodaj klasę** kreatora podczas tworzenia kontrolki, która ma punkty połączenia. Jeśli chcesz ręcznie określić liczbę punktów połączenia, zmień odwołanie z `CComDynamicUnkArray` do `CComUnkArray<` *n* `>`, gdzie *n* liczbę punktów połączenia Wymagane.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="add"></a>  CComDynamicUnkArray::Add

Wywołaj tę metodę, aby dodać `IUnknown` wskaźnika do tablicy.

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>Parametry

*pUnk*  
`IUnknown` Wskaźnik do dodania do tablicy.

### <a name="return-value"></a>Wartość zwracana

Zwraca plik cookie skojarzone z dodanym wskaźnika.

##  <a name="begin"></a>  CComDynamicUnkArray::begin

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

##  <a name="clear"></a>  CComDynamicUnkArray::clear

Opróżnia tablicy.

```
void clear();
```

##  <a name="ccomdynamicunkarray"></a>  CComDynamicUnkArray::CComDynamicUnkArray

Konstruktor.

```
CComDynamicUnkArray();
```

### <a name="remarks"></a>Uwagi

Ustawia rozmiar kolekcji zero i inicjuje wartości null. Destruktor zwalnia kolekcji, jeśli to konieczne.

##  <a name="dtor"></a>  CComDynamicUnkArray:: ~ CComDynamicUnkArray

Destruktor.

```
~CComDynamicUnkArray();
```

### <a name="remarks"></a>Uwagi

Zwalnia zasoby przydzielone przez konstruktora klasy.

##  <a name="end"></a>  CComDynamicUnkArray::end

Zwraca wskaźnik do pierwszego do ostatniego `IUnknown` wskaźnika w kolekcji.

```
IUnknown**
    end();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `IUnknown` wskaźnika interfejsu.

##  <a name="getat"></a>  CComDynamicUnkArray::GetAt

Pobiera element pod określonym indeksem.

```
IUnknown* GetAt(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*  
Indeks elementu do pobrania.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) interfejsu.

##  <a name="getcookie"></a>  CComDynamicUnkArray::GetCookie

Wywołaj tę metodę, aby pobrać plik cookie skojarzone z danym `IUnknown` wskaźnika.

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>Parametry

*ppFind*  
`IUnknown` Wskaźnika, dla których skojarzone pliki cookie jest wymagana.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość pliku cookie skojarzona z `IUnknown` wskaźnika lub zero, jeśli brak zgodności `IUnknown` znajduje się kursor.

### <a name="remarks"></a>Uwagi

Jeśli istnieje więcej niż jedno wystąpienie tego samego `IUnknown` wskaźnikiem, funkcja zwraca wartość pliku cookie dla pierwszej.

##  <a name="getsize"></a>  CComDynamicUnkArray::GetSize

Zwraca długość tablicy.

```
int GetSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Długość tablicy.

##  <a name="getunknown"></a>  CComDynamicUnkArray::GetUnknown

Wywołaj tę metodę, aby uzyskać `IUnknown` kursor skojarzony z danym pliku cookie.

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>Parametry

*dwCookie*  
Plik cookie, dla którego skojarzonego `IUnknown` wskaźnika jest wymagana.

### <a name="return-value"></a>Wartość zwracana

Zwraca `IUnknown` wskaźnika lub wartość NULL, jeśli znaleziono nie pasującego pliku cookie.

##  <a name="remove"></a>  CComDynamicUnkArray::Remove

Wywołaj tę metodę, aby usunąć `IUnknown` wskaźnika z tablicy.

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>Parametry

*dwCookie*  
Odwołanie do pliku cookie `IUnknown` wskaźnika do usunięcia z tablicy.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli wskaźnik jest usunięte; w przeciwnym razie wartość FALSE.

## <a name="see-also"></a>Zobacz też

[Klasa CComUnkArray](../../atl/reference/ccomunkarray-class.md)   
[Klasa — Przegląd](../../atl/atl-class-overview.md)
