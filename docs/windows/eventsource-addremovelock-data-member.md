---
title: EventSource::addRemoveLock_, składowa danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::addRemoveLock_
dev_langs:
- C++
helpviewer_keywords:
- addRemoveLock_ data member
ms.assetid: e2d69256-4891-4aad-ad0b-76479c0bb076
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9d45ba6670d94ae1a58a1a46fab41dbb2ee6f1c6
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39646543"
---
# <a name="eventsourceaddremovelock-data-member"></a>EventSource::addRemoveLock_ — Członek danych
Synchronizuje dostęp do [targets_ — element](../windows/eventsource-targets-data-member.md) tablicy podczas dodawania, usuwania lub wywoływania procedury obsługi zdarzeń.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
Wrappers::SRWLock addRemoveLock_;  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Zobacz też
 [EventSource, klasa](../windows/eventsource-class.md)