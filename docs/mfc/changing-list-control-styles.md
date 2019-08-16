---
title: Zmienianie stylów kontrolki listy
ms.date: 11/04/2016
helpviewer_keywords:
- styles [MFC], CListCtrl
- CListCtrl class [MFC], styles
- CListCtrl class [MFC], changing styles
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
ms.openlocfilehash: b3cc65ce6ef0e84eaa2f6738cb18b6b862a6473a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509052"
---
# <a name="changing-list-control-styles"></a>Zmienianie stylów kontrolki listy

Można zmienić styl okna kontrolki listy ([CListCtrl](../mfc/reference/clistctrl-class.md)) w dowolnym momencie po utworzeniu. Zmiana stylu okna powoduje zmianę rodzaju widoku używanego przez formant. Na przykład w celu emulowania Eksploratora możesz dostarczyć elementy menu lub przyciski paska narzędzi, aby przełączać kontrolkę między różnymi widokami: Widok ikon, widok listy i tak dalej.

Na przykład, gdy użytkownik wybierze element menu, można wywołać [GetWindowLong](/windows/win32/api/winuser/nf-winuser-getwindowlongw) w celu pobrania bieżącego stylu kontrolki, a następnie wywołać [SetWindowLong](/windows/win32/api/winuser/nf-winuser-setwindowlongw) w celu zresetowania stylu. Aby uzyskać więcej informacji, zobacz [Korzystanie z kontrolek widoku listy](/windows/win32/Controls/using-list-view-controls) w Windows SDK.

Dostępne style są wymienione w temacie [Create](../mfc/reference/clistctrl-class.md#create). Style **LVS_ICON**, **LVS_SMALLICON**, **LVS_LIST**i **LVS_REPORT** określają cztery widoki formantów listy.

## <a name="extended-styles"></a>Style rozszerzone

Oprócz standardowych stylów kontrolki listy istnieje inny zestaw nazywany stylami rozszerzonymi. Te style omówione w [stylu widoku listy rozszerzonej](/windows/win32/Controls/extended-list-view-styles) w Windows SDK zapewniają wiele przydatnych funkcji, które dostosowują zachowanie kontrolki listy. Aby zaimplementować zachowanie pewnego stylu (takiego jak wybór aktywowany), należy wywołać metodę [CListCtrl:: setextended](../mfc/reference/clistctrl-class.md#setextendedstyle), przechodząc do wymaganego stylu. Poniższy przykład ilustruje wywołanie funkcji:

[!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/cpp/changing-list-control-styles_1.cpp)]

> [!NOTE]
>  Aby zaznaczenie nie było możliwe, musisz mieć włączone **LVS_EX_ONECLICKACTIVATE** lub **LVS_EX_TWOCLICKACTIVATE** .

## <a name="see-also"></a>Zobacz także

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
