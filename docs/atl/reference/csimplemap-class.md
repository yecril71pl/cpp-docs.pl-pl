---
title: Klasa CSimpleMap | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CSimpleMap class
ms.assetid: 61b06eb4-ae73-44b0-a305-0afb5a33e8b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 415ce3c0d6b060ffc71aa448656cf9ad45a3e7bb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="csimplemap-class"></a>Klasa CSimpleMap
Ta klasa obsługuje tablicy mapowania proste.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class TKey, class TVal, class TEqual = CSimpleMapEqualHelper<TKey, TVal>>  
class CSimpleMap
```  
  
#### <a name="parameters"></a>Parametry  
 `TKey`  
 Typ klucza elementu.  
  
 `TVal`  
 Typ wartości elementu.  
  
 `TEqual`  
 Obiekt cechy Definiowanie testu równości dla elementów typu `T`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSimpleMap::_ArrayElementType](#_arrayelementtype)|Element TypeDef dla typu wartości.|  
|[CSimpleMap::_ArrayKeyType](#_arraykeytype)|Element TypeDef dla typu klucza.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSimpleMap::CSimpleMap](#csimplemap)|Konstruktor.|  
|[CSimpleMap:: ~ CSimpleMap](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSimpleMap::Add](#add)|Dodaje klucz i wartość skojarzoną z tablicą mapy.|  
|[CSimpleMap::FindKey](#findkey)|Znajduje określony klucz.|  
|[CSimpleMap::FindVal](#findval)|Wyszukuje określoną wartość.|  
|[CSimpleMap::GetKeyAt](#getkeyat)|Pobiera określony klucz.|  
|[CSimpleMap::GetSize](#getsize)|Zwraca liczbę wpisów w tabeli mapowania.|  
|[CSimpleMap::GetValueAt](#getvalueat)|Pobiera określoną wartość.|  
|[CSimpleMap::Lookup](#lookup)|Zwraca wartość skojarzoną z danym kluczem.|  
|[CSimpleMap::Remove](#remove)|Usuwa klucz i wartość.|  
|[CSimpleMap::RemoveAll](#removeall)|Usuwa wszystkie klucze i wartości.|  
|[CSimpleMap::RemoveAt](#removeat)|Usuwa określony klucz i wartość.|  
|[CSimpleMap::ReverseLookup](#reverselookup)|Zwraca klucz skojarzony z podanej wartości.|  
|[CSimpleMap::SetAt](#setat)|Ustawia wartość skojarzoną z danym kluczem.|  
|[CSimpleMap::SetAtIndex](#setatindex)|Ustawia określony klucz i wartość.|  
  
## <a name="remarks"></a>Uwagi  
 `CSimpleMap` zapewnia obsługę dla każdego typu tablicy mapowania proste `T`, zarządzanie nieuporządkowaną tablicę elementów kluczy oraz powiązanych wartości.  
  
 Parametr `TEqual` umożliwia definiowanie funkcję porównania dla dwóch elementów typu `T`. Tworząc podobny do klasy [CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md), można zmienić zachowanie testu równości dla dowolnej podanej tablicy. Na przykład podczas pracy nad tablicy wskaźników, może być przydatne do definiowania równości w zależności od wartości, które odwołują się wskaźniki. Domyślna implementacja używa **operator==()**.  
  
 Zarówno `CSimpleMap` i [CSimpleArray](../../atl/reference/csimplearray-class.md) podano zwalnia zgodność z poprzedniej biblioteki ATL i bardziej pełne i wydajne implementacje kolekcji są dostarczane przez [CAtlArray](../../atl/reference/catlarray-class.md) i [ CAtlMap](../../atl/reference/catlmap-class.md).  
  
 W przeciwieństwie do innych kolekcji mapy w ATL i MFC ta klasa jest realizowana za pomocą prostego tablicy i wyszukiwania wyszukiwania wymagają wyszukiwania liniowego. `CAtlMap` powinien być używany, gdy tablica zawiera dużą liczbę elementów.  
  
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
 `key`  
 Klucz.  
  
 *Val*  
 Skojarzona wartość.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli klucz i wartość zostały pomyślnie dodano, wartość FALSE w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Każda para klucza i wartości dodać mapowania macierz pamięci może być zwolniony i przydzielić, aby upewnić się, że dane dla każdego zawsze są przechowywane ciągłym przyczyny. Oznacza to drugi element klucza zawsze bezpośrednio następuje pierwszy element klucza w pamięci i tak dalej.  
  
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
  
##  <a name="dtor"></a>  CSimpleMap:: ~ CSimpleMap  
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
 `key`  
 Klucz do wyszukania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca indeks kluczy, jeśli znaleziono, w przeciwnym razie zwraca wartość -1.  
  
##  <a name="findval"></a>  CSimpleMap::FindVal  
 Wyszukuje określoną wartość.  
  
```
int FindVal(const TVal& val) const;
```  
  
### <a name="parameters"></a>Parametry  
 *Val*  
 Wartość do wyszukania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca indeks wartości, jeśli został znaleziony, w przeciwnym razie zwraca wartość -1.  
  
##  <a name="getkeyat"></a>  CSimpleMap::GetKeyAt  
 Pobiera klucz pod określonym indeksem.  
  
```
TKey& GetKeyAt(int nIndex) const;
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Indeks klucza do zwrócenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca klucz odwołuje się `nIndex`.  
  
