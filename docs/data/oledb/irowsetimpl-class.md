---
title: "Irowsetimpl — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetImpl
dev_langs:
- C++
helpviewer_keywords:
- IRowsetImpl class
ms.assetid: 6a9189af-7556-45b1-adcb-9d62bb36704c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 54b9fd321c4240e9ba02cc63d809a492ffa4d439
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetimpl-class"></a>IRowsetImpl — Klasa
Udostępnia implementację elementu `IRowset` interfejsu.  
  
## <a name="syntax"></a>Składnia

```cpp
template <  
   class T,   
   class RowsetInterface,  
   class RowClass = CSimpleRow,  
   class MapClass = CAtlMap <  
      RowClass::KeyType,  
      RowClass*>>  
class ATL_NO_VTABLE IRowsetImpl : public RowsetInterface  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `IRowsetImpl`.  
  
 `RowsetInterface`  
 Klasa pochodna od `IRowsetImpl`.  
  
 `RowClass`  
 Jednostki magazynu dla **HROW**.  
  
 `MapClass`  
 Jednostki magazynu dla wszystkich dojść do wierszy posiadanych przez dostawcę.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)|Dodaje liczba odwołań do istniejących uchwyt wiersza.|  
|[CreateRow](../../data/oledb/irowsetimpl-createrow.md)|Wywoływane przez [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) można przydzielić nowego **HROW**. Nie należy wywoływać bezpośrednio przez użytkownika.|  
|[GetData](../../data/oledb/irowsetimpl-getdata.md)|Pobiera dane z kopii zestawu wierszy wiersza.|  
|[GetDBStatus](../../data/oledb/irowsetimpl-getdbstatus.md)|Zwraca informacje o stanie dla określonego pola.|  
|[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)|Pobiera wiersze po kolei, pamiętaj o tym poprzedniej pozycji.|  
|[Irowsetimpl —](../../data/oledb/irowsetimpl-class.md)|Konstruktor. Nie należy wywoływać bezpośrednio przez użytkownika.|  
|[RefRows](../../data/oledb/irowsetimpl-refrows.md)|Wywoływane przez [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) i [ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md). Nie należy wywoływać bezpośrednio przez użytkownika.|  
|[ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md)|Wersje wierszy.|  
|[RestartPosition](../../data/oledb/irowsetimpl-restartposition.md)|Zmienia położenie dalej pozycji pobierania do pozycji początkowej; oznacza to utworzyć jej położenie podczas pierwszego zestawu wierszy.|  
|[SetDBStatus](../../data/oledb/irowsetimpl-setdbstatus.md)|Ustawia flagi stanu dla określonego pola.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|[m_bCanFetchBack](../../data/oledb/irowsetimpl-m-bcanfetchback.md)|Wskazuje, czy dostawca obsługuje pobieranie z poprzednimi wersjami.|  
|[m_bCanScrollBack](../../data/oledb/irowsetimpl-m-bcanscrollback.md)|Wskazuje, czy dostawca może mieć wstecz jego przewijania kursora.|  
|[m_bReset](../../data/oledb/irowsetimpl-m-breset.md)|Wskazuje, czy dostawca zresetował położeniu kursora. To ma specjalne znaczenie podczas przewijania wstecz lub pobieranie wstecz w [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md).|  
|[m_iRowset](../../data/oledb/irowsetimpl-m-irowset.md)|Indeks wierszy, reprezentujący kursora.|  
|[m_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md)|Listę dojść do wierszy.|  
  
## <a name="remarks"></a>Uwagi  
 [IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx) jest interfejs podstawowy zestaw wierszy.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)