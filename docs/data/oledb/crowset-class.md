---
title: Klasa CRowset | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CRowset<TAccessor>
- CRowset
- ATL::CRowset
- ATL::CRowset<TAccessor>
- ATL.CRowset
dev_langs:
- C++
helpviewer_keywords:
- CRowset class
ms.assetid: b0228a90-b8dd-47cc-b397-8d4c15c1e7f4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ef4ec2851365d9fbabab6819a0883b6a9b660f28
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="crowset-class"></a>Klasa CRowset
Hermetyzuje obiektu zestawu wierszy OLE DB i kilka powiązane interfejsy i dostarcza metod manipulowania wierszy danych.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class TAccessor = CAccessorBase>  
class CRowset  
```  
  
#### <a name="parameters"></a>Parametry  
 `TAccessor`  
 Klasa metody dostępu. Wartość domyślna to `CAccessorBase`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[AddRefRows](../../data/oledb/crowset-addrefrows.md)|Zwiększa liczbę odwołań powiązane z bieżącego wiersza.|  
|[Zamknij](../../data/oledb/crowset-close.md)|Zwalnia wierszy i obecnie `IRowset` interfejsu.|  
|[Porównaj](../../data/oledb/crowset-compare.md)|Porównuje dwa zakładki przy użyciu [IRowsetLocate::Compare](https://msdn.microsoft.com/en-us/library/ms709539.aspx).|  
|[CRowset](../../data/oledb/crowset-crowset.md)|Tworzy nowy `CRowset` obiektu i (opcjonalnie) kojarzy ją z **IRowset** interfejs dostarczony jako parametr.|  
|[Usuń](../../data/oledb/crowset-delete.md)|Usuwa wiersze z zestawu wierszy przy użyciu [IRowsetChange:DeleteRows](https://msdn.microsoft.com/en-us/library/ms724362.aspx).|  
|[FindNextRow](../../data/oledb/crowset-findnextrow.md)|Wyszukuje następny zgodny wiersz po zakładką.|  
|[GetApproximatePosition](../../data/oledb/crowset-getapproximateposition.md)|Zwraca pozycję przybliżonej wiersz odpowiadający zakładki.|  
|[GetData](../../data/oledb/crowset-getdata.md)|Pobiera dane z kopii zestawu wierszy wiersza.|  
|[GetDataHere](../../data/oledb/crowset-getdatahere.md)|Pobiera dane z określonego bufora.|  
|[GetOriginalData](../../data/oledb/crowset-getoriginaldata.md)|Pobiera dane ostatnio pobrana z lub przesłana do źródła danych, ignorowanie oczekujące zmiany.|  
|[GetRowStatus](../../data/oledb/crowset-getrowstatus.md)|Zwraca informacje o stanie wszystkich wierszy.|  
|[Wstaw](../../data/oledb/crowset-insert.md)|Tworzy i wstawia nowy wiersz za pomocą [IRowsetChange:InsertRow](https://msdn.microsoft.com/en-us/library/ms716921.aspx).|  
|[IsSameRow](../../data/oledb/crowset-issamerow.md)|Porównuje określony wiersz z bieżącego wiersza.|  
|[MoveFirst](../../data/oledb/crowset-movefirst.md)|Zmiana lokalizacji pobierania dalej do pozycji początkowej.|  
|[MoveLast](../../data/oledb/crowset-movelast.md)|Przenosi do ostatniego rekordu.|  
|[MoveNext](../../data/oledb/crowset-movenext.md)|Pobiera dane z następnego wiersza sekwencyjnych lub określoną liczbę pozycji poza następnego wiersza.|  
|[MovePrev](../../data/oledb/crowset-moveprev.md)|Przenosi do poprzedniego rekordu.|  
|[MoveToBookmark](../../data/oledb/crowset-movetobookmark.md)|Pobiera wiersza zakładki lub wiersza od określonego przesunięcia z tej zakładki.|  
|[MoveToRatio](../../data/oledb/crowset-movetoratio.md)|Pobiera wiersze, zaczynając od pozycji ułamkowych w zestawie wierszy.|  
|[ReleaseRows](../../data/oledb/crowset-releaserows.md)|Wywołania [IRowset::ReleaseRows](https://msdn.microsoft.com/en-us/library/ms719771.aspx) zwolnienia dojście do bieżącego wiersza.|  
|[SetData](../../data/oledb/crowset-setdata.md)|Ustawia wartości danych w jednej lub kilku kolumn, używając wiersza [IRowsetChange:SetData](https://msdn.microsoft.com/en-us/library/ms721232.aspx).|  
|[Cofnij](../../data/oledb/crowset-undo.md)|Cofa zmiany wprowadzone od czasu ostatniego pobrania wiersza lub [aktualizacji](../../data/oledb/crowset-update.md).|  
|[Aktualizacja](../../data/oledb/crowset-update.md)|Wysyła wszystkie oczekujące zmiany do bieżącego wiersza od czasu ostatniego pobrania lub aktualizacji.|  
|[UpdateAll](../../data/oledb/crowset-updateall.md)|Wysyła wszystkie oczekujące zmiany do wszystkich wierszy od czasu ostatniego pobrania lub aktualizacji.|  
  
## <a name="remarks"></a>Uwagi  
 W OLE DB zestawu wierszy jest obiekt, za pomocą którego program ustawia i pobiera dane.  
  
 Ta klasa nie jest przeznaczona do wystąpienia, ale raczej przekazany jako parametr szablonu w celu `CTable` lub `CCommand` (`CRowset` jest ustawieniem domyślnym).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe DBViewer](../../visual-cpp-samples.md)   
 [Przykładowe multiRead](../../visual-cpp-samples.md)   
 [Przykładowe multiRead atrybutów](../../visual-cpp-samples.md)   
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)