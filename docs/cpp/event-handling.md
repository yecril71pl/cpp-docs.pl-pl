---
title: Obsługa zdarzeń
ms.date: 05/07/2019
helpviewer_keywords:
- event handling [C++]
ms.assetid: 82de3f9a-2d88-470c-9527-8a5b54c8ced4
ms.openlocfilehash: 4ed2dd2140176fe302d2b6800a3aa7768d17eedd
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91498904"
---
# <a name="event-handling"></a>Obsługa zdarzeń

Obsługa zdarzeń jest przede wszystkim obsługiwana dla klas COM (klasy C++ implementujące obiekty COM, zazwyczaj przy użyciu klas ATL lub atrybutu [coclass](../windows/attributes/coclass.md) ). Aby uzyskać więcej informacji, zobacz [Obsługa zdarzeń w modelu COM](../cpp/event-handling-in-com.md).

Obsługa zdarzeń jest również obsługiwana dla natywnych klas języka C++ (klasy C++, które nie implementują obiektów COM), jednak pomoc techniczna jest przestarzała i zostanie usunięta w przyszłej wersji.  Aby uzyskać więcej informacji, zobacz [Obsługa zdarzeń w natywnym języku C++](../cpp/event-handling-in-native-cpp.md).

Obsługa zdarzeń obsługuje pojedyncze i wielowątkowe użycie i chroni dane przed jednoczesnym dostępem wielowątkowej. Umożliwia także wyprowadzanie podklas z klas źródłowych zdarzeń lub odbiorników oraz obsługę rozszerzonych źródeł zdarzeń/odbieranych w klasie pochodnej.

Kompilator języka Microsoft C++ zawiera atrybuty i słowa kluczowe do deklarowania zdarzeń i programów obsługi zdarzeń. Atrybuty i słowa kluczowe zdarzenia mogą być używane w programach CLR i w natywnych programach języka C++.

|Temat|Opis|
|-----------|-----------------|
|[event_source](../windows/attributes/event-source.md)|Tworzy Źródło zdarzenia.|
|[event_receiver](../windows/attributes/event-receiver.md)|Tworzy odbiorcę zdarzeń (ujścia).|
|[__event](../cpp/event.md)|Deklaruje zdarzenie.|
|[__raise](../cpp/raise.md)|Wyróżnia lokację wywołania zdarzenia.|
|[__hook](../cpp/hook.md)|Kojarzy metodę procedury obsługi ze zdarzeniem.|
|[__unhook](../cpp/unhook.md)|Deskojarzenie metody obsługi ze zdarzenia.|

## <a name="see-also"></a>Zobacz też

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
