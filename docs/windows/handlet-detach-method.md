---
title: "HandleT::Detach — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleT::Detach
dev_langs: C++
helpviewer_keywords: Detach method
ms.assetid: f7df0f90-fafb-4d1b-a215-a6c62941f6b0
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0b17d9f720d2fee92cfcf2aaf7b9f452cde32e3e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Handlet — klasa](../windows/handlet-class.md)