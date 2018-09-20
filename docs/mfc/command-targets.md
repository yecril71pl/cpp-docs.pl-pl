---
title: Obiekty docelowe poleceń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- command targets
- command mapping
- messages, command [MFC]
- command routing [MFC], command targets
ms.assetid: b0f784e5-c6dc-4391-9e71-aa7b7dcbe9f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 408f63b80ff30a7ebdc51e5becb1dd97bb062852
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404231"
---
# <a name="command-targets"></a>Obiekty docelowe poleceń

Rysunek [polecenia w strukturze](../mfc/user-interface-objects-and-command-ids.md) Pokazuje połączenia między obiekt interfejsu użytkownika, na przykład element menu, a funkcja obsługi, który struktura wywołuje do przeprowadzania wynikowy polecenia, po kliknięciu obiektu.

Windows wysyła komunikaty, które nie są komunikaty poleceń, bezpośrednio do okna, którego program obsługi wiadomości jest następnie wywoływana. Jednak struktura kieruje polecenia do liczby obiektów Release candidate — o nazwie "obiekty docelowe poleceń" — jeden z nich zwykle wywołuje program obsługi dla polecenia. Funkcje obsługi działają tak samo dla poleceń i standardowe komunikaty Windows, ale mechanizmy, według których są one nazywane różnią się, jak wyjaśniono w [jak struktura wywołuje program obsługi](../mfc/how-the-framework-calls-a-handler.md).

## <a name="see-also"></a>Zobacz też

[Komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md)

