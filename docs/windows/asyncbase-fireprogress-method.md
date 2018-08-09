---
title: AsyncBase::FireProgress, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::FireProgress
dev_langs:
- C++
helpviewer_keywords:
- FireProgress method
ms.assetid: 4512bef6-0ebc-4465-9b8a-4c9dfa82084c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 35faad82357b0f449d407787840c865b798427f1
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642012"
---
# <a name="asyncbasefireprogress-method"></a>AsyncBase::FireProgress — Metoda
Wywołuje Bieżący postęp obsługi zdarzeń.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void FireProgress(  
   const typename ProgressTraits::Arg2Type arg  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *ARG*  
 Metoda obsługi zdarzeń do wywołania.  
  
## <a name="remarks"></a>Uwagi  
 `ProgressTraits` jest tworzony na podstawie [argtraitshelper — struktura](../windows/argtraitshelper-structure.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [AsyncBase, klasa](../windows/asyncbase-class.md)