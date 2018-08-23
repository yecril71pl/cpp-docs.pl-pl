---
title: Cbulkrowset — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CBulkRowset
- ATL.CBulkRowset
- ATL::CBulkRowset<TAccessor>
- CBulkRowset
- ATL.CBulkRowset<TAccessor>
- CBulkRowset::AddRefRows
- AddRefRows
- CBulkRowset.AddRefRows
- ATL.CBulkRowset<TAccessor>.AddRefRows
- ATL::CBulkRowset::AddRefRows
- CBulkRowset<TAccessor>::AddRefRows
- ATL.CBulkRowset.AddRefRows
- ATL::CBulkRowset<TAccessor>::AddRefRows
- ATL.CBulkRowset<TAccessor>.CBulkRowset
- ATL::CBulkRowset::CBulkRowset
- CBulkRowset.CBulkRowset
- CBulkRowset::CBulkRowset
- ATL.CBulkRowset.CBulkRowset
- ATL::CBulkRowset<TAccessor>::CBulkRowset
- CBulkRowset<TAccessor>::CBulkRowset
- CBulkRowset
- ATL.CBulkRowset.MoveFirst
- CBulkRowset<TAccessor>.MoveFirst
- ATL.CBulkRowset<TAccessor>.MoveFirst
- ATL::CBulkRowset::MoveFirst
- ATL::CBulkRowset<TAccessor>::MoveFirst
- CBulkRowset::MoveFirst
- CBulkRowset<TAccessor>::MoveFirst
- CBulkRowset.MoveFirst
- CBulkRowset.MoveLast
- ATL.CBulkRowset.MoveLast
- ATL::CBulkRowset<TAccessor>::MoveLast
- CBulkRowset::MoveLast
- CBulkRowset<TAccessor>.MoveLast
- ATL::CBulkRowset::MoveLast
- ATL.CBulkRowset<TAccessor>.MoveLast
- CBulkRowset<TAccessor>::MoveLast
- MoveLast
- ATL.CBulkRowset<TAccessor>.MoveNext
- ATL::CBulkRowset::MoveNext
- CBulkRowset::MoveNext
- ATL.CBulkRowset.MoveNext
- CBulkRowset.MoveNext
- ATL::CBulkRowset<TAccessor>::MoveNext
- CBulkRowset<TAccessor>.MoveNext
- CBulkRowset<TAccessor>::MoveNext
- CBulkRowset::MovePrev
- MovePrev
- CBulkRowset<TAccessor>::MovePrev
- ATL::CBulkRowset<TAccessor>::MovePrev
- CBulkRowset<TAccessor>.MovePrev
- ATL::CBulkRowset::MovePrev
- CBulkRowset.MovePrev
- ATL.CBulkRowset.MovePrev
- ATL.CBulkRowset<TAccessor>.MovePrev
- CBulkRowset<TAccessor>::MoveToBookmark
- CBulkRowset.MoveToBookmark
- MoveToBookmark
- ATL.CBulkRowset.MoveToBookmark
- CBulkRowset::MoveToBookmark
- ATL::CBulkRowset<TAccessor>::MoveToBookmark
- ATL::CBulkRowset::MoveToBookmark
- CBulkRowset.MoveToRatio
- ATL::CBulkRowset::MoveToRatio
- MoveToRatio
- CBulkRowset::MoveToRatio
- ATL.CBulkRowset<TAccessor>.MoveToRatio
- ATL::CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset.MoveToRatio
- CBulkRowset<TAccessor>::MoveToRatio
- ReleaseRows
- ATL.CBulkRowset<TAccessor>.ReleaseRows
- ATL::CBulkRowset<TAccessor>::ReleaseRows
- ATL.CBulkRowset.ReleaseRows
- CBulkRowset<TAccessor>::ReleaseRows
- ATL::CBulkRowset::ReleaseRows
- CBulkRowset::ReleaseRows
- CBulkRowset.ReleaseRows
- ATL.CBulkRowset.SetRows
- CBulkRowset::SetRows
- CBulkRowset<TAccessor>.SetRows
- ATL.CBulkRowset<TAccessor>.SetRows
- CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset::SetRows
- CBulkRowset.SetRows
- SetRows
dev_langs:
- C++
helpviewer_keywords:
- CBulkRowset class
- AddRefRows method
- CBulkRowset class, constructor
- MoveFirst method
- MoveLast method
- MoveNext method
- MovePrev method
- MoveToBookmark method
- MoveToRatio method
- ReleaseRows method
- SetRows method
ms.assetid: c6bde426-c543-4022-a98a-9519d9e2ae59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e741055950449ea07c719cf6cd4c33a34d6f43b3
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42466346"
---
# <a name="cbulkrowset-class"></a>CBulkRowset — Klasa
Pobiera i obsługuje wiersze, aby pracować nad dane zbiorcze Pobieranie wielu dojść do wierszy za pomocą jednego wywołania.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class TAccessor>  
class CBulkRowset : public CRowset<TAccessor>  
```  
  
### <a name="parameters"></a>Parametry  
 *TAccessor*  
 Klasa metody dostępu.  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Addrefrows —](#addrefrows)|Zwiększa liczbę odwołań.|  
|[CBulkRowset](#cbulkrowset)|Konstruktor.|  
|[MoveFirst](#movefirst)|Pobiera pierwszy wiersz danych, wykonywanie nowych pobierania zbiorczego w razie potrzeby.|  
|[MoveLast](#movelast)|Przenosi do ostatniego wiersza.|  
|[MoveNext](#movenext)|Pobiera następny wiersz danych.|  
|[Moveprev —](#moveprev)|Przenosi do poprzedniego wiersza.|  
|[Movetobookmark —](#movetobookmark)|Pobiera zakładki lub wiersz w określonym przesunięciu z tej zakładki.|  
|[MoveToRatio](#movetoratio)|Pobiera wiersze, rozpoczynając od ułamków pozycji w zestawie wierszy.|  
|[Releaserows —](#releaserows)|Ustawia bieżący wiersz (`m_nCurrentRow`) do zera i zwalnia wszystkie wiersze.|  
|[Setrows —](#setrows)|Ustawia liczbę dojść do wierszy mają zostać pobrane przez jedno wywołanie.|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie `CBulkRowset` klasy.  
  
 [!code-cpp[NVC_OLEDB_Consumer#1](../../data/oledb/codesnippet/cpp/cbulkrowset-class_1.cpp)]  

## <a name="addrefrows"></a> CBulkRowset::AddRefRows
Wywołania [IRowset::AddRefRows](/previous-versions/windows/desktop/ms719619\(v=vs.85\)) Aby zwiększyć licznik odwołań dla wszystkich wierszy, które obecnie są pobierane z zestawu wierszy bulk.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT AddRefRows() throw();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa HRESULT. 
  
## <a name="cbulkrowset"></a> CBulkRowset::CBulkRowset
Tworzy nową `CBulkRowset` obiektu i ustawia domyślną liczbę wierszy do 10.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
CBulkRowset();  
```  

