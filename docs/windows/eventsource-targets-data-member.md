---
title: EventSource::targets_, składowa danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::targets_
dev_langs:
- C++
helpviewer_keywords:
- targets_ data member
ms.assetid: 5d5cee05-3315-4514-bce2-19173c923c7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ea08cdc8657100e1c1e0157a8a542a44ea34cd4d
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642376"
---
# <a name="eventsourcetargets-data-member"></a>EventSource::targets_ — Członek danych
Tablica procedury obsługi zdarzeń.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
ComPtr<Details::EventTargetArray> targets_;  
```  
  
## <a name="remarks"></a>Uwagi  
 Gdy zdarzenia, który jest reprezentowany przez bieżącą **EventSource** obiekt występuje, są wywoływane programy obsługi zdarzeń.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Zobacz też
 [EventSource, klasa](../windows/eventsource-class.md)