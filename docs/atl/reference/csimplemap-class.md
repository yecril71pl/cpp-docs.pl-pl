---
title: Klasa CSimpleMap
ms.date: 11/04/2016
f1_keywords:
- CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap::_ArrayElementType
- ATLSIMPCOLL/ATL::CSimpleMap::_ArrayKeyType
- ATLSIMPCOLL/ATL::CSimpleMap::CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap::Add
- ATLSIMPCOLL/ATL::CSimpleMap::FindKey
- ATLSIMPCOLL/ATL::CSimpleMap::FindVal
- ATLSIMPCOLL/ATL::CSimpleMap::GetKeyAt
- ATLSIMPCOLL/ATL::CSimpleMap::GetSize
- ATLSIMPCOLL/ATL::CSimpleMap::GetValueAt
- ATLSIMPCOLL/ATL::CSimpleMap::Lookup
- ATLSIMPCOLL/ATL::CSimpleMap::Remove
- ATLSIMPCOLL/ATL::CSimpleMap::RemoveAll
- ATLSIMPCOLL/ATL::CSimpleMap::RemoveAt
- ATLSIMPCOLL/ATL::CSimpleMap::ReverseLookup
- ATLSIMPCOLL/ATL::CSimpleMap::SetAt
- ATLSIMPCOLL/ATL::CSimpleMap::SetAtIndex
helpviewer_keywords:
- CSimpleMap class
ms.assetid: 61b06eb4-ae73-44b0-a305-0afb5a33e8b1
ms.openlocfilehash: afd9f017bb0fb9a95a0ed4fd135dcbd5ea4ddba2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62277945"
---
# <a name="csimplemap-class"></a>Klasa CSimpleMap

Ta klasa udostępnia obsługę tablicy mapowania proste.

## <a name="syntax"></a>Składnia

```
template <class TKey, class TVal, class TEqual = CSimpleMapEqualHelper<TKey, TVal>>
class CSimpleMap
```

#### <a name="parameters"></a>Parametry

*TKey*<br/>
Typ klucza elementu.

*TVal*<br/>
Typ elementu wartości.

