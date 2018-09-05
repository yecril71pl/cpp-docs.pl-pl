---
title: Błąd niekrytyczny ML A2006 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2006
dev_langs:
- C++
helpviewer_keywords:
- A2006
ms.assetid: b8a8f096-95df-42b5-85ed-d2530560a84c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f287c6ab46c6af71ba6dc0032f332ce3cc489454
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43677408"
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