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
ms.openlocfilehash: d27ff977bf3e4132f7782c0ffcb85bebefd42d68
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961444"
---
# <a name="event-handling"></a>Obsługa zdarzeń
Obsługa zdarzeń przede wszystkim jest obsługiwana dla klasy COM (klasy C++, które implementują obiektów COM, zazwyczaj przy użyciu klasy ATL lub [coclass](../windows/coclass.md) atrybutu).  Aby uzyskać więcej informacji, zobacz [zdarzenie obsługi w modelu COM](../cpp/event-handling-in-com.md).  
  
 Obsługa zdarzeń jest również obsługiwana dla macierzystych klas C++ (klasy C++, które nie implementują obiektów COM), jednak obsługujących jest przestarzały i zostanie usunięta w przyszłej wersji.  Aby uzyskać więcej informacji, zobacz [zdarzenie obsługi w natywnym kodzie C++](../cpp/event-handling-in-native-cpp.md).  
  
 Obsługa zdarzeń obsługuje jedno -, jak i wielowątkowe użycie i chroni dane przed jednoczesny dostęp wielowątkowych. Umożliwia również pochodzić podklasy ze źródła zdarzeń lub klasy odbiorcy i obsługę rozszerzonych określania źródła zdarzeń i odbieranie w klasie pochodnej.  
  
 Visual C++ zawiera atrybuty i słowa kluczowe do deklarowania zdarzenia i procedury obsługi zdarzeń. Atrybuty zdarzeń i słów kluczowych może służyć w programach CLR i w natywnych programach języka C++.  
  
|Temat|Opis|  
|-----------|-----------------|  
|[event_source](../windows/event-source.md)|Tworzy źródła zdarzenia.|  
|[event_receiver](../windows/event-receiver.md)|Tworzy odbiorca zdarzenia (ujścia).|  
|[__event](../cpp/event.md)|Deklaruje zdarzenie.|  
|[__raise](../cpp/raise.md)|Kładzie nacisk witryny wywołania zdarzenia.|  
|[__hook](../cpp/hook.md)|Kojarzy metody obsługi ze zdarzeniem.|  
|[__unhook](../cpp/unhook.md)|Dissociates metody obsługi zdarzeń.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
