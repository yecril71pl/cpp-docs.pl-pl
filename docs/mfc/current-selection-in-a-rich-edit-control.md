---
title: Bieżące zaznaczenie w formancie edycji wzbogaconej
ms.date: 11/04/2016
helpviewer_keywords:
- current selection in CRichEditCtrls
- CRichEditCtrl class [MFC], current selection in
- rich edit controls [MFC], current selection in
- selection, current in CRichEditCtrl
ms.assetid: f6b2a2b6-5481-4ad3-9720-6dd772ea6fc8
ms.openlocfilehash: 43a68d63f7888d762eee031196453eb156ecf105
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508773"
---
# <a name="current-selection-in-a-rich-edit-control"></a>Bieżące zaznaczenie w formancie edycji wzbogaconej

Użytkownik może wybrać tekst w kontrolce edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) za pomocą myszy lub klawiatury. Bieżące zaznaczenie jest zakresem wybranych znaków lub pozycją punktu wstawiania, jeśli nie są zaznaczone żadne znaki. Aplikacja może uzyskać informacje o bieżącym zaznaczeniu, ustawić bieżące zaznaczenie, określić, kiedy bieżące zaznaczenie zostanie zmienione, i pokazać lub ukryć zaznaczenie.

Aby określić bieżące zaznaczenie w formancie edycji wzbogaconej, użyj funkcji składowej [GetSel](../mfc/reference/cricheditctrl-class.md#getsel) . Aby ustawić bieżące zaznaczenie, użyj funkcji składowej [SetSel](../mfc/reference/cricheditctrl-class.md#setsel) . Struktura [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) jest używana z tymi funkcjami, aby określić zakres znaków. Aby pobrać informacje o zawartości bieżącego zaznaczenia, można użyć funkcji elementu członkowskiego GetSelectionType. [](../mfc/reference/cricheditctrl-class.md#getselectiontype)

Domyślnie kontrolka edycji wzbogaconej pokazuje i ukrywa zaznaczenie, gdy nastąpi i utraci fokus. W dowolnym momencie możesz pokazać lub ukryć zaznaczenie, używając funkcji składowej [HideSelection](../mfc/reference/cricheditctrl-class.md#hideselection) . Na przykład aplikacja może udostępnić okno dialogowe wyszukiwania, aby znaleźć tekst w kontrolce edycji wzbogaconej. Aplikacja może wybrać pasujący tekst bez zamykania okna dialogowego, w takim przypadku należy użyć `HideSelection` , aby zaznaczyć zaznaczenie.

Aby wyświetlić zaznaczony tekst w kontrolce edycji wzbogaconej, użyj funkcji składowej [GetSelText](../mfc/reference/cricheditctrl-class.md#getseltext) . Tekst jest kopiowany do określonej tablicy znaków. Należy upewnić się, że tablica jest wystarczająco duża, aby pomieścić zaznaczony tekst oraz kończący znak null.

Można wyszukać ciąg w kontrolce edycji wzbogaconej przy użyciu funkcji składowej [ciąg FindText](../mfc/reference/cricheditctrl-class.md#findtext) , która jest używana przez strukturę [FINDTEXTEX](/windows/win32/api/richedit/ns-richedit-findtextexw) z tą funkcją określa zakres tekstu do przeszukania oraz ciąg do wyszukania. Możesz również określić takie opcje, jak w przypadku wyszukiwania rozróżniana jest wielkość liter.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
