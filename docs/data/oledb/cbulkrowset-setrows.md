---
title: CBulkRowset::SetRows | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CBulkRowset.SetRows
- CBulkRowset::SetRows
- CBulkRowset<TAccessor>.SetRows
- ATL.CBulkRowset<TAccessor>.SetRows
- CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset::SetRows
- CBulkRowset.SetRows
- SetRows
dev_langs:
- C++
helpviewer_keywords:
- SetRows method
ms.assetid: 7e92312a-bfd0-4c24-a799-62bef663f28e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fa6305139e554c164f01acf74b78c069e1d030db
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cbulkrowsetsetrows"></a>CBulkRowset::SetRows
Ustawia liczbę pobierane przez każde wywołanie dojść do wierszy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      void SetRows(DBROWCOUNT nRows) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `nRows`  
 [in] Nowy rozmiar wierszy (liczba wierszy).  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wywołanie tej funkcji, należy przed otwarciem zestawu wierszy.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CBulkRowset, klasa](../../data/oledb/cbulkrowset-class.md)