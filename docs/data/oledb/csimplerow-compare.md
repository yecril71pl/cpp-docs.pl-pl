---
title: CSimpleRow::Compare | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CSimpleRow.Compare
- CSimpleRow::Compare
dev_langs:
- C++
helpviewer_keywords:
- Compare method
ms.assetid: 0bb65f09-c7bc-449b-aa4e-c828cac13510
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 75d79e753f1f4af630c26ef07fbb7241576535ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098968"
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