---
title: CRowset::AddRefRows | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRowset<TAccessor>.AddRefRows
- CRowset.AddRefRows
- ATL.CRowset.AddRefRows
- AddRefRows
- CRowset::AddRefRows
- CRowset<TAccessor>::AddRefRows
- ATL::CRowset::AddRefRows
- ATL.CRowset<TAccessor>.AddRefRows
- ATL::CRowset<TAccessor>::AddRefRows
dev_langs:
- C++
helpviewer_keywords:
- AddRefRows method
ms.assetid: 590b5a24-870f-4c42-b0c8-28491f368a82
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fed7e6981f72c9698f38eb91022619b9ad1edfb9
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="crowsetaddrefrows"></a>CRowset::AddRefRows
Wywołania [IRowset::AddRefRows](https://msdn.microsoft.com/en-us/library/ms719619.aspx) do zwiększenia (jeden) liczebności referencyjnej skojarzone z bieżącym dojście do wiersza.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT AddRefRows() throw();  
  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwiększa liczbę odwołanie do bieżącego dojście do wiersza. Wywołanie [ReleaseRows](../../data/oledb/crowset-releaserows.md) zmniejszyć wartość licznika. Wiersze zwrócone przez metody move ma liczebności referencyjnej równej jeden.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Crowset — klasa](../../data/oledb/crowset-class.md)   
 [CRowset::ReleaseRows](../../data/oledb/crowset-releaserows.md)