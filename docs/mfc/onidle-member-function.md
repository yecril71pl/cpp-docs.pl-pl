---
title: OnIdle — Funkcja członkowska
ms.date: 11/04/2016
f1_keywords:
- OnIdle
helpviewer_keywords:
- processing messages [MFC]
- OnIdle method [MFC]
- idle loop processing [MFC]
- CWinApp class [MFC], OnIdle method [MFC]
- message handling [MFC], OnIdle method [MFC]
ms.assetid: 51adc874-0075-4f76-be1c-79283f46c10b
ms.openlocfilehash: 3d457c1675d5f5f3f88c67b1aac2d03509c21564
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662153"
---
# <a name="onidle-member-function"></a>OnIdle — Funkcja członkowska

Podczas przetwarzania żadnych komunikatów Windows struktura wywołuje [CWinApp](../mfc/reference/cwinapp-class.md) funkcja elementu członkowskiego [OnIdle](../mfc/reference/cwinapp-class.md#onidle) (opisanej w odwołanie do biblioteki MFC).

Zastąp `OnIdle` do wykonywania zadań w tle. Domyślna wersja aktualizuje stan obiektów interfejsu użytkownika, takich jak przyciski paska narzędzi i wykonuje oczyszczania obiekty tymczasowe, utworzone przez platformę w trakcie jego działania. Na poniższym rysunku przedstawiono, jak pętli komunikatów wywołuje `OnIdle` gdy nie ma żadnych komunikatów w kolejce.

![Przetwarzanie pętli komunikatów](../mfc/media/vc387c1.gif "vc387c1") pętli komunikatów

Aby uzyskać więcej informacji na temat działania w pętli bezczynności, zobacz [przetwarzanie pętli bezczynności](../mfc/idle-loop-processing.md).

## <a name="see-also"></a>Zobacz też

[CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md)
