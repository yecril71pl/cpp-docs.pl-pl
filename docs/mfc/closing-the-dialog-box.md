---
title: Zamykanie okna dialogowego
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
ms.openlocfilehash: 48ea954552b3ea9aa7193a47fc2a66d731312d77
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685374"
---
# <a name="closing-the-dialog-box"></a>Zamykanie okna dialogowego

Modalne okno dialogowe jest zamykane, gdy użytkownik wybierze jeden z przycisków, zazwyczaj przycisk OK lub przycisk Anuluj. Wybranie przycisku OK lub Anuluj powoduje, że system Windows wysyła do obiektu okna dialogowego komunikat z powiadomieniem **BN_CLICKED** o identyfikatorze przycisku, **IDOK** lub **IDCANCEL**. `CDialog` udostępnia domyślne funkcje programu obsługi dla tych komunikatów: `OnOK` i `OnCancel`. Domyślne programy obsługi wywołują funkcję członkowską `EndDialog`, aby zamknąć okno dialogowe. Możesz również wywołać `EndDialog` z własnego kodu. Aby uzyskać więcej informacji, zobacz [zdarzenie EndDialog](../mfc/reference/cdialog-class.md#enddialog) funkcja członkowska klasy `CDialog` w *Kompendium MFC*.

Aby rozmieścić Zamknij i usunąć niemodalne okno dialogowe, Przesłoń `PostNcDestroy` i Wywołaj operator **delete** na **tym** wskaźniku. [Niszczenie okna dialogowego wyjaśnia,](../mfc/destroying-the-dialog-box.md) co się dzieje.

## <a name="see-also"></a>Zobacz także

[Praca z polami okna dialogowego w MFC](../mfc/life-cycle-of-a-dialog-box.md)
