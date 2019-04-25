---
title: Zamykanie okna dialogowego
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
ms.openlocfilehash: 07e4159eccde1fab89d4a5ffadee4e6d11fc20f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326849"
---
# <a name="closing-the-dialog-box"></a>Zamykanie okna dialogowego

Modalne okno dialogowe zostanie zamknięte, gdy użytkownik wybierze jeden z jej przyciski, zazwyczaj przycisk OK lub przycisk Anuluj. Wybierając przycisk OK lub przycisk Anuluj, powoduje, że Windows wysłać obiektu okna dialogowego **BN_CLICKED** kontroli powiadomienie za pomocą przycisku przez identyfikator, albo **IDOK** lub **IDCANCEL**. `CDialog` udostępnia domyślne, funkcje obsługi komunikatów: `OnOK` i `OnCancel`. Wywołanie procedury obsługi domyślne `EndDialog` funkcja elementu członkowskiego, aby zamknąć okno dialogowe. Można również wywołać `EndDialog` z własnego kodu. Aby uzyskać więcej informacji, zobacz [EndDialog](../mfc/reference/cdialog-class.md#enddialog) funkcji składowej klasy typu `CDialog` w *odwołanie MFC*.

Aby rozmieścić zamykania i usuwania niemodalnego okna dialogowego, należy zastąpić `PostNcDestroy` i wywoływać **Usuń** operatora na **to** wskaźnika. [Niszczenie okna dialogowego](../mfc/destroying-the-dialog-box.md) wyjaśnia, co dzieje się potem.

## <a name="see-also"></a>Zobacz także

[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)
