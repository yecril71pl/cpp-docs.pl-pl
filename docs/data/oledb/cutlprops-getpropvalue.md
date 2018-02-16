---
title: CUtlProps::GetPropValue | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CUtlProps::GetPropValue
- CUtlProps.GetPropValue
- GetPropValue
dev_langs:
- C++
helpviewer_keywords:
- GetPropValue method
ms.assetid: 9a3fbadb-7814-48f7-96a4-b960fc4ecf2e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c4e9ea040c9ec458f100beb4c9cd2516ac167052
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="cutlpropsgetpropvalue"></a>CUtlProps::GetPropValue
Pobiera właściwości z zestawu właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      OUT_OF_LINE HRESULT GetPropValue(const GUID* pguidPropSet,  
   DBPROPID dwPropId,  
   VARIANT* pvValue);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pguidPropSet`  
 [in] Identyfikator GUID zestawu właściwości.  
  
 `dwPropId`  
 [in] Indeks właściwości.  
  
 `pvValue`  
 [out] Wskaźnik do typ variant zawierający nowa wartość właściwości.  
  
## <a name="return-value"></a>Wartość zwracana  
 `Failure` w przypadku awarii i `S_OK` w przypadku powodzenia.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [CUtlProps, klasa](../../data/oledb/cutlprops-class.md)