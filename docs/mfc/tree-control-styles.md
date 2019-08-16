---
title: Style kontrolki drzewa
ms.date: 11/04/2016
f1_keywords:
- TVS_SINGLEEXPAND
- TVS_LINESATROOT
- TVS_HASBUTTONS
- TVS_NOTOOLTIPS
- TVS_HASLINES
helpviewer_keywords:
- TVS_LINESATROOT [MFC]
- styles [MFC], CTreeCtrl
- styles [MFC], tree control
- TVS_HASLINES
- TVS_SINGLEEXPAND
- CTreeCtrl class [MFC], styles
- TVS_EDITLABELS [MFC]
- TVS_NOTOOLTIPS [MFC]
- TVS_HASBUTTONS [MFC]
- tree controls [MFC], styles
ms.assetid: f43faebd-a355-479e-888a-bf0673d5e1b4
ms.openlocfilehash: f5f28025d0349e9bcd95aba50d4110d304fed376
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510939"
---
# <a name="tree-control-styles"></a>Style kontrolki drzewa

Style kontrolki drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) określają aspekty wyglądu kontrolki drzewa. Style początkowe są ustawiane podczas tworzenia kontrolki drzewa. Możesz pobrać i zmienić style po utworzeniu kontrolki drzewa przy użyciu funkcji systemu Windows [GetWindowLong](/windows/win32/api/winuser/nf-winuser-getwindowlongw) i [SetWindowLong](/windows/win32/api/winuser/nf-winuser-setwindowlongw) , określając **GWL_STYLE** dla parametru *nIndex* . Aby uzyskać pełną listę stylów, zobacz [Style okna kontrolki widoku drzewa](/windows/win32/Controls/tree-view-control-window-styles) w Windows SDK.

Styl **TVS_HASLINES** zwiększa graficzną reprezentację hierarchii kontrolki drzewa przez linie rysowania łączące elementy podrzędne z odpowiadającymi im elementami nadrzędnymi. Ten styl nie łączy elementów w elemencie głównym hierarchii. Aby to zrobić, należy połączyć style **TVS_HASLINES** i **TVS_LINESATROOT** .

Użytkownik może rozwinąć lub zwinąć listę elementów podrzędnych elementu nadrzędnego przez dwukrotne kliknięcie elementu nadrzędnego. Kontrolka drzewa, która ma styl **TVS_SINGLEEXPAND** , powoduje, że element jest wybierany do rozwinięcia i element jest usuwany w celu zwinięcia. Jeśli mysz jest używana do pojedynczego kliknięcia zaznaczonego elementu, a ten element zostanie zamknięty, zostanie rozwinięty. Jeśli wybrany element jest kliknięty po raz otwarty, zostanie zwinięty.

Kontrolka drzewa, która ma styl **TVS_HASBUTTONS** , dodaje przycisk po lewej stronie każdego elementu nadrzędnego. Użytkownik może kliknąć przycisk, aby rozwinąć lub zwinąć elementy podrzędne jako alternatywę do dwukrotnego kliknięcia elementu nadrzędnego. **TVS_HASBUTTONS** nie dodaje przycisków do elementów znajdujących się w katalogu głównym hierarchii. Aby to zrobić, należy połączyć **TVS_HASLINES**, **TVS_LINESATROOT**i **TVS_HASBUTTONS**.

Styl **TVS_EDITLABELS** umożliwia użytkownikowi edytowanie etykiet elementów kontrolki drzewa. Aby uzyskać więcej informacji na temat edytowania etykiet, zobacz sekcję [Edytowanie etykiety kontrolki drzewa](../mfc/tree-control-label-editing.md) w dalszej części tego tematu.

Styl **TVS_NOTOOLTIPS** wyłącza funkcję automatycznej etykietki narzędzia w widokach drzewa. Ta funkcja automatycznie wyświetla etykietkę narzędzia zawierającą tytuł elementu pod kursorem myszy, jeśli cały tytuł nie jest obecnie widoczny.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
