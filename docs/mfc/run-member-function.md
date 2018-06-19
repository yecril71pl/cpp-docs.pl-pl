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
ms.openlocfilehash: be1d7d90b4c13a23e2e3456e7371abbae61be4e9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379899"
---
# <a name="run-member-function"></a>Uruchamianie funkcji członkowskiej
Aplikacja framework zużywa większość czasu w [Uruchom](../mfc/reference/cwinapp-class.md#run) funkcji członkowskiej klasy [CWinApp](../mfc/reference/cwinapp-class.md). Po zainicjowaniu `WinMain` wywołania **Uruchom** do przetworzenia w pętli komunikatów.  
  
 **Uruchom** przełączanie po kolei pętli komunikatów, sprawdzanie kolejki komunikatów dla komunikatów dostępne. Jeśli komunikat jest dostępna, **Uruchom** wywołuje dla akcji. Jeśli nie ma wiadomości, która jest często ma wartość true, **Uruchom** wywołania `OnIdle` celu żadnych przetwarzania czas bezczynności, które platformę może potrzebować gotowe. Jeśli istnieją żadnych komunikatów i przetwarzanie w stanie bezczynności, aby zrobić, aplikacja oczekuje, aż wydarzy się coś. Po zakończeniu działania aplikacji **Uruchom** wywołania `ExitInstance`. Wartość w [funkcji członkowskiej OnIdle](../mfc/onidle-member-function.md) zawiera sekwencję akcji w pętli komunikatów.  
  
 Podczas wysyłania wiadomości zależy od rodzaju wiadomości. Aby uzyskać więcej informacji, zobacz [komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md).  
  
## <a name="see-also"></a>Zobacz też  
 [CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md)
