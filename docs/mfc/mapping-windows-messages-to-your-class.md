---
title: Mapowanie komunikatów systemu Windows na klasę
ms.date: 09/06/2019
helpviewer_keywords:
- MFC dialog boxes [MFC], Windows messages
- message maps [MFC], in dialog class
- Windows messages [MFC], mapping in dialog classes
- messages to dialog class [MFC]
- mappings [MFC], messages to dialog class [MFC]
- message maps [MFC], mapping Windows messages to classes
- messages to dialog class [MFC], mapping
- Class Wizard [MFC]
ms.assetid: a4c6fd1f-1d33-47c9-baa0-001755746d6d
ms.openlocfilehash: 49d1a888b148793f82cf214637956589d6b8ff07
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907475"
---
# <a name="mapping-windows-messages-to-your-class"></a>Mapowanie komunikatów systemu Windows na klasę

Jeśli potrzebujesz okna dialogowego do obsługi komunikatów systemu Windows, Zastąp odpowiednie funkcje obsługi. Aby to zrobić, wybierz kartę **Widok klasy** w **Eksplorator rozwiązań**, kliknij prawym przyciskiem myszy klasę, która reprezentuje okno dialogowe, a następnie wybierz polecenie [Kreator klas](reference/mfc-class-wizard.md). Użyj kreatora, aby [zamapować komunikaty](../mfc/reference/mapping-messages-to-functions.md) do klasy okna dialogowego. Spowoduje to zapisanie wpisu mapy komunikatów dla każdego komunikatu i dodanie funkcji składowych obsługi komunikatów do klasy. Użyj edytora kodu, aby napisać kod w programach obsługi komunikatów.

Można również przesłonić funkcje składowe [CDialog](../mfc/reference/cdialog-class.md) i jej klas podstawowych, szczególnie [CWnd](../mfc/reference/cwnd-class.md).

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Obsługa i mapowanie komunikatów](../mfc/message-handling-and-mapping.md)

- [Powszechnie zastępowane funkcje członkowskie](../mfc/commonly-overridden-member-functions.md)

- [Powszechnie dodawane funkcje członkowskie](../mfc/commonly-added-member-functions.md)

## <a name="see-also"></a>Zobacz także

[Okna dialogowe](../mfc/dialog-boxes.md)<br/>
[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)
