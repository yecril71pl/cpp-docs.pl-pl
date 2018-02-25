---
title: CRowset::IsSameRow | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRowset::IsSameRow
- CRowset.IsSameRow
- IsSameRow
- ATL::CRowset::IsSameRow
- ATL.CRowset.IsSameRow
- CRowset<TAccessor>::IsSameRow
- ATL.CRowset<TAccessor>.IsSameRow
- CRowset<TAccessor>.IsSameRow
- ATL::CRowset<TAccessor>::IsSameRow
dev_langs:
- C++
helpviewer_keywords:
- IsSameRow method
ms.assetid: 53cba847-52f5-4dd9-973f-bbe7454c425c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b43788e1c64df3db223aa02df53014d3871b4c71
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="crowsetissamerow"></a>CRowset::IsSameRow
Porównuje określony wiersz z bieżącego wiersza.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT IsSameRow(HROW hRow) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `hRow`  
 [in] Dojście do wiersza do porównania z bieżącym wierszem.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`. `S_OK` Wskazuje, że wiersze są takie same. Dla innych wartości [IRowsetIndentity::IsSameRow](https://msdn.microsoft.com/en-us/library/ms719629.aspx) w *OLE DB Podręcznik programisty* w zestawie Windows SDK.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CRowset, klasa](../../data/oledb/crowset-class.md)