---
title: HandleT::Detach, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method
ms.assetid: f7df0f90-fafb-4d1b-a215-a6c62941f6b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7bf4a6fab735708295a0ae229e7b47101ecc115b
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648395"
---
# <a name="handletdetach-method"></a>HandleT::Detach — Metoda
Powoduje usunięcie bieżącego **HandleT** obiekt z jego podstawowego dojścia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typename HandleTraits::Type Detach();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Podstawowego dojścia.  
  
## <a name="remarks"></a>Uwagi  
 Po zakończeniu tej operacji, bieżący **HandleT** ustawiono nieprawidłowy stan.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers  
  
## <a name="see-also"></a>Zobacz też  
 [HandleT, klasa](../windows/handlet-class.md)