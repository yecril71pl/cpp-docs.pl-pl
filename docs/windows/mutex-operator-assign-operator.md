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
ms.openlocfilehash: 9ce42a1e14e3de77b8ac10c67a8f15b6ee3f080f
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40019959"
---
# <a name="mutexoperator-operator"></a>Mutex::operator= Operator
Przypisuje (ruch) określonego **Mutex** obiekt do bieżącego **Mutex** obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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