---
title: Uruchamianie funkcji członkowskiej
ms.date: 11/04/2016
helpviewer_keywords:
- WinMain method [MFC]
ms.assetid: 24ab7597-2354-495b-9a20-2c8ccc7385b3
ms.openlocfilehash: 8271a10ad7439d2795dcc45d667b23b0932a0486
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271830"
---
# <a name="run-member-function"></a>Uruchamianie funkcji członkowskiej

Aplikacja framework spędza większość czasu w [Uruchom](../mfc/reference/cwinapp-class.md#run) funkcji składowej klasy typu [CWinApp](../mfc/reference/cwinapp-class.md). Po zainicjowaniu `WinMain` wywołania `Run` do przetworzenia w pętli komunikatów.

`Run` Przełączanie po kolei pętlę komunikatów sprawdzanie kolejki komunikatów dla komunikatów dostępne. Jeśli komunikat jest dostępna, `Run` wywołuje dla akcji. Jeśli nie ma wiadomości, co ma często miejsce ma wartość true, `Run` wywołania `OnIdle` celu jakiegokolwiek przetwarzania czas bezczynności (%), który framework lub może być konieczne gotowe. W przypadku żadnych komunikatów i przetwarzanie w stanie bezczynności, aby zrobić, aplikacja czeka, aż coś, co się dzieje. Po zakończeniu działania aplikacji, `Run` wywołania `ExitInstance`. Wartość w [funkcja elementu członkowskiego OnIdle](../mfc/onidle-member-function.md) zawiera sekwencję akcji w pętli komunikatów.

Wysyła komunikat zależy od rodzaju wiadomości. Aby uzyskać więcej informacji, zobacz [komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md).

## <a name="see-also"></a>Zobacz także

[CWinApp: Klasa aplikacji](../mfc/cwinapp-the-application-class.md)
