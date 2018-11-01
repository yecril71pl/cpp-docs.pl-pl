---
title: Dodawanie formantów do arkusza właściwości
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], adding to property sheets
- property sheets, adding controls
ms.assetid: 24ad4c0b-c1db-4850-b9f0-34aae8d74571
ms.openlocfilehash: 141339bd146fec20f02e73e24bb9dae387f4e3ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502781"
---
# <a name="adding-controls-to-a-property-sheet"></a>Dodawanie formantów do arkusza właściwości

Domyślnie arkusz właściwości przydziela obszaru okna stron właściwości, kolejność tabulacji i przyciski OK, Anuluj i Zastosuj. (Niemodalnego arkusza właściwości nie ma OK, anulować i Zastosuj przyciski). Możesz dodać inne formanty do arkusza właściwości. Na przykład można dodać okno podglądu po prawej stronie obszaru strony właściwości pokazać użytkownikowi bieżące ustawienia wygląda podobnie jak w przypadku stosowane do obiektu zewnętrznego.

Można dodać kontrolki do okna dialogowego arkusz właściwości w `OnCreate` programu obsługi. Zazwyczaj ograniczanych dodatkowe elementy sterujące wymaga rozszerzania rozmiar okna dialogowego arkusza właściwości. Po wywołaniu klasy bazowej **CPropertySheet::OnCreate**, wywołaj [getwindowrect —](../mfc/reference/cwnd-class.md#getwindowrect) można pobrać, szerokość i wysokość okna arkusza właściwości aktualnie przydzielone, rozwiń węzeł prostokąta wymiary i wywołanie [MoveWindow](../mfc/reference/cwnd-class.md#movewindow) do zmiany rozmiaru okna arkusza właściwości.

## <a name="see-also"></a>Zobacz też

[Arkusze właściwości](../mfc/property-sheets-mfc.md)<br/>
[Klasa CPropertyPage](../mfc/reference/cpropertypage-class.md)<br/>
[Klasa CPropertySheet](../mfc/reference/cpropertysheet-class.md)
