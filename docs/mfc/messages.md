---
title: Komunikaty
ms.date: 11/04/2016
helpviewer_keywords:
- messages, MFC
- messages [MFC]
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
ms.openlocfilehash: 033edfd289ea075b89e9d44111da94b987177470
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434544"
---
# <a name="messages"></a>Komunikaty

Pętli komunikatów w `Run` funkcji składowej klasy typu `CWinApp` pobiera komunikaty generowane przez różne zdarzenia w kolejce. Na przykład gdy użytkownik kliknie przycisk myszy, Windows wysyła kilka myszy komunikatów, takie jak WM_LBUTTONDOWN po naciśnięciu lewego przycisku myszy i WM_LBUTTONUP po zwolnieniu lewego przycisku myszy. Implementacja struktury pętli komunikatów dla aplikacji wysyła komunikat do odpowiedniego okna.

Kategorie ważne wiadomości są opisane w [kategorie komunikatów](../mfc/message-categories.md).

## <a name="see-also"></a>Zobacz też

[Komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md)

