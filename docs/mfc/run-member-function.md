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
ms.openlocfilehash: a658af47723a9c19218b205a17cb46919d7abd59
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932289"
---
# <a name="run-member-function"></a>Uruchamianie funkcji członkowskiej
Aplikacja framework zużywa większość czasu w [Uruchom](../mfc/reference/cwinapp-class.md#run) funkcji członkowskiej klasy [CWinApp](../mfc/reference/cwinapp-class.md). Po zainicjowaniu `WinMain` wywołania `Run` do przetworzenia w pętli komunikatów.  
  
 `Run` Przełączanie po kolei pętli komunikatów, sprawdzanie kolejki komunikatów dla komunikatów dostępne. Jeśli komunikat jest dostępna, `Run` wywołuje dla akcji. Jeśli nie ma wiadomości, która jest często ma wartość true, `Run` wywołania `OnIdle` celu żadnych przetwarzania czas bezczynności, które platformę może potrzebować gotowe. Jeśli istnieją żadnych komunikatów i przetwarzanie w stanie bezczynności, aby zrobić, aplikacja oczekuje, aż wydarzy się coś. Po zakończeniu działania aplikacji `Run` wywołania `ExitInstance`. Wartość w [funkcji członkowskiej OnIdle](../mfc/onidle-member-function.md) zawiera sekwencję akcji w pętli komunikatów.  
  
 Podczas wysyłania wiadomości zależy od rodzaju wiadomości. Aby uzyskać więcej informacji, zobacz [komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md).  
  
## <a name="see-also"></a>Zobacz też  
 [CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md)
