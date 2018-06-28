---
title: RuntimeClass::GetIids — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::GetIids
dev_langs:
- C++
helpviewer_keywords:
- GetIids method
ms.assetid: 826a67d1-ebc4-4940-b5d5-7cd66885e4a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c309c97b9c9ce057ca67ab4b5d729c61d803ea5a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33888428"
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
 [RuntimeClass, klasa](../windows/runtimeclass-class.md)