*TEqual*<br/>
Obiekt cech, definiujący testu równości dla elementów typu `T`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleMap::_ArrayElementType](#_arrayelementtype)|Element TypeDef dla typu wartości.|
|[CSimpleMap::_ArrayKeyType](#_arraykeytype)|Element TypeDef dla typu klucza.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleMap::CSimpleMap](#csimplemap)|Konstruktor.|
|[CSimpleMap::~CSimpleMap](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleMap::Add](#add)|Dodaje klucz i wartość skojarzoną z tablicą mapy.|
|[CSimpleMap::FindKey](#findkey)|Znajduje określony klucz.|
|[CSimpleMap::FindVal](#findval)|Wyszukuje określoną wartość.|
|[CSimpleMap::GetKeyAt](#getkeyat)|Pobiera określony klucz.|
|[CSimpleMap::GetSize](#getsize)|Zwraca liczbę wpisów w tablicy mapowania.|
|[CSimpleMap::GetValueAt](#getvalueat)|Pobiera określoną wartość.|
|[CSimpleMap::Lookup](#lookup)|Zwraca wartość skojarzoną z danym kluczem.|
|[CSimpleMap::Remove](#remove)|Usuwa klucz i wartość dopasowania.|
|[CSimpleMap::RemoveAll](#removeall)|Usuwa wszystkie klucze i wartości.|
|[CSimpleMap::RemoveAt](#removeat)|Usuwa określony klucz i wartość dopasowania.|
|[CSimpleMap::ReverseLookup](#reverselookup)|Zwraca klucz skojarzony z danej wartości.|
|[CSimpleMap::SetAt](#setat)|Ustawia wartość skojarzoną z danym kluczem.|
|[CSimpleMap::SetAtIndex](#setatindex)|Ustawia określony klucz i wartość.|

## <a name="remarks"></a>Uwagi

`CSimpleMap` zapewnia obsługę mapowania proste tablicę dla dowolnego typu `T`, Zarządzanie macierzą Nieuporządkowana kluczami elementów i ich skojarzone wartości.

Parametr `TEqual` umożliwia definiowanie funkcją porównania dla dwóch elementów typu `T`. Tworząc podobny do klasy [CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md), istnieje możliwość zmiany zachowania testu równości dla dowolnej podanej tablicy. Przykładowo zajmujące się tablicę wskaźników, może być przydatne do definiowania równości w zależności od wartości, które odwołują się wskaźniki. Domyślna implementacja używa **operator==()**.

Zarówno `CSimpleMap` i [CSimpleArray](../../atl/reference/csimplearray-class.md) znajdują się na zgodność z ATL poprzednie wersje i bardziej kompletne i skuteczne implementacje kolekcji są dostarczane przez [CAtlArray](../../atl/reference/catlarray-class.md) i [ CAtlMap](../../atl/reference/catlmap-class.md).

W przeciwieństwie do innych kolekcji mapy ATL i MFC ta klasa jest implementowane za pomocą prostej tablicy i wyszukiwania odnośników wymagają wyszukiwania liniowego. `CAtlMap` należy używać, jeśli tablica zawiera dużą liczbę elementów.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsimpcoll.h

## <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#91](../../atl/codesnippet/cpp/csimplemap-class_1.cpp)]

##  <a name="add"></a>  CSimpleMap::Add

Dodaje klucz i wartość skojarzoną z tablicą mapy.

```
BOOL Add(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz.

*Val*<br/>
Skojarzona wartość.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli klucz i wartość zostały pomyślnie dodano, wartość FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Każda para klucz / wartość dodana powoduje, że mapowanie tablicy pamięci może być zwolniony i ponownie rozdzielone, aby upewnić się, że dane dla każdej jest zawsze przechowywany w sposób ciągły. Oznacza to, że drugi element klucza zawsze bezpośrednio następuje klucza pierwszego elementu w pamięci i tak dalej.

##  <a name="_arrayelementtype"></a>  CSimpleMap::_ArrayElementType

Element typedef dla typu klucza.

```
typedef TVal _ArrayElementType;
```

##  <a name="_arraykeytype"></a>  CSimpleMap::_ArrayKeyType

Element typedef dla typu wartości.

```
typedef TKey _ArrayKeyType;
```

##  <a name="csimplemap"></a>  CSimpleMap::CSimpleMap

Konstruktor.

```
CSimpleMap();
```

### <a name="remarks"></a>Uwagi

Inicjuje elementy członkowskie danych.

##  <a name="dtor"></a>  CSimpleMap::~CSimpleMap

Destruktor.

```
~CSimpleMap();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby.

##  <a name="findkey"></a>  CSimpleMap::FindKey

Znajduje określony klucz.

```
int FindKey(const TKey& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz do wyszukania.

### <a name="return-value"></a>Wartość zwracana

Zwraca indeks klucza, jeśli znaleziono, w przeciwnym razie zwraca wartość -1.

##  <a name="findval"></a>  CSimpleMap::FindVal

Wyszukuje określoną wartość.

```
int FindVal(const TVal& val) const;
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Wartość do wyszukania.

### <a name="return-value"></a>Wartość zwracana

Zwraca indeks wartości, jeśli okaże się, w przeciwnym razie zwraca wartość -1.

##  <a name="getkeyat"></a>  CSimpleMap::GetKeyAt

Pobiera klucz pod określonym indeksem.

```
TKey& GetKeyAt(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks klucza do zwrócenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca klucz przywoływany przez *nIndex*.

### <a name="remarks"></a>Uwagi

Indeks przekazywane przez *nIndex* muszą być prawidłowe dla wartości zwracanej znaczące.

##  <a name="getsize"></a>  CSimpleMap::GetSize

Zwraca liczbę wpisów w tablicy mapowania.

```
int GetSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę wpisów (klucz i wartość jest jeden wpis) w tablicy mapowania.

##  <a name="getvalueat"></a>  CSimpleMap::GetValueAt

Pobiera wartość o określonym indeksie.

```
TVal& GetValueAt(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks wartości do zwrócenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość przywołana przez *nIndex*.

### <a name="remarks"></a>Uwagi

Indeks przekazywane przez *nIndex* muszą być prawidłowe dla wartości zwracanej znaczące.

##  <a name="lookup"></a>  CSimpleMap::Lookup

Zwraca wartość skojarzoną z danym kluczem.

```
TVal Lookup(const TKey& key) const;
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość skojarzoną. Jeśli znaleziono nie odpowiedniego klucza o wartości NULL jest zwracana.

##  <a name="remove"></a>  CSimpleMap::Remove

Usuwa klucz i wartość dopasowania.

```
BOOL Remove(const TKey& key);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli klucz i pasującej wartości zostały pomyślnie usunięte, wartość FALSE w przeciwnym razie.

##  <a name="removeall"></a>  CSimpleMap::RemoveAll

Usuwa wszystkie klucze i wartości.

```
void RemoveAll();
```

### <a name="remarks"></a>Uwagi

Usuwa wszystkie klucze i wartości z obiektu array mapowania.

##  <a name="removeat"></a>  CSimpleMap::RemoveAt

Usuwa klucz i wartość skojarzoną pod określonym indeksem.

```
BOOL RemoveAt(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks klucza i skojarzone wartości do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE, jeśli określony indeks jest nieprawidłowy indeks.

##  <a name="reverselookup"></a>  CSimpleMap::ReverseLookup

Zwraca klucz skojarzony z danej wartości.

```
TKey ReverseLookup(const TVal& val) const;
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Wartość.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość skojarzonego klucza. Jeśli znaleziono nie odpowiedniego klucza o wartości NULL jest zwracana.

##  <a name="setat"></a>  CSimpleMap::SetAt

Ustawia wartość skojarzoną z danym kluczem.

```
BOOL SetAt(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Klucz.

*Val*<br/>
Nowa wartość do przypisania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli klucz został znaleziony, a wartość został pomyślnie zmieniony, wartość FALSE w przeciwnym razie.

##  <a name="setatindex"></a>  CSimpleMap::SetAtIndex

Ustawia klucz i wartość z określonym indeksem.

```
BOOL SetAtIndex(
    int nIndex,
    const TKey& key,
    const TVal& val);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks odwołuje się do klucza i wartości parowanie, aby zmienić.

*Klucz*<br/>
Nowy klucz.

*Val*<br/>
Nowa wartość.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli powodzenia lub wartość FAŁSZ Jeśli indeks jest nieprawidłowy.

### <a name="remarks"></a>Uwagi

Aktualizuje klucz i wartość wskazywana przez *nIndex*.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../../atl/atl-class-overview.md)
