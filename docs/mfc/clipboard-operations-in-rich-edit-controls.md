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
ms.openlocfilehash: 3dea112ed32ae618991f6ff5f05823bd5be001b6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624858"
---
# <a name="clipboard-operations-in-rich-edit-controls"></a>Operacje schowka w formantach edycji wzbogaconej

Aplikacja może wkleić zawartość schowka do kontrolki edycji wzbogaconej ([CRichEditCtrl](reference/cricheditctrl-class.md)) przy użyciu najlepszego dostępnego formatu Schowka lub określonego formatu Schowka. Można również określić, czy wzbogacona kontrolka edycji umożliwia wklejenie formatu Schowka.

Możesz skopiować lub wyciąć zawartość bieżącego zaznaczenia przy użyciu funkcji [kopiowania](reference/cricheditctrl-class.md#copy) lub [wycinania](reference/cricheditctrl-class.md#cut) elementu członkowskiego. Podobnie można wkleić zawartość schowka do kontrolki edycji wzbogaconej przy użyciu funkcji [Wklej](reference/cricheditctrl-class.md#paste) element członkowski. Formant wkleja pierwszy dostępny format, który jest rozpoznawany, który najprawdopodobniej jest najbardziej opisowym formatem.

Aby wkleić określony format schowka, można użyć funkcji składowej [PasteSpecial](reference/cricheditctrl-class.md#pastespecial) . Ta funkcja jest przydatna w przypadku aplikacji z poleceniem Wklej specjalnie, które umożliwia użytkownikowi wybranie formatu Schowka. Można użyć funkcji elementu członkowskiego, aby [określić, czy](reference/cricheditctrl-class.md#canpaste) dany format jest rozpoznawany przez formant.

Można również użyć, `CanPaste` Aby określić, czy dowolny dostępny format Schowka jest rozpoznawany przez kontrolkę edycji wzbogaconej. Ta funkcja jest przydatna w programie `OnInitMenuPopup` obsługi. Aplikacja może włączyć lub szaro polecenie wklejenia w zależności od tego, czy kontrolka może wkleić dowolny dostępny format.

Kontrolki edycji wzbogaconej rejestrują dwa formaty schowka: format tekstu sformatowanego i format o nazwie RichEdit tekst i obiekty. Aplikacja może zarejestrować te formaty przy użyciu funkcji [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) , określając wartości **CF_RTF** i **CF_RETEXTOBJ** .

## <a name="see-also"></a>Zobacz też

[Korzystanie z CRichEditCtrl](using-cricheditctrl.md)<br/>
[Formanty](controls-mfc.md)
