---
title: Praca z polami okna dialogowego w MFC
ms.date: 09/27/2019
helpviewer_keywords:
- dialog boxes [MFC], life cycle
- modal dialog boxes [MFC], life cycle
- modeless dialog boxes [MFC], life cycle
- MFC dialog boxes [MFC], life cycle
- life cycle of dialog boxes [MFC]
ms.assetid: e16fd78e-238d-4f31-8c9d-8564f3953bd9
ms.openlocfilehash: ad15250cf9a8dd663072cf9423263260bbb40a0e
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685733"
---
# <a name="working-with-dialog-boxes-in-mfc"></a>Praca z polami okna dialogowego w MFC

Podczas cyklu życia okna dialogowego użytkownik wywołuje okno dialogowe, zwykle wewnątrz procedury obsługi poleceń, która tworzy i inicjuje obiekt okna dialogowego, użytkownik współdziała z oknem dialogowym, a następnie okno dialogowe zostanie zamknięte.

W przypadku modalnych okien dialogowych program obsługi zbiera wszystkie dane wprowadzone przez użytkownika po zamknięciu okna dialogowego. Ponieważ obiekt okna dialogowego istnieje po zamknięciu okna dialogowego, można po prostu użyć zmiennych składowych klasy okna dialogowego, aby wyodrębnić dane.

W przypadku niemodalnych okien dialogowych można często wyodrębnić dane z obiektu okna dialogowego, gdy okno dialogowe jest wciąż widoczne. W pewnym momencie obiekt okna dialogowego zostaje zniszczony; gdy tak się stanie, zależy od kodu.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Tworzenie i wyświetlanie okien dialogowych](../mfc/creating-and-displaying-dialog-boxes.md)

- [Tworzenie modalnych okien dialogowych](../mfc/creating-modal-dialog-boxes.md)

- [Tworzenie niemodalnych okien dialogowych](../mfc/creating-modeless-dialog-boxes.md)

- [Używanie szablonu okna dialogowego w pamięci](../mfc/using-a-dialog-template-in-memory.md)

- [Ustawianie koloru tła okna dialogowego](../mfc/setting-the-dialog-boxs-background-color.md)

- [Inicjowanie okna dialogowego](../mfc/initializing-the-dialog-box.md)

- [Obsługa komunikatów systemu Windows w oknie dialogowym](../mfc/handling-windows-messages-in-your-dialog-box.md)

- [Pobieranie danych z obiektu okna dialogowego](../mfc/retrieving-data-from-the-dialog-object.md)

- [Zamykanie okna dialogowego](../mfc/closing-the-dialog-box.md)

- [Niszczenie okna dialogowego](../mfc/destroying-the-dialog-box.md)

- [Wymiana danych okna dialogowego (DDX) i walidacja (DDV)](../mfc/dialog-data-exchange-and-validation.md)

- [Okna dialogowe arkusza właściwości](../mfc/property-sheets-and-property-pages-mfc.md)

## <a name="see-also"></a>Zobacz także

[Okna dialogowe](../mfc/dialog-boxes.md)
