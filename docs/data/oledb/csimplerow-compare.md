---
title: CSimpleRow::Compare | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleRow.Compare
- CSimpleRow::Compare
dev_langs:
- C++
helpviewer_keywords:
- Compare method
ms.assetid: 0bb65f09-c7bc-449b-aa4e-c828cac13510
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2649fcf708abaf9e971490d3e88a746c264b1009
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="csimplerowcompare"></a>CSimpleRow::Compare
Porównuje dwa wiersze, aby zobaczyć, czy odnoszą się do tego samego wystąpienia wiersza.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Compare(CSimpleRow* pRow);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRow`  
 Wskaźnik do `CSimpleRow` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT` Wartości zwykle `S_OK`, wskazując dwa wiersze są tego samego wystąpienia wiersza lub **S_FALSE**, wskazującą dwa wiersze są różne. Zobacz [IRowsetIdentity::IsSameRow](https://msdn.microsoft.com/en-us/library/ms719629.aspx) w *OLE DB Podręcznik programisty* dla innych możliwych wartości zwracanych.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Csimplerow — klasa](../../data/oledb/csimplerow-class.md)   
 [CSimpleRow::ReleaseRow](../../data/oledb/csimplerow-releaserow.md)   
 [IRowsetImpl::RefRows](../../data/oledb/irowsetimpl-refrows.md)