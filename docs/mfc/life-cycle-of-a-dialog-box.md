---
title: Cykl życiowy okna dialogowego
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], life cycle
- modal dialog boxes [MFC], life cycle
- modeless dialog boxes [MFC], life cycle
- MFC dialog boxes [MFC], life cycle
- life cycle of dialog boxes [MFC]
ms.assetid: e16fd78e-238d-4f31-8c9d-8564f3953bd9
ms.openlocfilehash: a3772a180e35a57c997446fcf2268d84bec2daa5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62365345"
---
# <a name="life-cycle-of-a-dialog-box"></a>Cykl życiowy okna dialogowego

Podczas cyklu życia okno dialogowe użytkownik wywoła okno dialogowe, zwykle wewnątrz procedury obsługi do polecenia, które tworzy i inicjuje obiekt okna dialogowego, użytkownik wchodzi w interakcję z okna dialogowego i zamyka okno dialogowe.

Modalne okno dialogowe pól programu obsługi zbiera wszystkie dane które użytkownik wprowadził po zamknięciu okna dialogowego. Ponieważ obiektu okna dialogowego istnieje, po jego okno dialogowe zostało zamknięte, możesz po prostu użyć zmienne składowe klasy okien dialogowych do wyodrębnienia danych.

Dla Niemodalne okna dialogowe może być często wyodrębniania danych z obiektu okna dialogowego, gdy okno dialogowe jest jeszcze widoczny. W pewnym momencie obiektu okna dialogowego zostanie zniszczony; w takim przypadku zależy od kodu.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Tworzenie i wyświetlanie okien dialogowych](../mfc/creating-and-displaying-dialog-boxes.md)

- [Tworzenie modalnych okien dialogowych](../mfc/creating-modal-dialog-boxes.md)

- [Tworzenie niemodalnych okien dialogowych](../mfc/creating-modeless-dialog-boxes.md)

- [Używanie szablonu okna dialogowego w pamięci](../mfc/using-a-dialog-template-in-memory.md)

- [Ustawianie koloru tła okna dialogowego](../mfc/setting-the-dialog-boxs-background-color.md)

- [Inicjowanie okna dialogowego](../mfc/initializing-the-dialog-box.md)

- [Obsługa komunikatów Windows w oknie dialogowym](../mfc/handling-windows-messages-in-your-dialog-box.md)

- [Trwa pobieranie danych z obiektu okna dialogowego](../mfc/retrieving-data-from-the-dialog-object.md)

- [Zamykanie okna dialogowego](../mfc/closing-the-dialog-box.md)

- [Niszczenie okna dialogowego](../mfc/destroying-the-dialog-box.md)

- [Wymiana danych okna dialogowego (DDX) i sprawdzania poprawności (DDV)](../mfc/dialog-data-exchange-and-validation.md)

- [Okna dialogowe arkusza właściwości](../mfc/property-sheets-and-property-pages-mfc.md)

## <a name="see-also"></a>Zobacz także

[Okna dialogowe](../mfc/dialog-boxes.md)
