---
title: CRowset::GetDataHere | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRowset<TAccessor>::GetDataHere
- CRowset<TAccessor>.GetDataHere
- CRowset.GetDataHere
- GetDataHere
- CRowset::GetDataHere
- ATL::CRowset::GetDataHere
- ATL::CRowset<TAccessor>::GetDataHere
- ATL.CRowset<TAccessor>.GetDataHere
- ATL.CRowset.GetDataHere
dev_langs:
- C++
helpviewer_keywords:
- GetDataHere method
ms.assetid: 2fe2a987-1c4c-4299-876e-0591caf63af4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bcd5a70702a2b38fcdc97b431bfdd29a01c60ddf
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="crowsetgetdatahere"></a>CRowset::GetDataHere
Pobiera dane z bieżącego wiersza i umieszcza je w buforze określona.  
  
## <a name="syntax"></a>Składnia  
  
```
HRESULT GetDataHere(int nAccessor,   
  void* pBuffer) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `nAccessor`  
 [in] Numer indeksu dostępu do użycia na potrzeby uzyskiwania dostępu do danych.  
  
 `pBuffer`  
 [out] Bufor do której mają zostać umieszczone dane dla bieżącego rekordu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Na przykład sposobu używania tej funkcji, zobacz [MultiRead próbki](../../visual-cpp-samples.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Crowset — klasa](../../data/oledb/crowset-class.md)   
 [CRowset::GetData](../../data/oledb/crowset-getdata.md)