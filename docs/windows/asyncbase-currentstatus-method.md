---
title: "AsyncBase::CurrentStatus — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::CurrentStatus
dev_langs: C++
helpviewer_keywords: CurrentStatus method
ms.assetid: 26ee4c4a-6525-4a5f-b49c-3ca40c365eb6
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b70974d4d53c819d1cf614660c53df0a75510482
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="asyncbasecurrentstatus-method"></a>AsyncBase::CurrentStatus — Metoda
Pobiera stan bieżącego operację asynchroniczną.  
  
## <a name="syntax"></a>Składnia  
  
```  
inline void CurrentStatus(  
   Details::AsyncStatusInternal *status  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `status`  
 Lokalizacja, w którym ta operacja przechowuje przy bieżącym stanie.  
  
## <a name="remarks"></a>Uwagi  
 Ta operacja jest bezpieczne wątkowo.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Asyncbase — klasa](../windows/asyncbase-class.md)   
 [Asyncstatusinternal — wyliczenie](../windows/asyncstatusinternal-enumeration.md)