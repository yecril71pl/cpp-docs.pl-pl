---
title: "DeferrableEventArgs::InvokeAllFinished — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 86b45205-3edb-4134-9cd0-ed7a7b4c3b1a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0ca021d66c615bfec84b8f08df8474eeb20709e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="deferrableeventargsinvokeallfinished-method"></a>DeferrableEventArgs::InvokeAllFinished — metoda
Wywołuje się, by wskazać, że przetwarzania obsługi zdarzenia odroczone jest pełny.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void InvokeAllFinished()  
```  
  
## <a name="remarks"></a>Uwagi  
 Tej metody należy wywołać po wywołań źródła zdarzeń [InvokeAll](../windows/eventsource-invokeall-method.md). Wywołanie tej metody uniemożliwia dalsze odroczenia podjęcie i wymusza programu obsługi zakończenia wykonywania odroczenia nie zostały pobrane.  
  
 Na przykład kod, zobacz [deferrableeventargs — klasa](../windows/deferrableeventargs-class.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Deferrableeventargs — klasa](../windows/deferrableeventargs-class.md)   
 [EventSource::InvokeAll, metoda](../windows/eventsource-invokeall-method.md)