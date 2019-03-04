---
title: Zmienianie stylów kontrolki listy
ms.date: 11/04/2016
helpviewer_keywords:
- styles [MFC], CListCtrl
- CListCtrl class [MFC], styles
- CListCtrl class [MFC], changing styles
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
ms.openlocfilehash: 2ba9ae81f7b1693be0df3565256a65e4e3561fd3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266877"
---
# <a name="changing-list-control-styles"></a>Zmienianie stylów kontrolki listy

Można zmienić styl okna kontrolki listy ([CListCtrl](../mfc/reference/clistctrl-class.md)) w dowolnym momencie po jego utworzeniu. Zmiana stylu okna, możesz zmienić rodzaj widoku, który korzysta z kontrolki. Na przykład, aby emulować w Eksploratorze, może być podasz w menu i przycisków paska narzędzi do przełączania sterowania między różne widoki: widoku ikon, widoku listy i tak dalej.

Na przykład po wybraniu elementu menu, możesz wykonać wywołanie do [GetWindowLong](/windows/desktop/api/winuser/nf-winuser-getwindowlonga) można pobrać bieżącego stylu kontrolki, a następnie wywołać [SetWindowLong](/windows/desktop/api/winuser/nf-winuser-setwindowlonga) zresetować stylu. Aby uzyskać więcej informacji, zobacz [za pomocą kontrolki widoku listy](/windows/desktop/Controls/using-list-view-controls) w zestawie Windows SDK.

Dostępne style są wymienione w [Utwórz](../mfc/reference/clistctrl-class.md#create). Style **LVS_ICON**, **LVS_SMALLICON**, **LVS_LIST**, i **LVS_REPORT** wyznaczyć widoki kontrolne cztery listy.

## <a name="extended-styles"></a>Rozszerzone style

Oprócz standardowych stylów kontrolki listy istnieje inny zestaw, określane jako rozszerzone style. Te style omówione w [rozszerzone style widoku listy](/windows/desktop/Controls/extended-list-view-styles) w zestawie Windows SDK oferują różne przydatne funkcje, które dostosować zachowanie kontroli nad listy. Aby zaimplementować to zachowanie niektórych stylu (takie jak wybór aktywowaniu), wywoływania [CListCtrl::SetExtendedStyle](../mfc/reference/clistctrl-class.md#setextendedstyle), przekazanie wymaganych stylu. W poniższym przykładzie pokazano wywołanie funkcji:

[!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/cpp/changing-list-control-styles_1.cpp)]

> [!NOTE]
>  Do wyboru po wskazaniu wskaźnikiem do pracy, musisz również posiadać albo **LVS_EX_ONECLICKACTIVATE** lub **LVS_EX_TWOCLICKACTIVATE** włączona.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
