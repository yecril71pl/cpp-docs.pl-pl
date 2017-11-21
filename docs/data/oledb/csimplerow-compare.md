---
title: CSimpleRow::Compare | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CSimpleRow.Compare
- CSimpleRow::Compare
dev_langs: C++
helpviewer_keywords: Compare method
ms.assetid: 0bb65f09-c7bc-449b-aa4e-c828cac13510
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8e49dcc0356c563312c0d73041ab412716694c1a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="csimplerowcompare"></a>CSimpleRow::Compare
Porównuje dwa wiersze, aby zobaczyć, czy odnoszą się do tego samego wystąpienia wiersza.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      HRESULT Compare(   
   CSimpleRow* pRow    
);  
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