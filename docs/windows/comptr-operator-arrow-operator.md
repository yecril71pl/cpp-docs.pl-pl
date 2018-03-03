---
title: "ComPtr::operator —&gt; Operator | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator->
dev_langs:
- C++
helpviewer_keywords:
- operator-> operator
ms.assetid: 7b7faefd-d1e4-4f31-a77d-17a42e0d6b6a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3c70c37523132d06bfb04c86cf6f737109da43e2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="comptroperator-gt-operator"></a>ComPtr::operator —&gt; — Operator
Pobiera wskaźnik do typu określonego przez parametr bieżącego szablonu.  
  
## <a name="syntax"></a>Składnia  
  
```  
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do typu określonego za pomocą bieżącej nazwy typu szablonu.  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja pomocnika usuwa niepotrzebne obciążenie spowodowane użyciem stdmethod — makro. Ta funkcja sprawia, że typy IUnknown prywatnej zamiast wirtualnego.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [ComPtr, klasa](../windows/comptr-class.md)