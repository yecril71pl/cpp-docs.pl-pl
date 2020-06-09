---
title: Dodawanie formantów do arkusza właściwości
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], adding to property sheets
- property sheets, adding controls
ms.assetid: 24ad4c0b-c1db-4850-b9f0-34aae8d74571
ms.openlocfilehash: 527c0a5ef6e9dc4fcc9d7668c12e15ec956b0e70
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616057"
---
# <a name="adding-controls-to-a-property-sheet"></a>Dodawanie formantów do arkusza właściwości

Domyślnie arkusz właściwości przydziela obszar okna dla stron właściwości, indeksu karty i przycisków OK, Anuluj i Zastosuj. (Niemodalny arkusz właściwości nie ma przycisków OK, Anuluj i Zastosuj). Możesz dodać inne kontrolki do arkusza właściwości. Na przykład można dodać okno podglądu z prawej strony obszaru Strona właściwości, aby pokazać użytkownikowi, jak będą wyglądać bieżące ustawienia w przypadku zastosowania do obiektu zewnętrznego.

Kontrolki można dodać do okna dialogowego arkusza właściwości w programie `OnCreate` obsługi. Obsługa dodatkowych kontrolek zwykle wymaga poszerzenia rozmiaru okna dialogowego arkusza właściwości. Po wywołaniu klasy bazowej **CPropertySheet:: OnCreate**, Call [GetWindowRect](reference/cwnd-class.md#getwindowrect) , aby uzyskać szerokość i wysokość okna aktualnie przydzielony arkusz właściwości, rozwiń wymiary prostokąta i Wywołaj [MoveWindow](reference/cwnd-class.md#movewindow) , aby zmienić rozmiar okna arkusza właściwości.

## <a name="see-also"></a>Zobacz też

[Arkusze właściwości](property-sheets-mfc.md)<br/>
[Klasa CPropertyPage](reference/cpropertypage-class.md)<br/>
[Klasa CPropertySheet](reference/cpropertysheet-class.md)
