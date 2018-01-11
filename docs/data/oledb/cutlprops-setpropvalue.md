---
title: CUtlProps::SetPropValue | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SetPropValue
- ATL::CUtlProps<T>::SetPropValue
- ATL.CUtlProps<T>.SetPropValue
- ATL.CUtlProps.SetPropValue
- CUtlProps::SetPropValue
- CUtlProps<T>::SetPropValue
- CUtlProps.SetPropValue
- CUtlProps<T>.SetPropValue
- ATL::CUtlProps::SetPropValue
dev_langs: C++
helpviewer_keywords: SetPropValue method
ms.assetid: 69a703c0-f640-4ca3-8850-0c4e75d52429
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 389aa22addcc293131c5b4a1c60aa2601b354f3f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cutlpropssetpropvalue"></a>CUtlProps::SetPropValue
Ustawia właściwość w zestawie właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      HRESULT SetPropValue(  
   const GUID* pguidPropSet,  
   DBPROPID dwPropId,  
   VARIANT* pvValue   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pguidPropSet`  
 [in] Identyfikator GUID zestawu właściwości.  
  
 `dwPropId`  
 [in] Indeks właściwości.  
  
 `pvValue`  
 [in] Wskaźnik do typ variant zawierający nowa wartość właściwości.  
  
## <a name="return-value"></a>Wartość zwracana  
 `Failure`w przypadku awarii i `S_OK` w przypadku powodzenia.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [CUtlProps, klasa](../../data/oledb/cutlprops-class.md)