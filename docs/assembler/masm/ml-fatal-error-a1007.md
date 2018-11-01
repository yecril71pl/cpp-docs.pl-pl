---
title: Błąd krytyczny ML A1007
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A1007
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
ms.openlocfilehash: 98933c3a24da22f447174a3b51c4855690aba83e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603401"
---
# <a name="ml-fatal-error-a1007"></a>Błąd krytyczny ML A1007

**poziom zagnieżdżenia, które są zbyt głęboko**

Asembler osiągnęła limit zagnieżdżania. Limit wynosi 20 poziomy, chyba że zaznaczono inaczej.

Jedną z następujących był zbyt głęboko zagnieżdżone:

- Dyrektywy wysokiego poziomu, takie jak [. Jeśli](../../assembler/masm/dot-if.md), [. Powtórz](../../assembler/masm/dot-repeat.md), lub [. GDY](../../assembler/masm/dot-while.md).

- Definicja struktury.

- Dyrektywa zestawu warunkowe.

- Definicja procedury.

- A [pushcontext —](../../assembler/masm/pushcontext.md) — dyrektywa (limit wynosi 10).

- Definicja segmentu.

- Plik dołączania.

- Makra.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>