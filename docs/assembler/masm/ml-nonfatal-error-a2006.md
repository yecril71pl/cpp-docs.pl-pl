---
title: Błąd niekrytyczny ML A2006
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2006
helpviewer_keywords:
- A2006
ms.assetid: b8a8f096-95df-42b5-85ed-d2530560a84c
ms.openlocfilehash: 6c55cb66d6eaeaf620aeedc1dd924f6618cbf817
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856786"
---
# <a name="ml-nonfatal-error-a2006"></a>Błąd niekrytyczny ML A2006

**Niezdefiniowany symbol: Identyfikator**

Podjęto próbę użycia niezdefiniowanego symbolu.

Może wystąpić jedna z następujących czynności:

- Symbol nie został zdefiniowany.

- Pole nie jest elementem członkowskim określonej struktury.

- Symbol został zdefiniowany w pliku dołączanym, który nie został uwzględniony.

- Symbol zewnętrzny został użyty bez dyrektywy [extern](../../assembler/masm/extern-masm.md) lub [EXTERNDEF](../../assembler/masm/externdef.md) .

- Nazwa symbolu jest błędna.

- Przywoływano lokalna etykieta kodu poza jej zakresem.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>