---
title: Błąd niekrytyczny ML A2006
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2006
helpviewer_keywords:
- A2006
ms.assetid: b8a8f096-95df-42b5-85ed-d2530560a84c
ms.openlocfilehash: 80283bde4dff36e32d276c998f6797b6eeed8160
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490067"
---
# <a name="ml-nonfatal-error-a2006"></a>Błąd niekrytyczny ML A2006

**Niezdefiniowany symbol: identyfikator**

Próbowano użyć symbolu, który nie został zdefiniowany.

Jedną z następujących przyczyn:

- Nie zdefiniowano symbolu.

- Pole nie jest członkiem określonej struktury.

- Symbol został zdefiniowany w pliku dołączonego, który nie został dołączony.

- Zewnętrzny symbol został użyty bez [EXTERN](../../assembler/masm/extern-masm.md) lub [externdef —](../../assembler/masm/externdef.md) dyrektywy.

- Nazwa symbolu została wpisana z błędem.

- Etykieta kod lokalny odwoływano się poza zakres.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>