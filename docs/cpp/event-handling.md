---
title: Obsługa zdarzeń
ms.date: 05/07/2019
helpviewer_keywords:
- event handling [C++]
ms.assetid: 82de3f9a-2d88-470c-9527-8a5b54c8ced4
ms.openlocfilehash: cf16ea0e6e14981f1105456a5f17d68c05a9c3fa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189211"
---
# <a name="event-handling"></a>Obsługa zdarzeń

Obsługa zdarzeń jest głównie obsługiwana dla klas COM (C++ klasy implementujące obiekty com, zazwyczaj przy użyciu klas ATL lub atrybut [klasy coclass](../windows/coclass.md) ). Aby uzyskać więcej informacji, zobacz [Obsługa zdarzeń w modelu COM](../cpp/event-handling-in-com.md).

Obsługa zdarzeń jest również obsługiwana dla natywnych C++ klasC++ (klasy, które nie implementują obiektów com), jednak pomoc techniczna jest przestarzała i zostanie usunięta w przyszłej wersji.  Aby uzyskać więcej informacji, zobacz [Obsługa zdarzeń w C++trybie macierzystym ](../cpp/event-handling-in-native-cpp.md).

Obsługa zdarzeń obsługuje pojedyncze i wielowątkowe użycie i chroni dane przed jednoczesnym dostępem wielowątkowej. Umożliwia także wyprowadzanie podklas z klas źródłowych zdarzeń lub odbiorników oraz obsługę rozszerzonych źródeł zdarzeń/odbieranych w klasie pochodnej.

Kompilator firmy C++ Microsoft zawiera atrybuty i słowa kluczowe do deklarowania zdarzeń i programów obsługi zdarzeń. Atrybuty i słowa kluczowe zdarzenia mogą być używane w programach CLR i w programach C++ natywnych.

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
