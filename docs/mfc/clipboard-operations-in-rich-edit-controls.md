---
title: Operacje schowka w formantach edycji wzbogaconej
ms.date: 11/04/2016
helpviewer_keywords:
- pasting Clipboard data
- CRichEditCtrl class [MFC], paste operation
- cut operation in CRichEditCtrl class [MFC]
- CRichEditCtrl class [MFC], Clipboard operations
- copy operations in rich edit controls
- Clipboard, operations in CRichEditCtrl
- rich edit controls [MFC], Clipboard operations
ms.assetid: 15ce66bc-2636-4a35-a2ae-d52285dc1af6
ms.openlocfilehash: 882c589d0d25b54650affa7fd41f916ecf6097d5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276874"
---
# <a name="clipboard-operations-in-rich-edit-controls"></a>Operacje schowka w formantach edycji wzbogaconej

Aplikację można wkleić zawartość Schowka do kontrolki edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) przy użyciu najlepszych dostępnych format Schowka lub w określonym formacie Schowka. Można również określić, czy kontrolki edycji wzbogaconej jest w stanie wklejanie format Schowka.

Można skopiować lub wyciąć zawartość bieżącego zaznaczenia przy użyciu [kopiowania](../mfc/reference/cricheditctrl-class.md#copy) lub [Wytnij](../mfc/reference/cricheditctrl-class.md#cut) funkcja elementu członkowskiego. Podobnie, Wklej zawartość Schowka w formantach edycji wzbogaconej przy użyciu [Wklej](../mfc/reference/cricheditctrl-class.md#paste) funkcja elementu członkowskiego. Kontrolka wkleja pierwszy dostępny formacie, który rozpoznaje, który prawdopodobnie jest format najbardziej opisowy.

Aby wkleić w określonym formacie Schowka, możesz użyć [PasteSpecial](../mfc/reference/cricheditctrl-class.md#pastespecial) funkcja elementu członkowskiego. Ta funkcja jest przydatne w przypadku aplikacji za pomocą polecenia Wklej specjalne, który umożliwia użytkownikowi wybranie format Schowka. Możesz użyć [CanPaste](../mfc/reference/cricheditctrl-class.md#canpaste) funkcja elementu członkowskiego, aby ustalić, czy dany format jest rozpoznawany przez formant.

Można również użyć `CanPaste` do określenia, czy wszystkie dostępne format Schowka jest rozpoznawany przez kontrolki edycji wzbogaconej. Funkcja ta jest przydatna w `OnInitMenuPopup` programu obsługi. Aplikacja może włączyć lub szary polecenia Wklej w zależności od tego, czy kontrolka można wkleić dostępnych formatów.

Bogatej edycji kontrolki rejestru dwa formaty Schowka: format tekstu sformatowanego i format nazywany RichEdit tekstu i obiektów. Aplikację można zarejestrować te formaty za pomocą [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) funkcji, określając **CF_RTF** i **CF_RETEXTOBJ** wartości.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
