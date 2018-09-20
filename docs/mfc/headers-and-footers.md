---
title: Nagłówki i stopki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- printing [MFC], multipage documents
- page headers [MFC], printing
- headers [MFC], printing
- footers [MFC], printing
- page footers [MFC], printing
- page headers [MFC]
- printing [MFC], headers and footers
- page footers [MFC]
ms.assetid: b0be9c53-5773-4955-a777-3c15da745128
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 825a74ebe53b934df6a85b3c06fc7df4f0bc135c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383106"
---
# <a name="headers-and-footers"></a>Nagłówki i stopki

W tym artykule wyjaśniono, jak dodawanie nagłówków i stopek do wydruku dokumentu.

Po wyświetleniu dokumentu na ekranie nazwę dokumentu i bieżącej lokalizacji w dokumencie często są wyświetlane na pasku tytułu i w pasku stanu. Patrząc kopię dokumentu, warto nazwa i numer strony wyświetlany w nagłówku lub stopce. Jest to typowy sposób, w których WYSIWYG nawet programy różnią się w ich działanie drukowania i wyświetlanie na ekranie.

[OnPrint](../mfc/reference/cview-class.md#onprint) funkcja członkowska jest właściwym miejscem do drukowania nagłówków i stopek, ponieważ jest ona wywoływana dla każdej strony, a ponieważ jest ona wywoływana tylko w przypadku drukowania nie do wyświetlania na ekranie. Zdefiniuj to oddzielna funkcja do drukowania w nagłówku lub stopce i przekazać go kontekstu urządzenia drukarki z `OnPrint`. Może być konieczne dostosowanie okna źródła lub zakresie przed wywołaniem [OnDraw](../mfc/reference/cview-class.md#ondraw) pozwala uniknąć treść strony nachodzące na siebie nagłówka lub stopki. Również może być konieczne zmodyfikowanie `OnDraw` ponieważ ilość dokument, który mieści się na stronie może zostać zmniejszona.

Jednym ze sposobów kompensacji dla obszaru podjęte przez nagłówek lub stopka jest użycie **m_rectDraw** członkiem [cprintinfo —](../mfc/reference/cprintinfo-structure.md). Każdorazowo, gdy strona jest drukowany, ten element członkowski jest inicjowany z powierzchnia użytkowa strony. Jeśli nagłówka lub stopki są wydruku przed wydrukowaniem ciała strony, można zmniejszyć rozmiar prostokąta, przechowywane w **m_rectDraw** do konta dla obszaru analizowaniem nagłówka lub stopki. Następnie `OnPrint` mogą odwoływać się do **m_rectDraw** Aby dowiedzieć się, ile obszaru pozostaje drukowanie ciała strony.

Nie można wydrukować nagłówek lub czymkolwiek, z [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc), ponieważ jest ona wywoływana przed `StartPage` funkcji składowej typu [CDC](../mfc/reference/cdc-class.md) została wywołana. W tym momencie kontekstu urządzenia drukarki uznaje się na granicy strony. Można wykonać drukowanie tylko z `OnPrint` funkcja elementu członkowskiego.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Drukowanie dokumentów wielostronicowych](../mfc/multipage-documents.md)

- [Alokowanie zasobów GDI związane z drukowaniem](../mfc/allocating-gdi-resources.md)

## <a name="see-also"></a>Zobacz też

[Drukowanie](../mfc/printing.md)

