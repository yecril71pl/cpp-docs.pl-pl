---
title: "Getmodulebase — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::GetModuleBase
dev_langs: C++
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 19f575705b1f8680a68e9100f20be66ca22ec87a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="getmodulebase-function"></a>GetModuleBase — Funkcja
Pobiera [ModuleBase](../windows/modulebase-class.md) wskaźnika, który umożliwia zwiększanie oraz zmniejszanie liczebności referencyjnej równej [runtimeclass —](../windows/runtimeclass-class.md) obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
inline Details::ModuleBase* GetModuleBase() throw()  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `ModuleBase` obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest używana wewnętrznie w celu zwiększyć i zmniejszyć liczby odwołanie do obiektu.  
  
 Ta funkcja służy do kontrolowania liczby odwołań przez wywołanie metody [ModuleBase::IncrementObjectCount](../windows/modulebase-incrementobjectcount-method.md) i [ModuleBase::DecrementObjectCount](../windows/modulebase-decrementobjectcount-method.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)