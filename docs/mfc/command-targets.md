---
title: Obiekty docelowe poleceń
ms.date: 11/04/2016
helpviewer_keywords:
- command targets
- command mapping
- messages, command [MFC]
- command routing [MFC], command targets
ms.assetid: b0f784e5-c6dc-4391-9e71-aa7b7dcbe9f0
ms.openlocfilehash: ed3d6a68967dc7f4244f887ae34760fdb99fa7f5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388517"
---
# <a name="command-targets"></a>Obiekty docelowe poleceń

Rysunek [polecenia w strukturze](../mfc/user-interface-objects-and-command-ids.md) Pokazuje połączenia między obiekt interfejsu użytkownika, na przykład element menu, a funkcja obsługi, który struktura wywołuje do przeprowadzania wynikowy polecenia, po kliknięciu obiektu.

Windows wysyła komunikaty, które nie są komunikaty poleceń, bezpośrednio do okna, którego program obsługi wiadomości jest następnie wywoływana. Jednak struktura kieruje polecenia do liczby obiektów Release candidate — o nazwie "obiekty docelowe poleceń" — jeden z nich zwykle wywołuje program obsługi dla polecenia. Funkcje obsługi działają tak samo dla poleceń i standardowe komunikaty Windows, ale mechanizmy, według których są one nazywane różnią się, jak wyjaśniono w [jak struktura wywołuje program obsługi](../mfc/how-the-framework-calls-a-handler.md).

## <a name="see-also"></a>Zobacz także

[Komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md)
