---
title: Zamykanie okna dialogowego
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
ms.openlocfilehash: a695a8e331eb8a4f22394deb65857bf93ecab41e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617207"
---
# <a name="closing-the-dialog-box"></a>Zamykanie okna dialogowego

Modalne okno dialogowe jest zamykane, gdy użytkownik wybierze jeden z przycisków, zazwyczaj przycisk OK lub przycisk Anuluj. Wybranie przycisku OK lub Anuluj powoduje, że system Windows wyśle do obiektu okna dialogowego komunikat z powiadomieniem o **BN_CLICKED** kontrolki z identyfikatorem przycisku ( **IDOK** lub **IDCANCEL**). `CDialog`udostępnia domyślne funkcje programu obsługi dla tych komunikatów: `OnOK` i `OnCancel` . Domyślne programy obsługi wywołują `EndDialog` funkcję członkowską, aby zamknąć okno dialogowe. Możesz również wywołać `EndDialog` z własnego kodu. Aby uzyskać więcej informacji, zobacz funkcja członkowska [zdarzenie EndDialog](reference/cdialog-class.md#enddialog) klasy `CDialog` w *Kompendium MFC*.

Aby rozmieścić Zamknij i usunąć niemodalne okno dialogowe, Przesłoń `PostNcDestroy` i Wywołaj operator **delete** na **tym** wskaźniku. [Niszczenie okna dialogowego wyjaśnia,](destroying-the-dialog-box.md) co się dzieje.

## <a name="see-also"></a>Zobacz też

[Praca z oknami dialogowymi w MFC](life-cycle-of-a-dialog-box.md)
