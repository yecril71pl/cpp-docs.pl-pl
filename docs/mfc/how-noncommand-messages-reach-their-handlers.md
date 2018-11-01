---
title: Jak komunikaty niebędące poleceniami docierają do swoich programów obsługi
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
ms.openlocfilehash: f64eb97315b41a314c791e1a4c5bc7721b329fca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545460"
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>Jak komunikaty niebędące poleceniami docierają do swoich programów obsługi

W przeciwieństwie do poleceń standardowe komunikaty Windows nie uzyskać kierowane za pośrednictwem cele podporządkowania, ale są zazwyczaj obsługiwane przez okno, do którego Windows wysyła wiadomość. Okno może być ramką głównego okna, okno podrzędne MDI, kontrolki standardowej, okno dialogowe, widoku lub innego rodzaju okna podrzędnego.

W czasie wykonywania, każde okno Windows jest dołączony do obiektu okna (pochodzi bezpośrednio lub pośrednio z `CWnd`) ma własne skojarzone mapy oraz obsługi funkcji obsługi wiadomości. Środowisko wykorzystuje mapy komunikatów — jak w przypadku polecenia — do mapowania obsługi wiadomości przychodzących.

## <a name="see-also"></a>Zobacz też

[Jak struktura wywołuje programy obsługi](../mfc/how-the-framework-calls-a-handler.md)

