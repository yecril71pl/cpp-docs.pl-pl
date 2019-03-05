---
title: Mapowanie komunikatów systemu Windows na klasę
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], Windows messages
- message maps [MFC], in dialog class
- Windows messages [MFC], mapping in dialog classes
- messages to dialog class [MFC]
- mappings [MFC], messages to dialog class [MFC]
- message maps [MFC], mapping Windows messages to classes
- messages to dialog class [MFC], mapping
ms.assetid: a4c6fd1f-1d33-47c9-baa0-001755746d6d
ms.openlocfilehash: 7e15f52e41d4ac91a839629342258128db86e2d5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326676"
---
# <a name="mapping-windows-messages-to-your-class"></a>Mapowanie komunikatów systemu Windows na klasę

Jeśli potrzebujesz dialogowym może obsługiwać komunikaty Windows, musi zostać zastąpiona funkcje odpowiedni program obsługi. Aby to zrobić, użyj okna właściwości [mapy wiadomości](../mfc/reference/mapping-messages-to-functions.md) do klasy okien dialogowych. Zapisuje wpis mapy komunikatów dla każdego komunikatu i dodaje funkcje Członkowskie obsługi wiadomości do klasy. Edytor kodu źródłowego języka Visual C++ umożliwia pisanie kodu w obsługi komunikatów.

Możesz też przesłonić funkcje elementów członkowskich [CDialog](../mfc/reference/cdialog-class.md) i jej klasy bazowe, szczególnie [CWnd](../mfc/reference/cwnd-class.md).

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Obsługa i mapowanie komunikatów](../mfc/message-handling-and-mapping.md)

- [Powszechnie zastępowane funkcje Członkowskie](../mfc/commonly-overridden-member-functions.md)

- [Powszechnie dodawane funkcje Członkowskie](../mfc/commonly-added-member-functions.md)

## <a name="see-also"></a>Zobacz także

[Okna dialogowe](../mfc/dialog-boxes.md)<br/>
[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)
