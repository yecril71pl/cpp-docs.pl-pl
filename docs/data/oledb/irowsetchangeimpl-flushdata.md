---
title: IRowsetChangeImpl::FlushData | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetChangeImpl::FlushData
- IRowsetChangeImpl.FlushData
- FlushData
dev_langs: C++
helpviewer_keywords: FlushData method
ms.assetid: fd4bc73b-bc25-4aab-90d5-0bed92670c88
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 565b971b53ddb0a50b276d76aaaf62e9f7fa39f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="irowsetchangeimplflushdata"></a>IRowsetChangeImpl::FlushData
Overidden przez dostawcę, aby przekazać do magazynu danych.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      HRESULT FlushData(  
   HROW hRowToFlush,  
   HACCESSOR hAccessorToFlush   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *hRowToFlush*  
 [in] Dojście do wierszy danych. Typ tego wiersza zależy od *RowClass* argumentu szablonu `IRowsetImpl` klasy (`CSimpleRow` domyślnie).  
  
 *hAccessorToFlush*  
 [in] Dojście do metody dostępu, który zawiera informacje o powiązaniu i informacje o typie w jego **PROVIDER_MAP** (zobacz [iaccessorimpl —](../../data/oledb/iaccessorimpl-class.md)).  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [IRowsetChangeImpl, klasa](../../data/oledb/irowsetchangeimpl-class.md)