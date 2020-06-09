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
ms.openlocfilehash: 6b1155945c4248c5ac2755d60d8887f890e6d324
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618299"
---
# <a name="mapping-windows-messages-to-your-class"></a>Mapowanie komunikatów systemu Windows na klasę

Jeśli potrzebujesz okna dialogowego do obsługi komunikatów systemu Windows, Zastąp odpowiednie funkcje obsługi. Aby to zrobić, wybierz kartę **Widok klasy** w **Eksplorator rozwiązań**, kliknij prawym przyciskiem myszy klasę, która reprezentuje okno dialogowe, a następnie wybierz polecenie [Kreator klas](reference/mfc-class-wizard.md). Użyj kreatora, aby [zamapować komunikaty](reference/mapping-messages-to-functions.md) do klasy okna dialogowego. Spowoduje to zapisanie wpisu mapy komunikatów dla każdego komunikatu i dodanie funkcji składowych obsługi komunikatów do klasy. Użyj edytora kodu, aby napisać kod w programach obsługi komunikatów.

Można również przesłonić funkcje składowe [CDialog](reference/cdialog-class.md) i jej klas podstawowych, szczególnie [CWnd](reference/cwnd-class.md).

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Obsługa i mapowanie komunikatów](message-handling-and-mapping.md)

- [Powszechnie zastępowane funkcje członkowskie](commonly-overridden-member-functions.md)

- [Powszechnie dodawane funkcje członkowskie](commonly-added-member-functions.md)

## <a name="see-also"></a>Zobacz też

[Okna dialogowe](dialog-boxes.md)<br/>
[Praca z oknami dialogowymi w MFC](life-cycle-of-a-dialog-box.md)
