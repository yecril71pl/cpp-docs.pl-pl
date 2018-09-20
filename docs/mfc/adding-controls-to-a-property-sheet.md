---
title: Dodawanie formantów do arkusza właściwości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [MFC], adding to property sheets
- property sheets, adding controls
ms.assetid: 24ad4c0b-c1db-4850-b9f0-34aae8d74571
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0783571ed77d3d8dfaca69edf06330e62d8e98d0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398511"
---
# <a name="adding-controls-to-a-property-sheet"></a>Dodawanie formantów do arkusza właściwości

Domyślnie arkusz właściwości przydziela obszaru okna stron właściwości, kolejność tabulacji i przyciski OK, Anuluj i Zastosuj. (Niemodalnego arkusza właściwości nie ma OK, anulować i Zastosuj przyciski). Możesz dodać inne formanty do arkusza właściwości. Na przykład można dodać okno podglądu po prawej stronie obszaru strony właściwości pokazać użytkownikowi bieżące ustawienia wygląda podobnie jak w przypadku stosowane do obiektu zewnętrznego.

Można dodać kontrolki do okna dialogowego arkusz właściwości w `OnCreate` programu obsługi. Zazwyczaj ograniczanych dodatkowe elementy sterujące wymaga rozszerzania rozmiar okna dialogowego arkusza właściwości. Po wywołaniu klasy bazowej **CPropertySheet::OnCreate**, wywołaj [getwindowrect —](../mfc/reference/cwnd-class.md#getwindowrect) można pobrać, szerokość i wysokość okna arkusza właściwości aktualnie przydzielone, rozwiń węzeł prostokąta wymiary i wywołanie [MoveWindow](../mfc/reference/cwnd-class.md#movewindow) do zmiany rozmiaru okna arkusza właściwości.

## <a name="see-also"></a>Zobacz też

[Arkusze właściwości](../mfc/property-sheets-mfc.md)<br/>
[Klasa CPropertyPage](../mfc/reference/cpropertypage-class.md)<br/>
[Klasa CPropertySheet](../mfc/reference/cpropertysheet-class.md)
