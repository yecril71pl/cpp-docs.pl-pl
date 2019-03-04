---
title: Bieżące zaznaczenie w formancie edycji wzbogaconej
ms.date: 11/04/2016
helpviewer_keywords:
- current selection in CRichEditCtrls
- CRichEditCtrl class [MFC], current selection in
- rich edit controls [MFC], current selection in
- selection, current in CRichEditCtrl
ms.assetid: f6b2a2b6-5481-4ad3-9720-6dd772ea6fc8
ms.openlocfilehash: 4516c4506419169ac3ab284e6c59cae71595be59
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57286867"
---
# <a name="current-selection-in-a-rich-edit-control"></a>Bieżące zaznaczenie w formancie edycji wzbogaconej

Użytkownik może wybrać tekstu w formancie edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) przy użyciu myszy lub klawiatury. Bieżące zaznaczenie jest zakresu znaków wybranego lub pozycji punktu wstawiania, jeśli żadne znaki nie są wybrane. Aplikację można uzyskać informacje na temat bieżącego zaznaczenia, Ustaw bieżące zaznaczenie, określić, kiedy Zaznacz bieżące zaznaczenie zmiany i Pokaż lub Ukryj zaznaczenie.

Aby określić bieżące zaznaczenie w formancie edycji wzbogaconej, użyj [GetSel](../mfc/reference/cricheditctrl-class.md#getsel) funkcja elementu członkowskiego. Aby ustawić bieżącego zaznaczenia, użyj [SetSel](../mfc/reference/cricheditctrl-class.md#setsel) funkcja elementu członkowskiego. [CHARRANGE](/windows/desktop/api/richedit/ns-richedit-_charrange) struktury służy do określania zakresu znaków za pomocą tych funkcji. Aby pobrać informacje o zawartości bieżącego zaznaczenia, można użyć [GetSelectionType](../mfc/reference/cricheditctrl-class.md#getselectiontype) funkcja elementu członkowskiego.

Domyślnie przez kontrolki edycji wzbogaconej pokazuje i ukrywa wyróżnienie wybór, gdy uzyskuje i traci fokus. Możesz pokazać lub ukryć wyróżnienie wybór w dowolnym momencie za pomocą [HideSelection](../mfc/reference/cricheditctrl-class.md#hideselection) funkcja elementu członkowskiego. Na przykład aplikacja może zawierać okno dialogowe Wyszukiwanie, aby wyszukać tekst w kontrolce edycji wzbogaconej. Aplikacja może wybrać pasujący tekst i bez konieczności zamykania okna dialogowego, w którym to przypadku należy użyć `HideSelection` zaznaczenie.

Aby uzyskać zaznaczonego tekstu w formancie edycji wzbogaconej, użyj [GetSelText](../mfc/reference/cricheditctrl-class.md#getseltext) funkcja elementu członkowskiego. Tekst jest kopiowany do określoną tablicę znaków. Należy się upewnić, że tablica jest wystarczająco duży, aby pomieścić zaznaczonego tekstu, a także kończącego znaku null.

Możesz wyszukać ciąg znaków w kontrolce edycji wzbogaconej przy użyciu [FindText](../mfc/reference/cricheditctrl-class.md#findtext) funkcja elementu członkowskiego [FINDTEXTEX](/windows/desktop/api/richedit/ns-richedit-_findtextexa) struktury używane z tą funkcją określa zakres tekstu do wyszukiwania i ciąg do wyszukania. Można również określić opcje, takie jak tego, czy w wyszukiwaniu jest uwzględniana wielkość liter.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
