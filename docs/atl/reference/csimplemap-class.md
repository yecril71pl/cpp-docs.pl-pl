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
ms.openlocfilehash: eed41c2250728d257b6d303e79c3afd36a543dbb
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747642"
---
# <a name="csimplemap-class"></a>Klasa CSimpleMap

Ta klasa zapewnia obsługę prostej tablicy mapowania.

## <a name="syntax"></a>Składnia

```
template <class TKey, class TVal, class TEqual = CSimpleMapEqualHelper<TKey, TVal>>
class CSimpleMap
```

#### <a name="parameters"></a>Parametry

*Tkey*<br/>
Typ elementu klucza.

*TVal (własn.*<br/>
Typ elementu wartości.

*TEqual ( TEqual )*<br/>
Obiekt cechy, definiujący test równości `T`dla elementów typu .

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleMap::_ArrayElementType](#_arrayelementtype)|Typedef dla typu wartości.|
|[CSimpleMap::_ArrayKeyType](#_arraykeytype)|Typedef dla typu klucza.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleMap::CSimpleMap](#csimplemap)|Konstruktor.|
|[CSimpleMap::~CSimpleMap](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleMap::Dodaj](#add)|Dodaje klucz i skojarzoną wartość do tablicy mapy.|
|[CSimpleMap::FindKey](#findkey)|Znajduje określony klucz.|
|[CSimpleMap::FindVal](#findval)|Znajduje określoną wartość.|
|[CSimpleMap::GetKeyAt](#getkeyat)|Pobiera określony klucz.|
|[CSimpleMap::GetSize](#getsize)|Zwraca liczbę wpisów w tablicy mapowania.|
|[CSimpleMap::GetValueAt](#getvalueat)|Pobiera określoną wartość.|
|[CSimpleMap::Odnośnik](#lookup)|Zwraca wartość skojarzoną z danym kluczem.|
|[CSimpleMap::Usuń](#remove)|Usuwa klucz i dopasowującą wartość.|
|[CSimpleMap::UsuńWszystki](#removeall)|Usuwa wszystkie klucze i wartości.|
|[CSimpleMap::RemoveAt](#removeat)|Usuwa określony klucz i dopasowującą wartość.|
|[CSimpleMap::ReverseLookup](#reverselookup)|Zwraca klucz skojarzony z daną wartością.|
|[CSimpleMap::SetAt](#setat)|Ustawia wartość skojarzoną z danym kluczem.|
|[CSimpleMap::SetAtIndex](#setatindex)|Ustawia określony klucz i wartość.|

## <a name="remarks"></a>Uwagi

`CSimpleMap`zapewnia obsługę prostej tablicy mapowania dowolnego typu, `T`zarządzającej nieuiszczona tablicą kluczowych elementów i skojarzonymi z nimi wartościami.

Parametr `TEqual` umożliwia zdefiniowanie funkcji równości dla dwóch elementów typu `T`. Tworząc klasę podobną do [CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md), można zmienić zachowanie testu równości dla danej tablicy. Na przykład w przypadku czynienia z tablicy wskaźników, może być przydatne do definiowania równości w zależności od wartości odniesienia wskaźników. Domyślna implementacja wykorzystuje **operator==()**.

Zarówno `CSimpleMap` i [CSimpleArray](../../atl/reference/csimplearray-class.md) są przewidziane dla zgodności z poprzednimi wersjami ATL i bardziej kompletne i wydajne implementacje kolekcji są dostarczane przez [CAtlArray](../../atl/reference/catlarray-class.md) i [CAtlMap](../../atl/reference/catlmap-class.md).

W przeciwieństwie do innych kolekcji map w ATL i MFC, ta klasa jest implementowana za pomocą prostej tablicy, a wyszukiwanie wyszukiwania wymaga wyszukiwania liniowego. `CAtlMap`należy użyć, gdy tablica zawiera dużą liczbę elementów.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsimpcoll.h

## <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#91](../../atl/codesnippet/cpp/csimplemap-class_1.cpp)]

## <a name="csimplemapadd"></a><a name="add"></a>CSimpleMap::Dodaj

Dodaje klucz i skojarzoną wartość do tablicy mapy.

```
BOOL Add(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klucz.

*Val*<br/>
Skojarzona wartość.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli klucz i wartość zostały pomyślnie dodane, FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Każdy klucz i wartość pary dodane powoduje, że pamięć tablicy mapowania mają być zwalniane i ponownie przydzielane, w celu zapewnienia, że dane dla każdego z nich są zawsze przechowywane w sposób ciągły. Oznacza to, że drugi element klucza zawsze bezpośrednio następuje pierwszy element klucza w pamięci i tak dalej.

## <a name="csimplemap_arrayelementtype"></a><a name="_arrayelementtype"></a>CSimpleMap::_ArrayElementType

Typedef dla typu klucza.

```
typedef TVal _ArrayElementType;
```

## <a name="csimplemap_arraykeytype"></a><a name="_arraykeytype"></a>CSimpleMap::_ArrayKeyType

Typedef dla typu wartości.

```
typedef TKey _ArrayKeyType;
```

## <a name="csimplemapcsimplemap"></a><a name="csimplemap"></a>CSimpleMap::CSimpleMap

Konstruktor.

```
CSimpleMap();
```

### <a name="remarks"></a>Uwagi

Inicjuje elementy członkowskie danych.

## <a name="csimplemapcsimplemap"></a><a name="dtor"></a>CSimpleMap::~CSimpleMap

Destruktor.

```
~CSimpleMap();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby.

## <a name="csimplemapfindkey"></a><a name="findkey"></a>CSimpleMap::FindKey

Znajduje określony klucz.

```
int FindKey(const TKey& key) const;
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klucz do wyszukiwania.

### <a name="return-value"></a>Wartość zwracana

Zwraca indeks klucza, jeśli zostanie znaleziony, w przeciwnym razie zwraca wartość -1.

## <a name="csimplemapfindval"></a><a name="findval"></a>CSimpleMap::FindVal

Znajduje określoną wartość.

```
int FindVal(const TVal& val) const;
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Wartość, dla której ma być wyszukiwana.

### <a name="return-value"></a>Wartość zwracana

Zwraca indeks wartości, jeśli zostanie znaleziony, w przeciwnym razie zwraca wartość -1.

## <a name="csimplemapgetkeyat"></a><a name="getkeyat"></a>CSimpleMap::GetKeyAt

Pobiera klucz w określonym indeksie.

```
TKey& GetKeyAt(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks klucza do powrotu.

### <a name="return-value"></a>Wartość zwracana

Zwraca klucz, do którego odwołuje się *nIndex*.

### <a name="remarks"></a>Uwagi

Indeks przekazany przez *nIndex* musi być prawidłowy dla wartości zwracanej, aby mieć znaczenie.

## <a name="csimplemapgetsize"></a><a name="getsize"></a>CSimpleMap::GetSize

Zwraca liczbę wpisów w tablicy mapowania.

```
int GetSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę wpisów (klucz i wartość to jeden wpis) w tablicy mapowania.

## <a name="csimplemapgetvalueat"></a><a name="getvalueat"></a>CSimpleMap::GetValueAt

Pobiera wartość w określonym indeksie.

```
TVal& GetValueAt(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks wartości do zwrócenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość, do którego odwołuje się *nIndex*.

### <a name="remarks"></a>Uwagi

Indeks przekazany przez *nIndex* musi być prawidłowy dla wartości zwracanej, aby mieć znaczenie.

## <a name="csimplemaplookup"></a><a name="lookup"></a>CSimpleMap::Odnośnik

Zwraca wartość skojarzoną z danym kluczem.

```
TVal Lookup(const TKey& key) const;
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klucz.

### <a name="return-value"></a>Wartość zwracana

Zwraca skojarzoną wartość. Jeśli nie zostanie znaleziony pasujący klucz, zwracana jest wartość NULL.

## <a name="csimplemapremove"></a><a name="remove"></a>CSimpleMap::Usuń

Usuwa klucz i dopasowującą wartość.

```
BOOL Remove(const TKey& key);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klucz.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli klucz i odpowiadająca jej wartość zostały pomyślnie usunięte, w przeciwnym razie wartość FAŁsz.

## <a name="csimplemapremoveall"></a><a name="removeall"></a>CSimpleMap::UsuńWszystki

Usuwa wszystkie klucze i wartości.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Uwagi

Usuwa wszystkie klucze i wartości z obiektu tablicy mapowania.

## <a name="csimplemapremoveat"></a><a name="removeat"></a>CSimpleMap::RemoveAt

Usuwa klucz i skojarzoną wartość w określonym indeksie.

```
BOOL RemoveAt(int nIndex);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks klucza i skojarzonej wartości do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA po sukcesie, WARTOŚĆ FAŁSZ, jeśli określony indeks jest nieprawidłowym indeksem.

## <a name="csimplemapreverselookup"></a><a name="reverselookup"></a>CSimpleMap::ReverseLookup

Zwraca klucz skojarzony z daną wartością.

```
TKey ReverseLookup(const TVal& val) const;
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Wartość.

### <a name="return-value"></a>Wartość zwracana

Zwraca skojarzony klucz. Jeśli nie zostanie znaleziony pasujący klucz, zwracana jest wartość NULL.

## <a name="csimplemapsetat"></a><a name="setat"></a>CSimpleMap::SetAt

Ustawia wartość skojarzoną z danym kluczem.

```
BOOL SetAt(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klucz.

*Val*<br/>
Nowa wartość do przypisania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli klucz został znaleziony, a wartość została pomyślnie zmieniona, FALSE w przeciwnym razie.

## <a name="csimplemapsetatindex"></a><a name="setatindex"></a>CSimpleMap::SetAtIndex

Ustawia klucz i wartość w określonym indeksie.

```
BOOL SetAtIndex(
    int nIndex,
    const TKey& key,
    const TVal& val);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks, odwołując się do parowania klucza i wartości, aby zmienić.

*key*<br/>
Nowy klucz.

*Val*<br/>
Nowa wartość.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli zakończy się pomyślnie, wartość FAŁSZ, jeśli indeks nie był prawidłowy.

### <a name="remarks"></a>Uwagi

Aktualizuje zarówno klucz, jak i wartość wskazywał przez *nIndex*.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
