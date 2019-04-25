---
title: Niszczenie okna dialogowego
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], deleting
- destruction, dialog box
- dialog boxes [MFC], destroying
- dialog boxes [MFC], removing
- modeless dialog boxes [MFC], destroying
- MFC dialog boxes [MFC], destroying
- modal dialog boxes [MFC], destroying
ms.assetid: dabceee7-3639-4d85-bf34-73515441b3d0
ms.openlocfilehash: 84ae5b336bb8eeac4f8ab7b6e5b9f00246f9ca15
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62254309"
---
# <a name="destroying-the-dialog-box"></a>Niszczenie okna dialogowego

Modalne okna dialogowe są zwykle tworzone na ramce stosu i niszczony, kiedy kończy się funkcji, który je utworzył. Obiektu okna dialogowego destruktor jest wywoływany, gdy obiekt wykracza poza zakres.

Niemodalne okna dialogowe są zwykle tworzone i należące do okna nadrzędnego widoku lub ramki — aplikacji głównej ramki okna i okna ramki dokumentu. Wartość domyślna [OnClose](../mfc/reference/cwnd-class.md#onclose) obsługi zdarzeń wywołuje [destroywindow —](../mfc/reference/cwnd-class.md#destroywindow), co niszczy okno dialogowe. Jeśli okno dialogowe to samodzielnie, przy użyciu żadnych wskaźników albo innej semantyki specjalne prawa własności, należy zastąpić [postncdestroy —](../mfc/reference/cwnd-class.md#postncdestroy) do zniszczenia obiektu języka C++ w oknie dialogowym. Należy również zastąpić [OnCancel](../mfc/reference/cdialog-class.md#oncancel) i wywołać `DestroyWindow` z znajdujący się w nim. W przeciwnym razie właściciela okna dialogowego należy zniszczyć obiektu języka C++, gdy nie jest już konieczne.

## <a name="see-also"></a>Zobacz także

[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)
