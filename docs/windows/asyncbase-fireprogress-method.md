---
title: "AsyncBase::FireProgress — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::FireProgress
dev_langs: C++
helpviewer_keywords: FireProgress method
ms.assetid: 4512bef6-0ebc-4465-9b8a-4c9dfa82084c
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 358a85f6ec0a451534684f2201caffefb1c1ad1b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="asyncbasefireprogress-method"></a>AsyncBase::FireProgress — Metoda
Wywołuje Bieżący postęp obsługi zdarzeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
void FireProgress(  
   const typename ProgressTraits::Arg2Type arg  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `arg`  
 Metoda obsługi zdarzeń do wywołania.  
  
## <a name="remarks"></a>Uwagi  
 `ProgressTraits`jest pochodną [argtraitshelper — struktura](../windows/argtraitshelper-structure.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [AsyncBase, klasa](../windows/asyncbase-class.md)