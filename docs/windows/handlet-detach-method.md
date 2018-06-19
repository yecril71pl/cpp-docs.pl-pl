---
title: HandleT::Detach — metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 100d215099494c9b2714fd2c42dee69644a5006c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878466"
---
# <a name="handletdetach-method"></a>HandleT::Detach — Metoda
Usuwa skojarzenia bieżącego obiektu handlet — z uchwytu podstawowej.  
  
## <a name="syntax"></a>Składnia  
  
```  
typename HandleTraits::Type Detach();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Dojście podstawowej.  
  
## <a name="remarks"></a>Uwagi  
 Po zakończeniu tej operacji, bieżący handlet — ustawiono nieprawidłowy stan.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [HandleT, klasa](../windows/handlet-class.md)