---
title: CUtlProps::GetPropValue | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CUtlProps::GetPropValue
- CUtlProps.GetPropValue
- GetPropValue
dev_langs:
- C++
helpviewer_keywords:
- GetPropValue method
ms.assetid: 9a3fbadb-7814-48f7-96a4-b960fc4ecf2e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 00f56c317f9325fa51f7165fc3872b1e4ca6e9da
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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