---
title: Błąd krytyczny ML A1007
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A1007
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
ms.openlocfilehash: 01633b4fa084b7d5e14af5a5c6e51e3dca684d2a
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856920"
---
# <a name="ml-fatal-error-a1007"></a>Błąd krytyczny ML A1007

**zbyt głęboki poziom zagnieżdżenia**

Asembler osiągnął limit zagnieżdżenia. Limit wynosi 20 poziomów, chyba że zaznaczono inaczej.

Jeden z następujących elementów został zagnieżdżony zbyt głęboko:

- Dyrektywa wysokiego poziomu, taka jak [. Jeśli](../../assembler/masm/dot-if.md), [. Powtórz](../../assembler/masm/dot-repeat.md)lub [. WHILE](../../assembler/masm/dot-while.md).

- Definicja struktury.

- Dyrektywa zestawu warunkowego.

- Definicja procedury.

- Dyrektywa [PUSHCONTEXT](../../assembler/masm/pushcontext.md) (limit wynosi 10).

- Definicja segmentu.

- Plik dołączany.

- Makro.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>