### <a name="remarks"></a>Uwagi  
 Indeks przekazany przez `nIndex` musi być prawidłowy dla wartości zwracanej znaczące.  
  
##  <a name="getsize"></a>  CSimpleMap::GetSize  
 Zwraca liczbę wpisów w tabeli mapowania.  
  
```
int GetSize() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę wpisów (klucz i wartość jest jeden wpis) w tabeli mapowania.  
  
##  <a name="getvalueat"></a>  CSimpleMap::GetValueAt  
 Pobiera wartość pod określonym indeksem.  
  
```
TVal& GetValueAt(int nIndex) const;
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Indeks wartości do zwrócenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość odwołuje się `nIndex`.  
  
### <a name="remarks"></a>Uwagi  
 Indeks przekazany przez `nIndex` musi być prawidłowy dla wartości zwracanej znaczące.  
  
##  <a name="lookup"></a>  CSimpleMap::Lookup  
 Zwraca wartość skojarzoną z danym kluczem.  
  
```
TVal Lookup(const TKey& key) const;
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość skojarzoną. Jeśli klucza nie pasujące ma znaleziony, wartość NULL, jest zwracana.  
  
##  <a name="remove"></a>  CSimpleMap::Remove  
 Usuwa klucz i wartość.  
  
```
BOOL Remove(const TKey& key);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli klucz i pasującej wartości zostały pomyślnie usunięte, wartość FALSE w przeciwnym razie wartość.  
  
##  <a name="removeall"></a>  CSimpleMap::RemoveAll  
 Usuwa wszystkie klucze i wartości.  
  
```
void RemoveAll();
```  
  
### <a name="remarks"></a>Uwagi  
 Usuwa wszystkie klucze i wartości z obiektu tablicy mapowania.  
  
##  <a name="removeat"></a>  CSimpleMap::RemoveAt  
 Usuwa klucz i wartość skojarzoną pod określonym indeksem.  
  
```
BOOL RemoveAt(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Indeks klucza i skojarzoną wartość do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA w przypadku powodzenia, FALSE, jeśli określony indeks jest nieprawidłowy indeks.  
  
##  <a name="reverselookup"></a>  CSimpleMap::ReverseLookup  
 Zwraca klucz skojarzony z podanej wartości.  
  
```
TKey ReverseLookup(const TVal& val) const;
```  
  
### <a name="parameters"></a>Parametry  
 *Val*  
 Wartość.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca skojarzony klucz. Jeśli klucza nie pasujące ma znaleziony, wartość NULL, jest zwracana.  
  
##  <a name="setat"></a>  CSimpleMap::SetAt  
 Ustawia wartość skojarzoną z danym kluczem.  
  
```
BOOL SetAt(const TKey& key, const TVal& val);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klucz.  
  
 *Val*  
 Nowa wartość do przypisania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli klucz został znaleziony, a wartość został pomyślnie zmieniony, wartość FALSE w przeciwnym razie wartość.  
  
##  <a name="setatindex"></a>  CSimpleMap::SetAtIndex  
 Ustawia klucz i wartość w określonym indeksie.  
  
```
BOOL SetAtIndex(  
    int nIndex,
    const TKey& key,
    const TVal& val);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Indeks odwołujące się do klucz i wartość parowanie można zmienić.  
  
 `key`  
 Nowy klucz.  
  
 *Val*  
 Nowa wartość.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli powodzenia lub wartość FALSE Jeśli indeks jest nieprawidłowy.  
  
### <a name="remarks"></a>Uwagi  
 Aktualizuje klucz i wartość wskazywana przez `nIndex`.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
