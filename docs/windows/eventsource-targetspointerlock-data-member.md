---
title: EventSource::targetspointerlock_ — członek danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::targetsPointerLock_
dev_langs:
- C++
helpviewer_keywords:
- targetsPointerLock_ data member
ms.assetid: 8f08409f-5262-4be7-9cf1-2ed15f19684a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fb3c2131331521dab1b8264b696206d953762851
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873111"
---
# <a name="eventsourcetargetspointerlock-data-member"></a>EventSource::targetsPointerLock_ — Członek danych
Synchronizuje dostępu do elementów członkowskich danych wewnętrznych, nawet wtedy, gdy programy obsługi zdarzeń dla tego elementu EventSource są dodawane, usunięte lub wywołany.  
  
## <a name="syntax"></a>Składnia  
  
```  
Wrappers::SRWLock targetsPointerLock_;  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::wrl —
 
 ## <a name="see-also"></a>Zobacz też
 [EventSource, klasa](../windows/eventsource-class.md)