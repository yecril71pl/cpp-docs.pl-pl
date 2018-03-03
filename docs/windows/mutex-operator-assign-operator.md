---
title: "Mutex::operator = — Operator | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: 9b0ee206-a930-4fea-8dc0-1f79839e9d13
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 23526911a2d9e723455a7d846bdaafb2dbefd45a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mutexoperator-operator"></a>Mutex::operator= Operator
Przypisuje (przenosi) określonego obiektu Mutex obiekt do bieżącego obiektu Mutex.  
  
## <a name="syntax"></a>Składnia  
  
```  
Mutex& operator=(  
   _Inout_ Mutex&& h  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `h`  
 R-wartości — odwołanie do obiektu Mutex.  
  
## <a name="return-value"></a>Wartość zwracana  
 Odwołanie do bieżącego obiektu Mutex.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz **Przenieś semantyki** sekcji [deklarator odwołania do r-wartości: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —
 
 ## <a name="see-also"></a>Zobacz też
 [Mutex — klasa](../windows/mutex-class1.md)