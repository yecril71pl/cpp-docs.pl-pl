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
ms.openlocfilehash: 30ff77fd81b63019f9c6c3bcfc8c6b676a1351f7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Microsoft::wrl — Namespace](../windows/microsoft-wrl-namespace.md)