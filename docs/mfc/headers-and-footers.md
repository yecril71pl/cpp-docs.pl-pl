---
title: Nagłówki i stopki
ms.date: 11/04/2016
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
ms.openlocfilehash: 7024c57dbe41a579582d409d0536db0ca0bc46d6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620107"
---
# <a name="headers-and-footers"></a>Nagłówki i stopki

W tym artykule wyjaśniono, jak dodać nagłówki i stopki do drukowanego dokumentu.

Podczas przeglądania dokumentu na ekranie, nazwa dokumentu i bieżąca lokalizacja w dokumencie są często wyświetlane na pasku tytułu i na pasku stanu. Gdy przeglądasz wydrukowaną kopię dokumentu, warto mieć nazwę i numer strony wyświetlaną w nagłówku lub stopce. Jest to typowy sposób, w którym nawet programy w trybie WYSIWYG różnią się sposobem drukowania i wyświetlania ekranu.

Funkcja składowej [OnPrint](reference/cview-class.md#onprint) jest odpowiednim miejscem do drukowania nagłówków lub stopek, ponieważ jest wywoływana dla każdej strony i ponieważ jest wywoływana tylko do drukowania, a nie do wyświetlania ekranu. Można zdefiniować osobną funkcję do drukowania nagłówka lub stopki i przekazać ją do kontekstu urządzenia drukarki `OnPrint` . Może być konieczne dostosowanie pochodzenia okna lub zakresu przed wywołaniem funkcji [OnDraw](reference/cview-class.md#ondraw) , aby uniknąć, że treść strony pokrywa się z nagłówkiem lub stopką. Może być również konieczne zmodyfikowanie, `OnDraw` ponieważ ilość dokumentu, który mieści się na stronie, może ulec zmniejszeniu.

Jednym ze sposobów kompensaty za obszar, w którym znajduje się nagłówek lub stopka, jest użycie **m_rectDrawego** elementu członkowskiego [CPrintInfo](reference/cprintinfo-structure.md). Za każdym razem, gdy strona jest drukowana, ten element członkowski jest inicjowany za pomocą obszaru możliwego do użycia na stronie. W przypadku drukowania nagłówka lub stopki przed wydrukowaniem treści strony można zmniejszyć rozmiar prostokąta przechowywanego w **m_rectDraw** , aby uwzględnić obszar, w którym znajduje się nagłówek lub Stopka. Następnie `OnPrint` może odwoływać się do **m_rectDraw** , aby dowiedzieć się, ile obszaru pozostało do drukowania treści strony.

Nie można drukować nagłówka ani niczego innego, od [OnPrepareDC](reference/cview-class.md#onpreparedc), ponieważ jest on wywoływany przed `StartPage` wywołaniem funkcji składowej [CDC](reference/cdc-class.md) obiektu przenoszącego. W tym momencie kontekst urządzenia drukarki jest uznawany za na granicy strony. Drukowanie można przeprowadzić tylko z poziomu `OnPrint` funkcji składowej.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Drukowanie dokumentów wielostronicowych](multipage-documents.md)

- [Alokowanie zasobów GDI do drukowania](allocating-gdi-resources.md)

## <a name="see-also"></a>Zobacz też

[Drukowanie](printing.md)
