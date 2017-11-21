---
title: "RuntimeClass::GetIids — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::RuntimeClass::GetIids
dev_langs: C++
helpviewer_keywords: GetIids method
ms.assetid: 826a67d1-ebc4-4940-b5d5-7cd66885e4a1
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d80e5ea7b068b1d362b46430a1c55f7ff6e620a5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="runtimeclassgetiids-method"></a>RuntimeClass::GetIids — Metoda
Pobiera tablicę, która może zawierać identyfikatory implementowane przez bieżący obiekt runtimeclass — interfejs.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDMETHOD(  
   GetIids  
)  
   (_Out_ ULONG *iidCount,   
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);  
```  
  
#### <a name="parameters"></a>Parametry  
 `iidCount`  
 Po zakończeniu tej operacji, całkowita liczba elementów w tablicy `iids`.  
  
 `iids`  
 Po tej operacji zakończeniu wskaźnika do tablicy identyfikatorów interfejsu.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie E_OUTOFMEMORY.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Runtimeclass — klasa](../windows/runtimeclass-class.md)