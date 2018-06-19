---
title: Klasa CSimpleArray | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray::CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray::Add
- ATLSIMPCOLL/ATL::CSimpleArray::Find
- ATLSIMPCOLL/ATL::CSimpleArray::GetData
- ATLSIMPCOLL/ATL::CSimpleArray::GetSize
- ATLSIMPCOLL/ATL::CSimpleArray::Remove
- ATLSIMPCOLL/ATL::CSimpleArray::RemoveAll
- ATLSIMPCOLL/ATL::CSimpleArray::RemoveAt
- ATLSIMPCOLL/ATL::CSimpleArray::SetAtIndex
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArray class
ms.assetid: ee0c9f39-b61c-4c18-bc43-4eada21dca3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 187dee79cd09e366fb56d9cd0e71395589476a69
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364274"
---
# <a name="csimplearray-class"></a>Klasa CSimpleArray
Ta klasa dostarcza metody do zarządzania proste tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T, class TEqual = CSimpleArrayEqualHelper<T>>  
class CSimpleArray
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych, które mają być przechowywane w tablicy.  
  
 `TEqual`  
 Obiekt cechy Definiowanie testu równości dla elementów typu `T`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSimpleArray::CSimpleArray](#csimplearray)|Konstruktor proste tablicy.|  
|[CSimpleArray:: ~ CSimpleArray](#dtor)|Destruktor dla elementu tablicy proste.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSimpleArray::Add](#add)|Dodaje nowy element do tablicy.|  
|[CSimpleArray::Find](#find)|Odnajduje element w tablicy.|  
|[CSimpleArray::GetData](#getdata)|Zwraca wskaźnik do danych przechowywanych w tablicy.|  
|[CSimpleArray::GetSize](#getsize)|Zwraca liczbę elementów przechowywane w tablicy.|  
|[CSimpleArray::Remove](#remove)|Usuwa określonego elementu z tablicy.|  
|[CSimpleArray::RemoveAll](#removeall)|Usuwa wszystkie elementy z tablicy.|  
|[CSimpleArray::RemoveAt](#removeat)|Usuwa określony element z tablicy.|  
|[CSimpleArray::SetAtIndex](#setatindex)|Ustawia określony element w tablicy.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSimpleArray::operator\[\]](#operator_at)|Pobiera element z tablicy.|  
|[CSimpleArray::operator =](#operator_eq)|Operator przypisania.|  

  
## <a name="remarks"></a>Uwagi  
 `CSimpleArray` udostępnia metody do tworzenia i zarządzania proste tablica danego typu `T`.  
  
 Parametr `TEqual` umożliwia definiowanie funkcję porównania dla dwóch elementów typu `T`. Tworząc podobny do klasy [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md), można zmienić zachowanie testu równości dla dowolnej podanej tablicy. Na przykład podczas pracy nad tablicy wskaźników, może być przydatne do definiowania równości w zależności od wartości, które odwołują się wskaźniki. Domyślna implementacja używa **operator=()**.  
  
 Zarówno `CSimpleArray` i [CSimpleMap](../../atl/reference/csimplemap-class.md) są przeznaczone dla niewielkiej liczby elementów. [CAtlArray](../../atl/reference/catlarray-class.md) i [CAtlMap](../../atl/reference/catlmap-class.md) powinna być używana, gdy tablica zawiera dużą liczbę elementów.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsimpcoll.h  
  
## <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#86](../../atl/codesnippet/cpp/csimplearray-class_1.cpp)]  
  
##  <a name="add"></a>  CSimpleArray::Add  
 Dodaje nowy element do tablicy.  
  
```
BOOL Add(const T& t);
```  
  
### <a name="parameters"></a>Parametry  
 *t*  
 Element, aby dodać do tablicy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli element został pomyślnie dodany do tablicy, wartość FALSE w przeciwnym razie wartość.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#87](../../atl/codesnippet/cpp/csimplearray-class_2.cpp)]  
  
##  <a name="csimplearray"></a>  CSimpleArray::CSimpleArray  
 Konstruktor dla obiekt array.  
  
```
CSimpleArray(const CSimpleArray<T, TEqual>& src);  
CSimpleArray();
```     
  
### <a name="parameters"></a>Parametry  
 *src*  
 Istniejące `CSimpleArray` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Inicjuje elementy członkowskie danych, tworzenie nowych pusta `CSimpleArray` obiektu lub kopię istniejącej `CSimpleArray` obiektu.  
  
##  <a name="dtor"></a>  CSimpleArray:: ~ CSimpleArray  
 Destruktor.  
  
```
~CSimpleArray();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie przydzielone zasoby.  
  
##  <a name="find"></a>  CSimpleArray::Find  
 Odnajduje element w tablicy.  
  
```
int Find(const T& t) const;
```  
  
### <a name="parameters"></a>Parametry  
 *t*  
 Element do wyszukania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca indeks znaleziony element lub wartość -1, jeśli element nie zostanie znaleziony.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#88](../../atl/codesnippet/cpp/csimplearray-class_3.cpp)]  
  
##  <a name="getdata"></a>  CSimpleArray::GetData  
 Zwraca wskaźnik do danych przechowywanych w tablicy.  
  
```
T* GetData() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do danych w tablicy.  
  
##  <a name="getsize"></a>  CSimpleArray::GetSize  
 Zwraca liczbę elementów przechowywane w tablicy.  
  
```
int GetSize() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę elementów przechowywane w tablicy.  
  
##  <a name="operator_at"></a>  CSimpleArray::operator \[\]  
 Pobiera element z tablicy.  
  
```
T& operator[](int nindex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Indeks elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca element tablicy odwołuje się `nIndex`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#89](../../atl/codesnippet/cpp/csimplearray-class_4.cpp)]  
  
##  <a name="operator_eq"></a>  CSimpleArray::operator =  
 Operator przypisania.  
  
```
CSimpleArray<T, TEqual>
& operator=(
    const CSimpleArray<T, TEqual>& src);
```  
  
### <a name="parameters"></a>Parametry  
 *src*  
 Tablica do skopiowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do zaktualizowanego `CSimpleArray` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Kopiuje wszystkie elementy z `CSimpleArray` zawiera odwołanie do obiektu *src* do bieżącego obiektu tablicy zastąpienie wszystkich istniejących danych.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#90](../../atl/codesnippet/cpp/csimplearray-class_5.cpp)]  
  
##  <a name="remove"></a>  CSimpleArray::Remove  
 Usuwa określonego elementu z tablicy.  
  
```
BOOL Remove(const T& t);
```  
  
### <a name="parameters"></a>Parametry  
 *t*  
 Element, aby usunąć z tablicy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli element jest znaleziono i usunięty, wartość FALSE w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Po usunięciu elementu pozostałych elementów w tablicy są numerowane do wypełnienia pustego miejsca.  
  
##  <a name="removeall"></a>  CSimpleArray::RemoveAll  
 Usuwa wszystkie elementy z tablicy.  
  
```
void RemoveAll();
```  
  
### <a name="remarks"></a>Uwagi  
 Usuwa wszystkie elementy przechowywane w tablicy.  
  
##  <a name="removeat"></a>  CSimpleArray::RemoveAt  
 Usuwa określony element z tablicy.  
  
```
BOOL RemoveAtint nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Indeks wskazuje element do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli element został usunięty, wartość FALSE, jeśli indeks jest nieprawidłowy.  
  
### <a name="remarks"></a>Uwagi  
 Po usunięciu elementu pozostałych elementów w tablicy są numerowane do wypełnienia pustego miejsca.  
  
##  <a name="setatindex"></a>  CSimpleArray::SetAtIndex  
 Ustaw określony element w tablicy.  
  
```
BOOL SetAtIndex(
    int nIndex,
    const T& t);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Indeks elementu do zmiany.  
  
 *t*  
 Wartość do przypisania do określonego elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli powodzenia lub wartość FALSE Jeśli indeks jest nieprawidłowy.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
