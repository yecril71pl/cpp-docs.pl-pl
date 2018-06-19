---
title: Getmodulebase — funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
dev_langs:
- C++
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 25e4bb6db6114f7d64522dfe145d51ffaabd476a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874210"
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