---
title: 'Wyjątki: Wyjątki w konstruktorach | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3cab21255698c19046cfca185a0d8d7e7c530112
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421937"
---
# <a name="exceptions-exceptions-in-constructors"></a>Wyjątki: wyjątki w konstruktorach

Gdy zostanie zgłoszony wyjątek w konstruktorze, wyczyść dowolnych obiektów i alokacji pamięci wprowadzono przed zgłaszania wyjątku, zgodnie z objaśnieniem w [wyjątki: zgłaszanie wyjątków z Twojej własnej funkcji](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md).

Gdy zostanie zgłoszony wyjątek w konstruktorze, pamięć sam obiekt został już przydzielony przez razem, gdy wywoływany jest Konstruktor. Tak kompilator będzie automatycznie cofnięcia przydzielenia pamięci zajmowanego przez obiekt po wyrzuceniu wyjątku.

Aby uzyskać więcej informacji, zobacz [wyjątki: zwalnianie obiektów w wyjątkach](../mfc/exceptions-freeing-objects-in-exceptions.md).

## <a name="see-also"></a>Zobacz też

[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)

