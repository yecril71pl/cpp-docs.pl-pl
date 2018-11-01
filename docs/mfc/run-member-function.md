---
title: Uruchamianie funkcji członkowskiej
ms.date: 11/04/2016
helpviewer_keywords:
- WinMain method [MFC]
ms.assetid: 24ab7597-2354-495b-9a20-2c8ccc7385b3
ms.openlocfilehash: 8e6e74b8f0fd62f96d6d846bbba867f9189550ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666859"
---
# <a name="run-member-function"></a>Uruchamianie funkcji członkowskiej

Aplikacja framework spędza większość czasu w [Uruchom](../mfc/reference/cwinapp-class.md#run) funkcji składowej klasy typu [CWinApp](../mfc/reference/cwinapp-class.md). Po zainicjowaniu `WinMain` wywołania `Run` do przetworzenia w pętli komunikatów.

`Run` Przełączanie po kolei pętlę komunikatów sprawdzanie kolejki komunikatów dla komunikatów dostępne. Jeśli komunikat jest dostępna, `Run` wywołuje dla akcji. Jeśli nie ma wiadomości, co ma często miejsce ma wartość true, `Run` wywołania `OnIdle` celu jakiegokolwiek przetwarzania czas bezczynności (%), który framework lub może być konieczne gotowe. W przypadku żadnych komunikatów i przetwarzanie w stanie bezczynności, aby zrobić, aplikacja czeka, aż coś, co się dzieje. Po zakończeniu działania aplikacji, `Run` wywołania `ExitInstance`. Wartość w [funkcja elementu członkowskiego OnIdle](../mfc/onidle-member-function.md) zawiera sekwencję akcji w pętli komunikatów.

Wysyła komunikat zależy od rodzaju wiadomości. Aby uzyskać więcej informacji, zobacz [komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md).

## <a name="see-also"></a>Zobacz też

[CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md)
