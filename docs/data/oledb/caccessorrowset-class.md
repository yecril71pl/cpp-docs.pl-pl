---
title: "Caccessorrowset — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAccessorRowset
- ATL.CAccessorRowset
- ATL::CAccessorRowset
dev_langs:
- C++
helpviewer_keywords:
- CAccessorRowset class
ms.assetid: bd4f58ed-cebf-4d43-8985-1e5fcbf06953
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9da490873c14ea04f55f223e38009ac1952fe6d0
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="caccessorrowset-class"></a>CAccessorRowset — Klasa
Hermetyzuje zestawu wierszy i jego skojarzony metod dostępu w jednej klasy.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class TAccessor = CNoAccessor, 
          template <typename T> class TRowset = CRowset>  
class CAccessorRowset : public TAccessor, public TRowset<TAccessor>  
```  
  
#### <a name="parameters"></a>Parametry  
 `TAccessor`  
 Klasa metody dostępu.  
  
 `TRowset`  
 Klasy zestawu wierszy.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[BIND](../../data/oledb/caccessorrowset-bind.md)|Tworzy powiązania (używane podczas **bBind** jest określony jako wartość false w [CCommand::Open](../../data/oledb/ccommand-open.md)).|  
|[CAccessorRowset](../../data/oledb/caccessorrowset-caccessorrowset.md)|Konstruktor.|  
|[Zamknij](../../data/oledb/caccessorrowset-close.md)|Zamyka zestawu wierszy i wszystkie metody dostępu.|  
|[FreeRecordMemory](../../data/oledb/caccessorrowset-freerecordmemory.md)|Zwalnia wszystkie kolumny w bieżącego rekordu, który musi zostać zwolniony.|  
|[GetColumnInfo](../../data/oledb/caccessorrowset-getcolumninfo.md)|Implementuje [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx).|  
  
## <a name="remarks"></a>Uwagi  
 Klasa `TAccessor` zarządza metodzie dostępu. Klasa *TRowset* zarządza zestawu wierszy.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)