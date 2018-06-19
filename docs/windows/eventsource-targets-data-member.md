---
title: EventSource::targets_ — członek danych | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: a35992a5579bf852323f4c01396fab56542f40cd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33871747"
---
# <a name="eventsourcetargets-data-member"></a>EventSource::targets_ — Członek danych
Tablica procedury obsługi zdarzeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
ComPtr<Details::EventTargetArray> targets_;  
```  
  
## <a name="remarks"></a>Uwagi  
 W przypadku wystąpienia zdarzenia, które jest reprezentowana przez bieżącego obiektu EventSource są wywoływane programy obsługi zdarzeń.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::wrl —
 
 ## <a name="see-also"></a>Zobacz też
 [EventSource, klasa](../windows/eventsource-class.md)