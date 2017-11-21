---
title: "ComPtr::operator == — Operator | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::ComPtr::operator==
dev_langs: C++
ms.assetid: 6a26e936-29d4-4b7d-b44a-7c575ad07509
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2f325e4dbdeb862b417d390bbc432917c67d7a94
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="comptroperator-operator"></a>ComPtr::operator== Operator
Wskazuje, czy dwa obiekty comptr — są takie same.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
bool operator==(  
   const ComPtr<T>& a,  
   const ComPtr<U>& b  
);  
  
bool operator==(  
   const ComPtr<T>& a,  
   decltype(__nullptr)  
);  
  
bool operator==(  
   decltype(__nullptr),  
   const ComPtr<T>& a  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `a`  
 Odwołanie do obiektu comptr —.  
  
 `b`  
 Odwołanie do innego obiektu comptr —.  
  
## <a name="return-value"></a>Wartość zwracana  
 Pierwszy wydajności operator `true` Jeśli obiekt `a` jest taki sam obiekt `b`; w przeciwnym razie `false`.  
  
 Operatory drugi i trzeci yield `true` Jeśli obiekt `a` jest równa `nullptr`; w przeciwnym razie `false`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl — Namespace](../windows/microsoft-wrl-namespace.md)   
 [Comptr — klasa](../windows/comptr-class.md)