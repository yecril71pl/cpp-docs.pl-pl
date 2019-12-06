---
title: Błąd krytyczny ML A1010
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A1010
helpviewer_keywords:
- A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
ms.openlocfilehash: 6ec82f7f6d559d977a9aa039ed91689a0ef4d49a
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856881"
---
# <a name="ml-fatal-error-a1010"></a>Błąd krytyczny ML A1010

**niedopasowane zagnieżdżenie bloków:**

Początek bloku nie ma pasującego końca lub zakończenie bloku nie ma pasującego początku. Może być uwzględniona jedna z następujących elementów:

- Dyrektywa wysokiego poziomu, taka jak [. Jeśli](../../assembler/masm/dot-if.md), [. Powtórz](../../assembler/masm/dot-repeat.md)lub [. WHILE](../../assembler/masm/dot-while.md).

- Dyrektywa zestawu warunkowego, taka jak [if](../../assembler/masm/if-masm.md), [REPEAT](../../assembler/masm/repeat.md)lub **while**.

- Struktura lub definicja związku.

- Definicja procedury.

- Definicja segmentu.

- Dyrektywa [POPCONTEXT](../../assembler/masm/popcontext.md) .

- Dyrektywa zestawu warunkowego, taka jak [else](../../assembler/masm/else-masm.md), [ElseIf](../../assembler/masm/elseif-masm.md)lub **endif** bez dopasowania [if](../../assembler/masm/if-masm.md).

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>