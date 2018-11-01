---
title: 'Wyjątki: wyjątki w konstruktorach'
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
ms.openlocfilehash: 23d1f6a9a3c76cc9c0c1d4aebd5c0b0ea45c3154
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472274"
---
# <a name="exceptions-exceptions-in-constructors"></a>Wyjątki: wyjątki w konstruktorach

Gdy zostanie zgłoszony wyjątek w konstruktorze, wyczyść dowolnych obiektów i alokacji pamięci wprowadzono przed zgłaszania wyjątku, zgodnie z objaśnieniem w [wyjątki: zgłaszanie wyjątków z Twojej własnej funkcji](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md).

Gdy zostanie zgłoszony wyjątek w konstruktorze, pamięć sam obiekt został już przydzielony przez razem, gdy wywoływany jest Konstruktor. Tak kompilator będzie automatycznie cofnięcia przydzielenia pamięci zajmowanego przez obiekt po wyrzuceniu wyjątku.

Aby uzyskać więcej informacji, zobacz [wyjątki: zwalnianie obiektów w wyjątkach](../mfc/exceptions-freeing-objects-in-exceptions.md).

## <a name="see-also"></a>Zobacz też

[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)

