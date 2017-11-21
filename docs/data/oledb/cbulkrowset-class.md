---
title: "Cbulkrowset — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CBulkRowset
- ATL.CBulkRowset
- ATL::CBulkRowset<TAccessor>
- CBulkRowset
- ATL.CBulkRowset<TAccessor>
dev_langs: C++
helpviewer_keywords: CBulkRowset class
ms.assetid: c6bde426-c543-4022-a98a-9519d9e2ae59
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7208e2ecda79cf175f234499f6e69550693f182f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cbulkrowset-class"></a>CBulkRowset — Klasa
Pobiera i manipuluje wiersze, aby pracować nad dane zbiorcze Pobieranie wielu dojść do wierszy przy użyciu jednego wywołania.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|[Cbulkrowset —](../../data/oledb/cbulkrowset-cbulkrowset.md)|Konstruktor.|  
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
 [Dokumentacja szablonów konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)