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
ms.openlocfilehash: 9b1244b03dc3f6f418730dd782050448f3bf8934
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621916"
---
# <a name="destroying-the-dialog-box"></a>Niszczenie okna dialogowego

Modalne okna dialogowe są zwykle tworzone w ramce stosu i niszczone, gdy zostanie ona zakończona. Destruktor obiektu okna dialogowego jest wywoływany, gdy obiekt wykracza poza zakres.

Niemodalne okna dialogowe są zwykle tworzone i są własnością widoku nadrzędnego lub okna ramki — głównego okna ramki aplikacji lub okna ramki dokumentu. Domyślna procedura obsługi [OnClose](reference/cwnd-class.md#onclose) wywołuje [DestroyWindow](reference/cwnd-class.md#destroywindow), co niszczy okno dialogowe. Jeśli okno dialogowe jest samodzielne, bez wskaźników do niego ani do innej semantyki specjalnej własności, należy przesłonić [PostNcDestroy](reference/cwnd-class.md#postncdestroy) , aby zniszczyć obiekt okna dialogowego języka C++. Należy również przesłonić [OnCancel](reference/cdialog-class.md#oncancel) i wywołać `DestroyWindow` je. Jeśli nie, właściciel okna dialogowego powinien zniszczyć obiekt C++, gdy nie jest już potrzebny.

## <a name="see-also"></a>Zobacz też

[Praca z oknami dialogowymi w MFC](life-cycle-of-a-dialog-box.md)
