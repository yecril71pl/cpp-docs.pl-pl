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
ms.openlocfilehash: e232010b443ace245844f1c28649477cccc8e9e4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508969"
---
# <a name="clipboard-operations-in-rich-edit-controls"></a>Operacje schowka w formantach edycji wzbogaconej

Aplikacja może wkleić zawartość schowka do kontrolki edycji wzbogaconej ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) przy użyciu najlepszego dostępnego formatu Schowka lub określonego formatu Schowka. Można również określić, czy wzbogacona kontrolka edycji umożliwia wklejenie formatu Schowka.

Możesz skopiować lub wyciąć zawartość bieżącego zaznaczenia przy użyciu funkcji [kopiowania](../mfc/reference/cricheditctrl-class.md#copy) lub wycinania elementu [](../mfc/reference/cricheditctrl-class.md#cut) Członkowskiego. Podobnie można wkleić zawartość schowka do kontrolki edycji wzbogaconej przy użyciu funkcji [Wklej](../mfc/reference/cricheditctrl-class.md#paste) element członkowski. Formant wkleja pierwszy dostępny format, który jest rozpoznawany, który najprawdopodobniej jest najbardziej opisowym formatem.

Aby wkleić określony format schowka, można użyć funkcji składowej [PasteSpecial](../mfc/reference/cricheditctrl-class.md#pastespecial) . Ta funkcja jest przydatna w przypadku aplikacji z poleceniem Wklej specjalnie, które umożliwia użytkownikowi wybranie formatu Schowka. Można użyć funkcji elementu [](../mfc/reference/cricheditctrl-class.md#canpaste) Członkowskiego, aby określić, czy dany format jest rozpoznawany przez formant.

Można również użyć `CanPaste` , aby określić, czy dowolny dostępny format Schowka jest rozpoznawany przez kontrolkę edycji wzbogaconej. Ta funkcja jest przydatna w programie `OnInitMenuPopup` obsługi. Aplikacja może włączyć lub szaro polecenie wklejenia w zależności od tego, czy kontrolka może wkleić dowolny dostępny format.

Kontrolki edycji wzbogaconej rejestrują dwa formaty schowka: format tekstu sformatowanego i format o nazwie RichEdit tekst i obiekty. Aplikacja może zarejestrować te formaty przy użyciu funkcji [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) , określając wartości **CF_RTF** i **CF_RETEXTOBJ** .

## <a name="see-also"></a>Zobacz także

[Korzystanie z CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
