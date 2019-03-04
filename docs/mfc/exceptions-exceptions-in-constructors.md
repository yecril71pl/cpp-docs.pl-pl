---
title: 'Wyjątki: Wyjątki w konstruktorach'
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
ms.openlocfilehash: 0b11f5be18879d5ad4b9e204bb02e18b4617c6b7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271016"
---
# <a name="exceptions-exceptions-in-constructors"></a>Wyjątki: Wyjątki w konstruktorach

Gdy zostanie zgłoszony wyjątek w konstruktorze, wyczyść dowolnych obiektów i alokacji pamięci wprowadzono przed zgłaszania wyjątku, zgodnie z objaśnieniem w [wyjątków: Zgłaszanie wyjątków z własnych funkcji](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md).

Gdy zostanie zgłoszony wyjątek w konstruktorze, pamięć sam obiekt został już przydzielony przez razem, gdy wywoływany jest Konstruktor. Tak kompilator będzie automatycznie cofnięcia przydzielenia pamięci zajmowanego przez obiekt po wyrzuceniu wyjątku.

Aby uzyskać więcej informacji, zobacz [wyjątków: Zwalnianie obiektów w wyjątkach](../mfc/exceptions-freeing-objects-in-exceptions.md).

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)
