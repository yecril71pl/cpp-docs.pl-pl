---
title: Niszczenie okna dialogowego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [MFC], deleting
- destruction, dialog box
- dialog boxes [MFC], destroying
- dialog boxes [MFC], removing
- modeless dialog boxes [MFC], destroying
- MFC dialog boxes [MFC], destroying
- modal dialog boxes [MFC], destroying
ms.assetid: dabceee7-3639-4d85-bf34-73515441b3d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 863b70f3bf4e9828d69024b838dce43abbba26be
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425915"
---
# <a name="destroying-the-dialog-box"></a>Niszczenie okna dialogowego

Modalne okna dialogowe są zwykle tworzone na ramce stosu i niszczony, kiedy kończy się funkcji, który je utworzył. Obiektu okna dialogowego destruktor jest wywoływany, gdy obiekt wykracza poza zakres.

Niemodalne okna dialogowe są zwykle tworzone i należące do okna nadrzędnego widoku lub ramki — aplikacji głównej ramki okna i okna ramki dokumentu. Wartość domyślna [OnClose](../mfc/reference/cwnd-class.md#onclose) obsługi zdarzeń wywołuje [destroywindow —](../mfc/reference/cwnd-class.md#destroywindow), co niszczy okno dialogowe. Jeśli okno dialogowe to samodzielnie, przy użyciu żadnych wskaźników albo innej semantyki specjalne prawa własności, należy zastąpić [postncdestroy —](../mfc/reference/cwnd-class.md#postncdestroy) do zniszczenia obiektu języka C++ w oknie dialogowym. Należy również zastąpić [OnCancel](../mfc/reference/cdialog-class.md#oncancel) i wywołać `DestroyWindow` z znajdujący się w nim. W przeciwnym razie właściciela okna dialogowego należy zniszczyć obiektu języka C++, gdy nie jest już konieczne.

## <a name="see-also"></a>Zobacz też

[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)

