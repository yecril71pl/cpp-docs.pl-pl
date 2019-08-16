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
ms.openlocfilehash: d55a6d6bfbcc6921fa0633753365f5799388dc27
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497244"
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
|[CComDynamicUnkArray::CComDynamicUnkArray](#ccomdynamicunkarray)|Konstruktor. Inicjuje wartości kolekcji na wartość NULL, a rozmiar kolekcji to zero.|
|[CComDynamicUnkArray:: ~ CComDynamicUnkArray](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComDynamicUnkArray:: Add](#add)|Wywołaj tę metodę, aby `IUnknown` dodać wskaźnik do tablicy.|
|[CComDynamicUnkArray::begin](#begin)|Zwraca wskaźnik do pierwszego `IUnknown` wskaźnika w kolekcji.|
|[CComDynamicUnkArray::clear](#clear)|Opróżnia tablicę.|
|[CComDynamicUnkArray::end](#end)|Zwraca wskaźnik do jednego z nich poza ostatnim `IUnknown` wskaźnikiem w kolekcji.|
|[CComDynamicUnkArray::GetAt](#getat)|Pobiera element pod określonym indeksem.|
|[CComDynamicUnkArray::GetCookie](#getcookie)|Wywołaj tę metodę, aby pobrać plik cookie skojarzony z `IUnknown` danym wskaźnikiem.|
|[CComDynamicUnkArray:: GetSize](#getsize)|Zwraca długość tablicy.|
|[CComDynamicUnkArray:: getnieznany](#getunknown)|Wywołaj tę metodę, aby `IUnknown` uzyskać wskaźnik skojarzony z danym plikiem cookie.|
|[CComDynamicUnkArray::Remove](#remove)|Wywołaj tę metodę, aby `IUnknown` usunąć wskaźnik z tablicy.|

## <a name="remarks"></a>Uwagi

`CComDynamicUnkArray`przechowuje dynamicznie przydzieloną tablicę `IUnknown` wskaźników, każdy interfejs w punkcie połączenia. `CComDynamicUnkArray`może być używany jako parametr klasy szablonu [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) .

Metody BEGIN i [End](#end) mogą służyć do zapętlenia przez wszystkie punkty połączenia (na przykład gdy zdarzenie jest wyzwalane). [](#begin) `CComDynamicUnkArray`

Aby uzyskać szczegółowe informacje na temat automatyzacji tworzenia serwerów proxy punktu połączenia [, zobacz Dodawanie punktów połączenia do obiektu](../../atl/adding-connection-points-to-an-object.md) .

> [!NOTE]
> **Uwaga** Klasa `CComDynamicUnkArray` jest używana przez kreatora **dodawania klasy** podczas tworzenia kontrolki, która ma punkty połączenia. Jeśli chcesz ręcznie określić liczbę punktów połączenia `CComDynamicUnkArray` , Zmień odwołanie z do `>` `CComUnkArray<` n, gdzie *n* to liczba wymaganych punktów połączenia.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

##  <a name="add"></a>CComDynamicUnkArray:: Add

Wywołaj tę metodę, aby `IUnknown` dodać wskaźnik do tablicy.

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>Parametry

*pUnk*<br/>
`IUnknown` Wskaźnik, który ma zostać dodany do tablicy.

### <a name="return-value"></a>Wartość zwracana

Zwraca plik cookie skojarzony z nowo dodanym wskaźnikiem.

##  <a name="begin"></a>CComDynamicUnkArray:: BEGIN

Zwraca wskaźnik do początku kolekcji `IUnknown` wskaźników interfejsu.

```
IUnknown**
    begin();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `IUnknown` wskaźnika interfejsu.

### <a name="remarks"></a>Uwagi

Kolekcja zawiera wskaźniki do interfejsów przechowywanych lokalnie jako `IUnknown`. Każdy `IUnknown` interfejs jest rzutowany do rzeczywistego typu interfejsu, a następnie wywoływany przez niego. Nie trzeba najpierw wykonywać zapytania dotyczącego interfejsu.

Przed użyciem `IUnknown` interfejsu należy sprawdzić, czy nie jest on pusty.

##  <a name="clear"></a>CComDynamicUnkArray:: Clear

Opróżnia tablicę.

```
void clear();
```

##  <a name="ccomdynamicunkarray"></a>CComDynamicUnkArray::CComDynamicUnkArray

Konstruktor.

```
CComDynamicUnkArray();
```

### <a name="remarks"></a>Uwagi

Ustawia rozmiar kolekcji na zero i inicjuje wartości NULL. Destruktor zwalnia kolekcję, w razie potrzeby.

##  <a name="dtor"></a>CComDynamicUnkArray:: ~ CComDynamicUnkArray

Destruktor.

```
~CComDynamicUnkArray();
```

### <a name="remarks"></a>Uwagi

Zwalnia zasoby przydzielone przez konstruktora klasy.

##  <a name="end"></a>CComDynamicUnkArray:: end

Zwraca wskaźnik do jednego z nich poza ostatnim `IUnknown` wskaźnikiem w kolekcji.

```
IUnknown**
    end();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `IUnknown` wskaźnika interfejsu.

##  <a name="getat"></a>CComDynamicUnkArray::GetAt

Pobiera element pod określonym indeksem.

```
IUnknown* GetAt(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks elementu, który ma zostać pobrany.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do interfejsu [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) .

##  <a name="getcookie"></a>CComDynamicUnkArray:: getcookas

Wywołaj tę metodę, aby pobrać plik cookie skojarzony z `IUnknown` danym wskaźnikiem.

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>Parametry

*ppFind*<br/>
`IUnknown` Wskaźnik, dla którego wymagany jest skojarzony plik cookie.

### <a name="return-value"></a>Wartość zwracana

Zwraca plik cookie skojarzony ze `IUnknown` wskaźnikiem lub zero, jeśli nie znaleziono pasującego `IUnknown` wskaźnika.

### <a name="remarks"></a>Uwagi

Jeśli istnieje więcej niż jedno wystąpienie tego samego `IUnknown` wskaźnika, funkcja ta zwraca plik cookie dla pierwszej z nich.

##  <a name="getsize"></a>CComDynamicUnkArray:: GetSize

Zwraca długość tablicy.

```
int GetSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Długość tablicy.

##  <a name="getunknown"></a>CComDynamicUnkArray:: getnieznany

Wywołaj tę metodę, aby `IUnknown` uzyskać wskaźnik skojarzony z danym plikiem cookie.

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>Parametry

*dwCookie*<br/>
Plik cookie, dla którego wymagany `IUnknown` jest skojarzony wskaźnik.

### <a name="return-value"></a>Wartość zwracana

`IUnknown` Zwraca wskaźnik lub wartość null, jeśli nie zostanie znaleziony pasujący plik cookie.

##  <a name="remove"></a>CComDynamicUnkArray:: Remove

Wywołaj tę metodę, aby `IUnknown` usunąć wskaźnik z tablicy.

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>Parametry

*dwCookie*<br/>
Plik cookie odwołujący się do wskaźnika, `IUnknown` który ma zostać usunięty z tablicy.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli wskaźnik został usunięty; w przeciwnym razie FALSE.

## <a name="see-also"></a>Zobacz także

[Klasa CComUnkArray](../../atl/reference/ccomunkarray-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
