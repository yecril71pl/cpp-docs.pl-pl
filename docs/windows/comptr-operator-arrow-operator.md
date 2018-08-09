---
title: ComPtr::operator -&gt; Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator->
dev_langs:
- C++
helpviewer_keywords:
- operator-> operator
ms.assetid: 7b7faefd-d1e4-4f31-a77d-17a42e0d6b6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1530f7998f2597aeb2fe46dba09f4844b471cd93
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644833"
---
# <a name="comptroperator-gt-operator"></a>ComPtr::operator —&gt; — Operator
Pobiera wskaźnik do typu określonego przez parametr bieżącego szablonu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do typu określonego przez nazwę typu bieżącego szablonu.  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja pomocnika usuwa niepotrzebne obciążenie spowodowane użyciem STDMETHOD — makro. Ta funkcja sprawia, że `IUnknown` typy **prywatnej** zamiast **wirtualnego**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [ComPtr, klasa](../windows/comptr-class.md)