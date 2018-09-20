---
title: Jak komunikaty niebędące poleceniami docierają do swoich programów obsługi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b5c38a1d4294993170cfeff64be6a83700fa7497
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373441"
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>Jak komunikaty niebędące poleceniami docierają do swoich programów obsługi

W przeciwieństwie do poleceń standardowe komunikaty Windows nie uzyskać kierowane za pośrednictwem cele podporządkowania, ale są zazwyczaj obsługiwane przez okno, do którego Windows wysyła wiadomość. Okno może być ramką głównego okna, okno podrzędne MDI, kontrolki standardowej, okno dialogowe, widoku lub innego rodzaju okna podrzędnego.

W czasie wykonywania, każde okno Windows jest dołączony do obiektu okna (pochodzi bezpośrednio lub pośrednio z `CWnd`) ma własne skojarzone mapy oraz obsługi funkcji obsługi wiadomości. Środowisko wykorzystuje mapy komunikatów — jak w przypadku polecenia — do mapowania obsługi wiadomości przychodzących.

## <a name="see-also"></a>Zobacz też

[Jak struktura wywołuje programy obsługi](../mfc/how-the-framework-calls-a-handler.md)

