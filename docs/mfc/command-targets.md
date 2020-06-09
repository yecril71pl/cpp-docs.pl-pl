---
title: Obiekty docelowe poleceń
ms.date: 11/04/2016
helpviewer_keywords:
- command targets
- command mapping
- messages, command [MFC]
- command routing [MFC], command targets
ms.assetid: b0f784e5-c6dc-4391-9e71-aa7b7dcbe9f0
ms.openlocfilehash: 59ba197174e95e42cd237c875f39f07801cb3dbe
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619311"
---
# <a name="command-targets"></a>Obiekty docelowe poleceń

Polecenia rysunek [w strukturze](user-interface-objects-and-command-ids.md) przedstawiają połączenie między obiektem interfejsu użytkownika, takim jak element menu, a funkcją obsługi, którą struktura wywołuje w celu przeprowadzenia wyniku polecenia po kliknięciu obiektu.

System Windows wysyła komunikaty, które nie są komunikatami poleceń bezpośrednio do okna, którego program obsługi wiadomości jest wywoływany. Jednak struktura kieruje polecenia do kilku obiektów kandydujących — nazywanych "obiektami docelowymi poleceń" — jednym z, które zwykle wywołuje procedurę obsługi dla polecenia. Funkcje obsługi działają w taki sam sposób dla obu poleceń i standardowych komunikatów systemu Windows, ale mechanizmy, za pomocą których są wywoływane, są inne, zgodnie z opisem w temacie [jak struktura wywołuje procedurę obsługi](how-the-framework-calls-a-handler.md).

## <a name="see-also"></a>Zobacz też

[Komunikaty i polecenia w strukturze](messages-and-commands-in-the-framework.md)
