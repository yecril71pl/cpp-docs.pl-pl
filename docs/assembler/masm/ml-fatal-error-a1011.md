---
title: Błąd krytyczny ML A1011
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A1011
helpviewer_keywords:
- A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
ms.openlocfilehash: 0d8d3896f7788aa3f51605651ee1b728b0e1d60a
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856855"
---
# <a name="ml-fatal-error-a1011"></a>Błąd krytyczny ML A1011

**dyrektywa musi być w bloku sterowania**

Asembler znalazł dyrektywę wysokiego poziomu, której nie oczekiwano. Znaleziono jedną z następujących dyrektyw:

- [. INACZEJ](../../assembler/masm/dot-else.md) bez [. Jeśli](../../assembler/masm/dot-if.md)

- [. ENDIF](../../assembler/masm/dot-endif.md) bez [. Jeśli](../../assembler/masm/dot-if.md)

- [. ENDW](../../assembler/masm/dot-endw.md) bez [. WHILE](../../assembler/masm/dot-while.md)

- [. UNTILCXZ](../../assembler/masm/dot-untilcxz.md) bez [. Powtórz](../../assembler/masm/dot-repeat.md)

- [. Kontynuuj](../../assembler/masm/dot-continue.md) bez [. WHILE](../../assembler/masm/dot-while.md) lub [. Powtórz](../../assembler/masm/dot-repeat.md)

- [. Przerwij](../../assembler/masm/dot-break.md) bez [. WHILE](../../assembler/masm/dot-while.md) lub [. Powtórz](../../assembler/masm/dot-repeat.md)

- [. ELSE](../../assembler/masm/dot-else.md) `.ELSE`

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>