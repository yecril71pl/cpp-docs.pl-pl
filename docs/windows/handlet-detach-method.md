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
ms.openlocfilehash: cc11d6be992584adb1ce2075e73d080cc3a43f47
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2018
ms.locfileid: "39569482"
---
# <a name="handletdetach-method"></a>HandleT::Detach — Metoda
Powoduje usunięcie bieżącego **HandleT** obiekt z jego podstawowego dojścia.  
  
## <a name="syntax"></a>Składnia  
  
```  
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