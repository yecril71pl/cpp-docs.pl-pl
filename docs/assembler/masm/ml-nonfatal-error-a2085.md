---
title: Błąd niekrytyczny ML A2085
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2085
helpviewer_keywords:
- A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
ms.openlocfilehash: 3bd89fb2b7f8b755cdb095e63ed89386332ecf9d
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74855761"
---
# <a name="ml-nonfatal-error-a2085"></a>Błąd niekrytyczny ML A2085

**instrukcja lub rejestr nie został zaakceptowany w bieżącym trybie procesora**

Podjęto próbę użycia instrukcji, rejestru lub słowa kluczowego, które były nieprawidłowe dla bieżącego trybu procesora.

Na przykład rejestry 32-bitowe wymagają [. 386](../../assembler/masm/dot-386.md) lub nowszego. Rejestry kontroli, takie jak CR0, wymagają trybu uprzywilejowanego [. 386P](../../assembler/masm/dot-386p.md) lub wyższe. Ten błąd zostanie również wygenerowany dla **NEAR32**, **FAR32**i **zwykłych** słów kluczowych, które wymagają. **386** lub nowszy.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>