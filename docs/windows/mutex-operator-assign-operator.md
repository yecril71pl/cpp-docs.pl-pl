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
ms.openlocfilehash: 837c8ed508b713f790d1a6a56310705a00f12b3f
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39602749"
---
# <a name="mutexoperator-operator"></a>Mutex::operator= Operator
Przypisuje (ruch) określonego **Mutex** obiekt do bieżącego **Mutex** obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
Mutex& operator=(  
   _Inout_ Mutex&& h  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *h*  
 Odwołania rvalue do **Mutex** obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Odwołanie do bieżącego **Mutex** obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz **przenoszenie semantyki** części [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers
 
 ## <a name="see-also"></a>Zobacz też
 [Mutex — klasa](../windows/mutex-class1.md)