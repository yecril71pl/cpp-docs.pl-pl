---
title: Komunikaty
ms.date: 11/04/2016
helpviewer_keywords:
- messages, MFC
- messages [MFC]
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
ms.openlocfilehash: 8e1bfd1baa8ffef76ba31912fc619c4217696683
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384130"
---
# <a name="messages"></a>Komunikaty

Pętli komunikatów w `Run` funkcji składowej klasy typu `CWinApp` pobiera komunikaty generowane przez różne zdarzenia w kolejce. Na przykład gdy użytkownik kliknie przycisk myszy, Windows wysyła kilka myszy komunikatów, takie jak WM_LBUTTONDOWN po naciśnięciu lewego przycisku myszy i WM_LBUTTONUP po zwolnieniu lewego przycisku myszy. Implementacja struktury pętli komunikatów dla aplikacji wysyła komunikat do odpowiedniego okna.

Kategorie ważne wiadomości są opisane w [kategorie komunikatów](../mfc/message-categories.md).

## <a name="see-also"></a>Zobacz także

[Komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md)
