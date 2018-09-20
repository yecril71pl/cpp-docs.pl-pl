---
title: Komunikaty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- messages, MFC
- messages [MFC]
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f25c9cc70cec598f975bbd242af83597311bdc7c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392258"
---
# <a name="messages"></a>Komunikaty

Pętli komunikatów w `Run` funkcji składowej klasy typu `CWinApp` pobiera komunikaty generowane przez różne zdarzenia w kolejce. Na przykład gdy użytkownik kliknie przycisk myszy, Windows wysyła kilka myszy komunikatów, takie jak WM_LBUTTONDOWN po naciśnięciu lewego przycisku myszy i WM_LBUTTONUP po zwolnieniu lewego przycisku myszy. Implementacja struktury pętli komunikatów dla aplikacji wysyła komunikat do odpowiedniego okna.

Kategorie ważne wiadomości są opisane w [kategorie komunikatów](../mfc/message-categories.md).

## <a name="see-also"></a>Zobacz też

[Komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md)

