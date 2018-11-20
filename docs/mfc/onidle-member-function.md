---
title: OnIdle — Funkcja członkowska
ms.date: 11/19/2018
f1_keywords:
- OnIdle
helpviewer_keywords:
- processing messages [MFC]
- OnIdle method [MFC]
- idle loop processing [MFC]
- CWinApp class [MFC], OnIdle method [MFC]
- message handling [MFC], OnIdle method [MFC]
ms.assetid: 51adc874-0075-4f76-be1c-79283f46c10b
ms.openlocfilehash: 7b3f2fbeac6ae356003abf12b5df4c54c8bb327a
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175136"
---
# <a name="onidle-member-function"></a>OnIdle — Funkcja członkowska

Podczas przetwarzania żadnych komunikatów Windows struktura wywołuje [CWinApp](../mfc/reference/cwinapp-class.md) funkcja elementu członkowskiego [OnIdle](../mfc/reference/cwinapp-class.md#onidle) (opisanej w odwołanie do biblioteki MFC).

Zastąp `OnIdle` do wykonywania zadań w tle. Domyślna wersja aktualizuje stan obiektów interfejsu użytkownika, takich jak przyciski paska narzędzi i wykonuje oczyszczania obiekty tymczasowe, utworzone przez platformę w trakcie jego działania. Na poniższym rysunku przedstawiono, jak pętli komunikatów wywołuje `OnIdle` gdy nie ma żadnych komunikatów w kolejce.

![Przetwarzanie pętli komunikatów](../mfc/media/vc387c1.gif "proces pętli komunikatów") <br/>
Pętli komunikatów

Aby uzyskać więcej informacji na temat działania w pętli bezczynności, zobacz [przetwarzanie pętli bezczynności](../mfc/idle-loop-processing.md).

## <a name="see-also"></a>Zobacz też

[CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md)
