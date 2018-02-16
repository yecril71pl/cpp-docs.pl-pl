---
title: "Cbulkrowset — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CBulkRowset
- ATL.CBulkRowset
- ATL::CBulkRowset<TAccessor>
- CBulkRowset
- ATL.CBulkRowset<TAccessor>
dev_langs:
- C++
helpviewer_keywords:
- CBulkRowset class
ms.assetid: c6bde426-c543-4022-a98a-9519d9e2ae59
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 990178bf1a98ccd522755ce82eae229558fb7747
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="cbulkrowset-class"></a>CBulkRowset — Klasa
Pobiera i manipuluje wiersze, aby pracować nad dane zbiorcze Pobieranie wielu dojść do wierszy przy użyciu jednego wywołania.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class TAccessor>  
class CBulkRowset : public CRowset<TAccessor>  
```  
  
#### <a name="parameters"></a>Parametry  
 `TAccessor`  
 Klasa metody dostępu.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[AddRefRows](../../data/oledb/cbulkrowset-addrefrows.md)|Zwiększa liczbę odwołania.|  
|[CBulkRowset](../../data/oledb/cbulkrowset-cbulkrowset.md)|Konstruktor.|  
|[MoveFirst](../../data/oledb/cbulkrowset-movefirst.md)|Pobiera pierwszy wiersz danych wykonywania nowych pobierania zbiorczego w razie potrzeby.|  
|[MoveLast](../../data/oledb/cbulkrowset-movelast.md)|Przenosi do ostatniego wiersza.|  
|[MoveNext](../../data/oledb/cbulkrowset-movenext.md)|Pobiera następnego wiersza danych.|  
|[MovePrev](../../data/oledb/cbulkrowset-moveprev.md)|Przenosi do poprzedniego wiersza.|  
|[MoveToBookmark](../../data/oledb/cbulkrowset-movetobookmark.md)|Pobiera wiersza zakładki lub wiersza od określonego przesunięcia z tej zakładki.|  
|[MoveToRatio](../../data/oledb/cbulkrowset-movetoratio.md)|Pobiera wiersze, zaczynając od pozycji ułamkowych w zestawie wierszy.|  
|[ReleaseRows](../../data/oledb/cbulkrowset-releaserows.md)|Ustawia bieżący wiersz (**m_nCurrentRow**) do zera i zwalnia wszystkie wiersze.|  
|[SetRows](../../data/oledb/cbulkrowset-setrows.md)|Ustawia liczbę dojść do wierszy mają zostać pobrane przez jedno wywołanie.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `CBulkRowset` klasy.  
  
 [!code-cpp[NVC_OLEDB_Consumer#1](../../data/oledb/codesnippet/cpp/cbulkrowset-class_1.cpp)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)