## <a name="movefirst"></a> CBulkRowset::MoveFirst
Pobiera pierwszy wiersz danych.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT MoveFirst() throw();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa HRESULT.

## <a name="movelast"></a> CBulkRowset::MoveLast
Przenosi do ostatniego wiersza.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT MoveLast() throw();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa HRESULT.  

## <a name="movenext"></a> CBulkRowset::MoveNext
Pobiera następny wiersz danych.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT MoveNext() throw();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa HRESULT. Zwraca DB_S_ENDOFROWSET, gdy zostanie osiągnięty koniec zestawu wierszy. 

## <a name="moveprev"></a> CBulkRowset::MovePrev
Przenosi do poprzedniego wiersza.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT MovePrev() throw();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa HRESULT.  

## <a name="movetobookmark"></a> CBulkRowset::MoveToBookmark
Pobiera wiersz oznaczone przez zakładki lub wiersz w określonym przesunięciu (*lSkip*) z tej zakładki.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT MoveToBookmark(const CBookmarkBase& bookmark, 
   DBCOUNTITEM lSkip = 0) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *Zakładka*  
 [in] Zakładka, oznaczanie lokalizacji, z którego chcesz pobrać dane.  
  
 *lSkip*  
 [in] Liczbę wierszy z zakładki, aby wiersz docelowy. Jeśli *lSkip* wynosi zero, pierwszy wiersz pobrania jest zakładką wiersza. Jeśli *lSkip* wynosi 1, pierwszy wiersz pobrania jest wiersz po wierszu zakładką. Jeśli *lSkip* wynosi -1, pierwszy wiersz pobrania jest wierszy przed wierszem zakładką.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zobacz [IRowset::GetData](/previous-versions/windows/desktop/ms716988\(v=vs.85\)) w *OLE DB Podręcznik programisty*. 

## <a name="movetoratio"></a> CBulkRowset::MoveToRatio
Pobiera wiersze, rozpoczynając od ułamków pozycji w zestawie wierszy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT MoveToRatio(DBCOUNTITEM nNumerator, 
   DBCOUNTITEM nDenominator)throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *nNumerator*  
 [in] Licznik używany do określenia pozycji ułamkowych, z którego można pobrać danych.  
  
 *nDenominator*  
 [in] Denominator, używany do określenia pozycji ułamkowych, z którego można pobrać danych.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 `MoveToRatio` Pobiera wiersze około zgodnie z następującą formułę:  
  
 `(nNumerator *  RowsetSize ) / nDenominator`  
  
 Gdzie `RowsetSize` jest rozmiar wierszy, mierzone w wierszach. Dokładność tę formułę, zależy od określonego dostawcy. Aby uzyskać więcej informacji, zobacz [IRowsetScroll::GetRowsAtRatio](/previous-versions/windows/desktop/ms709602\(v=vs.85\)) w *OLE DB Podręcznik programisty*.   

## <a name="releaserows"></a> CBulkRowset::ReleaseRows
Wywołania [IRowset::ReleaseRows](/previous-versions/windows/desktop/ms719771\(v=vs.85\)) na liczbę odwołań we wszystkich wierszach, które obecnie są pobierane z zestawu wierszy bulk.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT ReleaseRows() throw();   
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa HRESULT.  

## <a name="setrows"></a> CBulkRowset::SetRows
Ustawia liczbę dojść do wierszy pobierane przez każde wywołanie.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
void SetRows(DBROWCOUNT nRows) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *nRows*  
 [in] Nowy rozmiar wierszy (liczba wierszy).  
  
### <a name="remarks"></a>Uwagi  
 Jeśli chcesz wywołać tę funkcję, należy przed otwarciem zestawu wierszy.
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)