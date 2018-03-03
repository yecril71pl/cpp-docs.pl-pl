---
title: "Obsługa zdarzeń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], event handling
- intrinsic functions [C++], event handling
- event handling [C++], Visual C++
ms.assetid: 82de3f9a-2d88-470c-9527-8a5b54c8ced4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4167a76d3e301f76ebba09f78abcd7e64fc7f108
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="event-handling"></a>Obsługa zdarzeń
Obsługa zdarzeń przede wszystkim jest obsługiwana dla klasy COM (C++ klasy, które implementują obiektów COM, zwykle za pomocą klasy ATL lub [coclass](../windows/coclass.md) atrybutu).  Aby uzyskać więcej informacji, zobacz [obsługi zdarzeń w modelu COM](../cpp/event-handling-in-com.md).  
  
 Obsługa zdarzeń jest również obsługiwane dla macierzystych klas C++ (klasy C++, które nie implementują obiektów COM), jednak obsługujących jest przestarzała i zostanie usunięta w przyszłej wersji.  Aby uzyskać więcej informacji, zobacz [obsługi zdarzeń w natywnym kodzie C++](../cpp/event-handling-in-native-cpp.md).  
  
 Obsługa zdarzeń obsługuje jedno - i wielowątkowe użycie i chroni dane przed jednoczesny dostęp wielowątkowym. Umożliwia również pochodzić podklasy ze źródła zdarzeń lub klasy odbiornik i pomocy technicznej rozszerzone sourcing zdarzeń i odbieranie w klasie pochodnej.  
  
 Visual C++ zawiera atrybuty i słów kluczowych deklarowania zdarzenia i procedury obsługi zdarzeń. Atrybuty zdarzeń i słów kluczowych można w programach CLR i w programach natywnych języka C++.  
  
|Temat|Opis|  
|-----------|-----------------|  
|[event_source](../windows/event-source.md)|Tworzy źródła zdarzenia.|  
|[event_receiver](../windows/event-receiver.md)|Tworzy odbiorcy zdarzeń (zbiornika).|  
|[__event](../cpp/event.md)|Deklaruje zdarzenie.|  
|[__raise](../cpp/raise.md)|Zwrócono szczególną uwagę na miejsce wywołania zdarzenia.|  
|[__hook](../cpp/hook.md)|Kojarzy metoda obsługi ze zdarzeniem.|  
|[__unhook](../cpp/unhook.md)|Dissociates metody obsługi zdarzeń.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 [Przykłady obsługi zdarzeń](http://msdn.microsoft.com/en-us/cc0287d4-f92b-4da5-85fc-a0f186e16424)