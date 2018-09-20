---
title: Bieżące zaznaczenie w formancie edycji wzbogaconej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- current selection in CRichEditCtrls
- CRichEditCtrl class [MFC], current selection in
- rich edit controls [MFC], current selection in
- selection, current in CRichEditCtrl
ms.assetid: f6b2a2b6-5481-4ad3-9720-6dd772ea6fc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c5870c7c3352a53d85bdd15020a1e7f535ef6efc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403672"
---
# <a name="current-selection-in-a-rich-edit-control"></a>Bieżące zaznaczenie w formancie edycji wzbogaconej

Użytkownik może wybrać tekstu w formancie edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) przy użyciu myszy lub klawiatury. Bieżące zaznaczenie jest zakresu znaków wybranego lub pozycji punktu wstawiania, jeśli żadne znaki nie są wybrane. Aplikację można uzyskać informacje na temat bieżącego zaznaczenia, Ustaw bieżące zaznaczenie, określić, kiedy Zaznacz bieżące zaznaczenie zmiany i Pokaż lub Ukryj zaznaczenie.

Aby określić bieżące zaznaczenie w formancie edycji wzbogaconej, użyj [GetSel](../mfc/reference/cricheditctrl-class.md#getsel) funkcja elementu członkowskiego. Aby ustawić bieżącego zaznaczenia, użyj [SetSel](../mfc/reference/cricheditctrl-class.md#setsel) funkcja elementu członkowskiego. [CHARRANGE](/windows/desktop/api/richedit/ns-richedit-_charrange) struktury służy do określania zakresu znaków za pomocą tych funkcji. Aby pobrać informacje o zawartości bieżącego zaznaczenia, można użyć [GetSelectionType](../mfc/reference/cricheditctrl-class.md#getselectiontype) funkcja elementu członkowskiego.

Domyślnie przez kontrolki edycji wzbogaconej pokazuje i ukrywa wyróżnienie wybór, gdy uzyskuje i traci fokus. Możesz pokazać lub ukryć wyróżnienie wybór w dowolnym momencie za pomocą [HideSelection](../mfc/reference/cricheditctrl-class.md#hideselection) funkcja elementu członkowskiego. Na przykład aplikacja może zawierać okno dialogowe Wyszukiwanie, aby wyszukać tekst w kontrolce edycji wzbogaconej. Aplikacja może wybrać pasujący tekst i bez konieczności zamykania okna dialogowego, w którym to przypadku należy użyć `HideSelection` zaznaczenie.

Aby uzyskać zaznaczonego tekstu w formancie edycji wzbogaconej, użyj [GetSelText](../mfc/reference/cricheditctrl-class.md#getseltext) funkcja elementu członkowskiego. Tekst jest kopiowany do określoną tablicę znaków. Należy się upewnić, że tablica jest wystarczająco duży, aby pomieścić zaznaczonego tekstu, a także kończącego znaku null.

Możesz wyszukać ciąg znaków w kontrolce edycji wzbogaconej przy użyciu [FindText](../mfc/reference/cricheditctrl-class.md#findtext) funkcja elementu członkowskiego [FINDTEXTEX](/windows/desktop/api/richedit/ns-richedit-_findtextexa) struktury używane z tą funkcją określa zakres tekstu do wyszukiwania i ciąg do wyszukania. Można również określić opcje, takie jak tego, czy w wyszukiwaniu jest uwzględniana wielkość liter.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

