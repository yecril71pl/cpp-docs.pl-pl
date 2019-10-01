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
ms.openlocfilehash: 8b407c6e832dde7a5865146e7cc12d1840d3234a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685847"
---
# <a name="destroying-the-dialog-box"></a>Niszczenie okna dialogowego

Modalne okna dialogowe są zwykle tworzone w ramce stosu i niszczone, gdy zostanie ona zakończona. Destruktor obiektu okna dialogowego jest wywoływany, gdy obiekt wykracza poza zakres.

Niemodalne okna dialogowe są zwykle tworzone i są własnością widoku nadrzędnego lub okna ramki — głównego okna ramki aplikacji lub okna ramki dokumentu. Domyślna procedura obsługi [OnClose](../mfc/reference/cwnd-class.md#onclose) wywołuje [DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow), co niszczy okno dialogowe. Jeśli okno dialogowe jest samodzielne, bez wskaźników do niego ani do innej semantyki specjalnej własności, należy przesłonić [PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy) , aby zniszczyć C++ obiekt okna dialogowego. Należy również zastąpić [OnCancel](../mfc/reference/cdialog-class.md#oncancel) i wywołać `DestroyWindow` z tego poziomu. Jeśli nie, właściciel okna dialogowego powinien zniszczyć obiekt, C++ gdy nie jest już potrzebny.

## <a name="see-also"></a>Zobacz także

[Praca z polami okna dialogowego w MFC](../mfc/life-cycle-of-a-dialog-box.md)
