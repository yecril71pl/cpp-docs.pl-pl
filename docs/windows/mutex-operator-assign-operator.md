---
title: Mutex::operator = — Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: 9b0ee206-a930-4fea-8dc0-1f79839e9d13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8791d3c947206be399f475bb8c895b2b5e032133
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875490"
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