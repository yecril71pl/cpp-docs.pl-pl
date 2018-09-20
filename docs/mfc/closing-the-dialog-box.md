---
title: Zamykanie okna dialogowego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e9ad4b8af63b68912c232767bf1fd14070fda261
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409054"
---
# <a name="closing-the-dialog-box"></a>Zamykanie okna dialogowego

Modalne okno dialogowe zostanie zamknięte, gdy użytkownik wybierze jeden z jej przyciski, zazwyczaj przycisk OK lub przycisk Anuluj. Wybierając przycisk OK lub przycisk Anuluj, powoduje, że Windows wysłać obiektu okna dialogowego **BN_CLICKED** kontroli powiadomienie za pomocą przycisku przez identyfikator, albo **IDOK** lub **IDCANCEL**. `CDialog` udostępnia domyślne, funkcje obsługi komunikatów: `OnOK` i `OnCancel`. Wywołanie procedury obsługi domyślne `EndDialog` funkcja elementu członkowskiego, aby zamknąć okno dialogowe. Można również wywołać `EndDialog` z własnego kodu. Aby uzyskać więcej informacji, zobacz [EndDialog](../mfc/reference/cdialog-class.md#enddialog) funkcji składowej klasy typu `CDialog` w *odwołanie MFC*.

Aby rozmieścić zamykania i usuwania niemodalnego okna dialogowego, należy zastąpić `PostNcDestroy` i wywoływać **Usuń** operatora na **to** wskaźnika. [Niszczenie okna dialogowego](../mfc/destroying-the-dialog-box.md) wyjaśnia, co dzieje się potem.

## <a name="see-also"></a>Zobacz też

[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)

