---
title: "Irowsetchangeimpl — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::IRowsetChangeImpl
- IRowsetChangeImpl
- ATL.IRowsetChangeImpl
dev_langs:
- C++
helpviewer_keywords:
- providers, updatable
- updatable providers, immediate update
- IRowsetChangeImpl class
ms.assetid: 1e9fee15-ed9e-4387-af8f-215569beca6c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b289e20f4714503e0aef6deb2273f6cd12192e7d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl — Klasa
Szablony OLE DB stosowania [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx) interfejsu w specyfikacji OLE DB.  
  
## <a name="syntax"></a>Składnia

```cpp
template <  
   class T,   
   class Storage,   
   class BaseInterface = IRowsetChange,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>>  
class ATL_NO_VTABLE IRowsetChangeImpl : public BaseInterface  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Klasa pochodna od `IRowsetChangeImpl`.  
  
 `Storage`  
 Rekord użytkownika.  
  
 `BaseInterface`  
 Podstawowym klasy dla interfejsu, takich jak `IRowsetChange`.  
  
 `RowClass`  
 Jednostki magazynu na dojście wiersza.  
  
 `MapClass`  
 Jednostki magazynu dla wszystkich dojść do wierszy posiadanych przez dostawcę.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="interface-methods-used-with-irowsetchange"></a>Metody interfejsu (używane z IRowsetChange)  
  
|||  
|-|-|  
|[DeleteRows](../../data/oledb/irowsetchangeimpl-deleterows.md)|Usuwa wiersze z zestawu wierszy.|  
|[InsertRow](../../data/oledb/irowsetchangeimpl-insertrow.md)|Wstawia wiersz do zestawu wierszy.|  
|[SetData](../../data/oledb/irowsetchangeimpl-setdata.md)|Ustawia wartości danych w co najmniej jedną kolumnę.|  
  
### <a name="implementation-method-callback"></a>Implementacja metody (wywołanie zwrotne)  
  
|||  
|-|-|  
|[FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md)|Overidden przez dostawcę, aby przekazać do magazynu danych.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest odpowiedzialny za operacje natychmiastowego zapisu w magazynie danych. "Natychmiastowe" oznacza, że po użytkownika końcowego (osoba używająca konsumenta) żadnych zmian, zmiany te zostaną natychmiast przesłane do danych magazynu (i nie można cofnąć).  
  
 `IRowsetChangeImpl` implementuje OLE DB `IRowsetChange` interfejs, który umożliwia aktualizowania wartości kolumn w istniejących wierszy, usuwanie wierszy i wstawiania nowych wierszy.  
  
 Implementacja szablony OLE DB obsługuje wszystkie metody podstawowej (`SetData`, `InsertRow`, i `DeleteRows`).  
  
> [!IMPORTANT]
>  Zdecydowanie zaleca się przeczytanie następujących dokumentacji, przed przystąpieniem do implementowania dostawcy:  
  
-   [Tworzenie aktualizowalnego dostawcy](../../data/oledb/creating-an-updatable-provider.md)  
  
-   Rozdział 6 *OLE DB Podręcznik programisty*  
  
-   Zobacz też sposób `RUpdateRowset` klasa jest używana w przykładowym UpdatePV  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)