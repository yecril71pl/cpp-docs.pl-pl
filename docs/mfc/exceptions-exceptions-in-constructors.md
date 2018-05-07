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
ms.openlocfilehash: 8336700cc0137efe3bc106871ebd76b8de7a99af
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="exceptions-exceptions-in-constructors"></a>Wyjątki: wyjątki w konstruktorach
Po zgłoszeniu wyjątku w konstruktorze, wyczyść niezależnie od obiektów i alokacji pamięci zostały wprowadzone przed zgłoszeniem wyjątku, zgodnie z objaśnieniem w [wyjątki: zgłaszanie wyjątków z swój własny funkcji](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md).  
  
 Po zgłoszeniu wyjątku w konstruktorze, pamięć sam obiekt został już przydzielony przez czas wywołania konstruktora. Tak kompilator będzie automatycznie cofnięcia przydzielenia pamięci zajmowanego przez obiekt po wyjątku.  
  
 Aby uzyskać więcej informacji, zobacz [wyjątki: zwalnianie obiektów w wyjątkach](../mfc/exceptions-freeing-objects-in-exceptions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)

