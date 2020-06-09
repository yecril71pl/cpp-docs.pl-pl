---
title: Jak komunikaty niebędące poleceniami docierają do swoich programów obsługi
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
ms.openlocfilehash: c7b2bf819c5305da4039fae172578298d3b4e609
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618507"
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>Jak komunikaty niebędące poleceniami docierają do swoich programów obsługi

W przeciwieństwie do poleceń standardowe komunikaty systemu Windows nie są kierowane przez łańcuch obiektów docelowych poleceń, ale są zwykle obsługiwane przez okno, do którego system Windows wysyła komunikat. Okno może być głównym oknem ramki, oknem podrzędnym MDI, formantem standardowym, oknem dialogowym, widokiem lub innym rodzajem okna podrzędnego.

W czasie wykonywania każde okno systemu Windows jest dołączone do obiektu okna (pochodnego bezpośrednio lub pośrednio z `CWnd` ), który ma własną skojarzoną mapę komunikatów i funkcje obsługi. Struktura używa mapy komunikatów — podobnie jak w przypadku polecenia — do mapowania komunikatów przychodzących do programów obsługi.

## <a name="see-also"></a>Zobacz też

[Jak struktura wywołuje program obsługi](how-the-framework-calls-a-handler.md)
