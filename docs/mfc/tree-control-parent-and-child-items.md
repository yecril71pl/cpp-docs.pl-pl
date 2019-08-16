---
title: Elementy nadrzędne i podrzędne kontrolki drzewa
ms.date: 11/04/2016
helpviewer_keywords:
- parent items in CTreeCtrl [MFC]
- child items in tree control [MFC]
- CTreeCtrl class [MFC], parent and child items
- tree controls [MFC], parent and child items
ms.assetid: abcea1e4-fe9b-40d9-86dc-1db235f8f103
ms.openlocfilehash: 5a02194ccef8eca81971bb4e8ae24d859e578bcc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513969"
---
# <a name="tree-control-parent-and-child-items"></a>Elementy nadrzędne i podrzędne kontrolki drzewa

Każdy element w kontrolce drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) może mieć listę elementów podrzędnych, które są nazywane elementami podrzędnymi, z których skojarzone. Element, który ma co najmniej jeden element podrzędny jest nazywany elementem nadrzędnym. Element podrzędny jest wyświetlany poniżej jego elementu nadrzędnego i ma wcięcia, aby wskazać, że jest podrzędny względem elementu nadrzędnego. Element, który nie ma elementu nadrzędnego, znajduje się na szczycie hierarchii i nosi nazwę elementu głównego.

W danym momencie stan listy elementów podrzędnych elementu nadrzędnego może być rozwinięty lub zwinięty. Gdy stan jest rozwinięty, elementy podrzędne są wyświetlane poniżej elementu nadrzędnego. Gdy jest zwinięte, elementy podrzędne nie są wyświetlane. Lista automatycznie przełącza się między rozwiniętym i zwiniętym stanem, gdy użytkownik kliknie dwukrotnie element nadrzędny lub, jeśli element nadrzędny ma styl **TVS_HASBUTTONS** , gdy użytkownik kliknie przycisk skojarzony z elementem nadrzędnym. Aplikacja może rozwijać lub zwijać elementy podrzędne przy użyciu funkcji [Rozwiń](../mfc/reference/ctreectrl-class.md#expand) element członkowski.

Dodaj element do kontrolki drzewa, wywołując funkcję elementu członkowskiego [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) . Ta funkcja zwraca dojście typu **hTreeItem** , który jednoznacznie identyfikuje element. Podczas dodawania elementu należy określić uchwyt elementu nadrzędnego nowego elementu. W przypadku określenia wartości **null** lub wartości **TVI_ROOT** zamiast uchwytu elementu nadrzędnego w strukturze [TVINSERTSTRUCT](/windows/win32/api/commctrl/ns-commctrl-tvinsertstructw) lub *hParent* , element zostanie dodany jako element główny.

Kontrolka drzewa wysyła komunikat powiadomienia [TVN_ITEMEXPANDING](/windows/win32/Controls/tvn-itemexpanding) , gdy lista elementów podrzędnych elementu nadrzędnego zostanie rozwinięta lub zwinięte. Powiadomienie daje możliwość uniemożliwienia zmiany lub ustawienia atrybutów elementu nadrzędnego, które są zależne od stanu listy elementów podrzędnych. Po zmianie stanu listy formant drzewa wysyła komunikat powiadomienia [TVN_ITEMEXPANDED](/windows/win32/Controls/tvn-itemexpanded) .

Gdy lista elementów podrzędnych jest rozwinięta, wcięcie jest wcięte względem elementu nadrzędnego. Można ustawić wcięcie przy użyciu funkcji elementu członkowskiego setwcięcie [](../mfc/reference/ctreectrl-class.md#setindent) lub pobrać bieżącą kwotę za pomocą funkcji składowej getwcięcia. [](../mfc/reference/ctreectrl-class.md#getindent)

## <a name="see-also"></a>Zobacz także

[Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
