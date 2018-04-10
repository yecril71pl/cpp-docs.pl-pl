---
title: Obiekty docelowe poleceń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- command targets
- command mapping
- messages, command [MFC]
- command routing [MFC], command targets
ms.assetid: b0f784e5-c6dc-4391-9e71-aa7b7dcbe9f0
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bb8d2bff69e95a089827c85ade6dc4bcd67eb7ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="command-targets"></a>Obiekty docelowe poleceń
Rysunek [polecenia w strukturze](../mfc/user-interface-objects-and-command-ids.md) pokazuje połączenie między obiektu interfejsu użytkownika, takie jak element menu i funkcji programu obsługi, która struktura wywołuje do wykonania tego polecenia wynikowy, gdy obiekt zostanie kliknięty.  
  
 System Windows wysyła komunikaty, które nie są komunikaty poleceń, bezpośrednio do okna, którego program obsługi wiadomości jest następnie wywoływana. Jednak platformę kieruje poleceń do liczby obiektów candidate — o nazwie "obiekty docelowe poleceń" — z których jedna zwykle wywołuje program obsługi dla polecenia. Funkcje obsługi działają tak samo dla poleceń i standardowe komunikaty systemu Windows, ale mechanizmy, które są nazywane są różne, zgodnie z objaśnieniem w [jak struktura wywołuje program obsługi](../mfc/how-the-framework-calls-a-handler.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md)

