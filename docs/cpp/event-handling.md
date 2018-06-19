---
title: Obsługa zdarzeń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], event handling
- intrinsic functions [C++], event handling
- event handling [C++], Visual C++
ms.assetid: 82de3f9a-2d88-470c-9527-8a5b54c8ced4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 09029f3afef0a9a28fdc572b9b7d8685cf76e811
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32414623"
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
 [Keywords](../cpp/keywords-cpp.md)   
 [Przykłady obsługi zdarzeń](http://msdn.microsoft.com/en-us/cc0287d4-f92b-4da5-85fc-a0f186e16424)