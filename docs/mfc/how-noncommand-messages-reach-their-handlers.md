---
title: Jak komunikaty niebędące poleceniami docierają do swoich programów obsługi
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
ms.openlocfilehash: 4b9fb0a72b330380f0207db9968199a7e4c3d9b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407942"
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>Jak komunikaty niebędące poleceniami docierają do swoich programów obsługi

W przeciwieństwie do poleceń standardowe komunikaty Windows nie uzyskać kierowane za pośrednictwem cele podporządkowania, ale są zazwyczaj obsługiwane przez okno, do którego Windows wysyła wiadomość. Okno może być ramką głównego okna, okno podrzędne MDI, kontrolki standardowej, okno dialogowe, widoku lub innego rodzaju okna podrzędnego.

W czasie wykonywania, każde okno Windows jest dołączony do obiektu okna (pochodzi bezpośrednio lub pośrednio z `CWnd`) ma własne skojarzone mapy oraz obsługi funkcji obsługi wiadomości. Środowisko wykorzystuje mapy komunikatów — jak w przypadku polecenia — do mapowania obsługi wiadomości przychodzących.

## <a name="see-also"></a>Zobacz także

[Jak struktura wywołuje programy obsługi](../mfc/how-the-framework-calls-a-handler.md)
