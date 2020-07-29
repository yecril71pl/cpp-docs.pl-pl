---
title: Zamykanie okna dialogowego
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
ms.openlocfilehash: ef6cdaeb4cb0d7537cda980a1d2c483c53c8dc9d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217977"
---
# <a name="closing-the-dialog-box"></a>Zamykanie okna dialogowego

Modalne okno dialogowe jest zamykane, gdy użytkownik wybierze jeden z przycisków, zazwyczaj przycisk OK lub przycisk Anuluj. Wybranie przycisku OK lub Anuluj powoduje, że system Windows wyśle do obiektu okna dialogowego komunikat z powiadomieniem o **BN_CLICKED** kontrolki z identyfikatorem przycisku ( **IDOK** lub **IDCANCEL**). `CDialog`udostępnia domyślne funkcje programu obsługi dla tych komunikatów: `OnOK` i `OnCancel` . Domyślne programy obsługi wywołują `EndDialog` funkcję członkowską, aby zamknąć okno dialogowe. Możesz również wywołać `EndDialog` z własnego kodu. Aby uzyskać więcej informacji, zobacz funkcja członkowska [zdarzenie EndDialog](reference/cdialog-class.md#enddialog) klasy `CDialog` w *Kompendium MFC*.

Aby rozmieścić Zamknij i usunąć niemodalne okno dialogowe, Przesłoń `PostNcDestroy` i Wywołaj **`delete`** operator na **`this`** wskaźniku. [Niszczenie okna dialogowego wyjaśnia,](destroying-the-dialog-box.md) co się dzieje.

## <a name="see-also"></a>Zobacz także

[Praca z oknami dialogowymi w MFC](life-cycle-of-a-dialog-box.md)
