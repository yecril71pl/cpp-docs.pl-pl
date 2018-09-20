---
title: Uruchamianie funkcji członkowskiej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- WinMain method [MFC]
ms.assetid: 24ab7597-2354-495b-9a20-2c8ccc7385b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 446b1b6fc2a5265e2c4eb8a608ff8b4f0028c57d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408235"
---
# <a name="run-member-function"></a>Uruchamianie funkcji członkowskiej

Aplikacja framework spędza większość czasu w [Uruchom](../mfc/reference/cwinapp-class.md#run) funkcji składowej klasy typu [CWinApp](../mfc/reference/cwinapp-class.md). Po zainicjowaniu `WinMain` wywołania `Run` do przetworzenia w pętli komunikatów.

`Run` Przełączanie po kolei pętlę komunikatów sprawdzanie kolejki komunikatów dla komunikatów dostępne. Jeśli komunikat jest dostępna, `Run` wywołuje dla akcji. Jeśli nie ma wiadomości, co ma często miejsce ma wartość true, `Run` wywołania `OnIdle` celu jakiegokolwiek przetwarzania czas bezczynności (%), który framework lub może być konieczne gotowe. W przypadku żadnych komunikatów i przetwarzanie w stanie bezczynności, aby zrobić, aplikacja czeka, aż coś, co się dzieje. Po zakończeniu działania aplikacji, `Run` wywołania `ExitInstance`. Wartość w [funkcja elementu członkowskiego OnIdle](../mfc/onidle-member-function.md) zawiera sekwencję akcji w pętli komunikatów.

Wysyła komunikat zależy od rodzaju wiadomości. Aby uzyskać więcej informacji, zobacz [komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md).

## <a name="see-also"></a>Zobacz też

[CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md)
