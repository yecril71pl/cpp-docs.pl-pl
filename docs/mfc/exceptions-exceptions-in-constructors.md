---
title: 'Wyjątki: wyjątki w konstruktorach'
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
ms.openlocfilehash: 4089f4d44f03c7de3432f137b5d28f74189e1cb9
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624617"
---
# <a name="exceptions-exceptions-in-constructors"></a>Wyjątki: wyjątki w konstruktorach

W przypadku zgłaszania wyjątku w konstruktorze Wyczyść wszystkie obiekty i alokacje pamięci wykonane przed wygenerowaniem wyjątku, jak wyjaśniono w [wyjątkach: zgłaszanie wyjątków z własnych funkcji](exceptions-throwing-exceptions-from-your-own-functions.md).

W przypadku zgłaszania wyjątku w konstruktorze pamięć dla samego obiektu została już przydzielone przez czas, gdy Konstruktor jest wywoływany. W takim przypadku kompilator automatycznie przywróci pamięć zajmowaną przez obiekt po wystąpieniu wyjątku.

Aby uzyskać więcej informacji, zobacz [wyjątki: zwalnianie obiektów w wyjątkach](exceptions-freeing-objects-in-exceptions.md).

## <a name="see-also"></a>Zobacz też

[Obsługa wyjątków](exception-handling-in-mfc.md)
