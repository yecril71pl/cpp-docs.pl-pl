---
title: Praca z obiektami okien | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- child windows [MFC], working with
- window objects [MFC], working with
ms.assetid: f73aa254-90e3-46a9-8e9b-d78b7054a331
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 55f3eae10954ee2da1386907f88ae8b594dc8e53
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413636"
---
# <a name="working-with-window-objects"></a>Praca z obiektami okien

Praca z wywołaniami systemu windows na dwa rodzaje działań:

- Obsługa komunikatów Windows

- Rysowanie w oknie

Do obsługi komunikatów Windows w dowolnym oknie, w tym własne okna podrzędnego zobaczyć [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md) do mapy wiadomości do klasy okna języka C++. Następnie napisać program obsługi komunikatów funkcji składowych w klasie.

Większość rysowania w aplikacji framework odbywa się w widoku, którego [OnDraw](../mfc/reference/cview-class.md#ondraw) funkcja członkowska jest wywoływana zawsze wtedy, gdy musi zostać narysowany zawartość okna. Jeśli okno jest elementem podrzędnym tego widoku, może przekazywać niektóre Rysowanie w widoku do okna podrzędne dzięki `OnDraw` wywołać jedną z funkcji elementów członkowskich z oknem.

W każdym przypadku konieczne będzie kontekst urządzenia do rysowania. Można użyć standardowych pióra, pędzla i innymi obiektami zawarte w kontekście urządzenia skojarzony z oknem. Lub możesz zmodyfikować te obiekty, aby uzyskać efekty rysowania, czego potrzebujesz. Przy użyciu kontekstu urządzenia, jak chcesz skonfigurować, wywołaj element członkowski funkcji klasy [CDC](../mfc/reference/cdc-class.md) (kontekst urządzenia klasy) do rysowania linii, kształty i tekst; Użyj kolorów; oraz pracy z układ współrzędnych.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Obsługa i mapowanie komunikatów](../mfc/message-handling-and-mapping.md)

- [Rysowanie w widoku](../mfc/drawing-in-a-view.md)

- [Konteksty urządzenia](../mfc/device-contexts.md)

- [Obiekty graficzne](../mfc/graphic-objects.md)

## <a name="see-also"></a>Zobacz też

[Obiekty okna](../mfc/window-objects.md)

