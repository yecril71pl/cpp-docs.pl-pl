---
title: Zmienianie stylów kontrolki listy
ms.date: 11/04/2016
helpviewer_keywords:
- styles [MFC], CListCtrl
- CListCtrl class [MFC], styles
- CListCtrl class [MFC], changing styles
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
ms.openlocfilehash: 5f45e0549c3fc0f5747f8dd12a6310fafd7dd7bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370813"
---
# <a name="changing-list-control-styles"></a>Zmienianie stylów kontrolki listy

Styl okna formantu listy[(CListCtrl)](../mfc/reference/clistctrl-class.md)można zmienić w dowolnym momencie po jego utworzeniu. Zmieniając styl okna, można zmienić rodzaj widoku używa formantu. Na przykład, aby emulować Eksploratora, można podać elementy menu lub przyciski paska narzędzi do przełączania formantu między różnymi widokami: widok ikony, widok listy i tak dalej.

Na przykład, gdy użytkownik wybierze element menu, można nawiązać połączenie [z GetWindowLong,](/windows/win32/api/winuser/nf-winuser-getwindowlongw) aby pobrać bieżący styl formantu, a następnie wywołać [SetWindowLong,](/windows/win32/api/winuser/nf-winuser-setwindowlongw) aby zresetować styl. Aby uzyskać więcej informacji, zobacz [Korzystanie z kontrolek widoku listy](/windows/win32/Controls/using-list-view-controls) w zestawie Windows SDK.

Dostępne style są wymienione w [obszarze Utwórz](../mfc/reference/clistctrl-class.md#create). Style **LVS_ICON** **, LVS_SMALLICON**, **LVS_LIST**i **LVS_REPORT** wyznaczyć cztery widoki kontroli listy.

## <a name="extended-styles"></a>Rozszerzone style

Oprócz standardowych stylów formantu listy istnieje inny zestaw, określany jako style rozszerzone. Te style, omówione w [rozszerzonych stylów widoku listy](/windows/win32/Controls/extended-list-view-styles) w zestawie Windows SDK, zapewniają wiele przydatnych funkcji, które dostosowują zachowanie formantu listy. Aby zaimplementować zachowanie określonego stylu (na przykład zaznaczenie wskaźnika myszy), należy wywołać [CListCtrl::SetExtendedStyle](../mfc/reference/clistctrl-class.md#setextendedstyle), przekazując wymagany styl. Poniższy przykład pokazuje wywołanie funkcji:

[!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/cpp/changing-list-control-styles_1.cpp)]

> [!NOTE]
> Aby wybór najechania kursorem działał, musisz mieć włączony **LVS_EX_ONECLICKACTIVATE** lub **LVS_EX_TWOCLICKACTIVATE.**

## <a name="see-also"></a>Zobacz też

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Formanty](../mfc/controls-mfc.md)
