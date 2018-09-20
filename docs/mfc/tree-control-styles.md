---
title: Style kontrolki drzewa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TVS_SINGLEEXPAND
- TVS_LINESATROOT
- TVS_HASBUTTONS
- TVS_NOTOOLTIPS
- TVS_HASLINES
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ef7c24fb321594c64afe45e1902676f43afd3e9b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412674"
---
# <a name="tree-control-styles"></a>Style kontrolki drzewa

Kontrolki drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) Style określają aspekty wyglądu formantu drzewa. Możesz ustawić style początkowej podczas tworzenia kontrolki drzewa. Możesz pobrać i zmieniać style po utworzeniu kontrolki drzewa za pomocą [GetWindowLong](/windows/desktop/api/winuser/nf-winuser-getwindowlonga) i [SetWindowLong](/windows/desktop/api/winuser/nf-winuser-setwindowlonga) funkcje Windows, określając **GWL_STYLE** dla *nIndex* parametru. Aby uzyskać pełną listę style, zobacz [Style okna kontrolki widoku drzewa](/windows/desktop/Controls/tree-view-control-window-styles) w zestawie Windows SDK.

**TVS_HASLINES** styl zwiększa graficzną reprezentację kontrolką drzewa hierarchii za pomocą rysowania wiersze, które łączą elementy podrzędne do ich odpowiedniego elementu nadrzędnego. Ten styl nie łączy się elementy w folderze głównym hierarchii. Aby to zrobić, trzeba połączyć **TVS_HASLINES** i **TVS_LINESATROOT** style.

Użytkownika można rozwinąć lub zwinąć listę elementów podrzędnych elementu nadrzędnego, klikając dwukrotnie plik elementu nadrzędnego. Kontrolka drzewa, która ma **TVS_SINGLEEXPAND** stylu powoduje, że element wybrane do rozwijania i elementu jest usunięto zaznaczenie, aby zwinąć. Jeśli przycisk myszy jest używany do wybranego elementu jednym kliknięciem i ten element jest zamknięty, zostanie rozszerzona. Wybrany element jest kliknięte po otwarciu, będzie zwinięte.

Kontrolka drzewa, która ma **TVS_HASBUTTONS** stylów dodaje przycisk do po lewej stronie każdego elementu nadrzędnego. Użytkownik może kliknąć przycisk, aby rozwinąć lub zwinąć elementów podrzędnych jako alternatywę dla dwukrotnie element nadrzędny. **TVS_HASBUTTONS** nie powoduje dodania przycisków do elementów w folderze głównym hierarchii. Aby to zrobić, należy połączyć **TVS_HASLINES**, **TVS_LINESATROOT**, i **TVS_HASBUTTONS**.

**TVS_EDITLABELS** style umożliwia użytkownikowi edytowanie etykiety elementów kontrolki drzewa. Aby uzyskać więcej informacji na temat edytowania etykiet, zobacz [Edytowanie etykiet kontrolki drzewa](../mfc/tree-control-label-editing.md) w dalszej części tego tematu.

**TVS_NOTOOLTIPS** styl wyłącza funkcję Porada automatyczne narzędzia z kontrolki widoku drzewa. Ta funkcja automatycznie wyświetla etykietki narzędzia, zawierające tytuł elementu pod kursorem myszy, jeśli cały tytuł nie jest aktualnie widoczne.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

