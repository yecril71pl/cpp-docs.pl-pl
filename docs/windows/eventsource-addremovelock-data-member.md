---
title: "EventSource::addremovelock_ — członek danych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::EventSource::addRemoveLock_
dev_langs: C++
helpviewer_keywords: addRemoveLock_ data member
ms.assetid: e2d69256-4891-4aad-ad0b-76479c0bb076
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1eb3a62429883ce8b2ff39828cdcdff47624f894
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="eventsourceaddremovelock-data-member"></a>EventSource::addRemoveLock_ — Członek danych
Synchronizuje dostęp do [targets_ —](../windows/eventsource-targets-data-member.md) tablicy podczas dodawania, usuwania lub wywoływanie programów obsługi zdarzeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
Wrappers::SRWLock addRemoveLock_;  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::wrl —
 
 ## <a name="see-also"></a>Zobacz też
 [EventSource — klasa](../windows/eventsource-class.md)