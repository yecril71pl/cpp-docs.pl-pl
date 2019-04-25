---
title: Błąd krytyczny ML A1011
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A1011
helpviewer_keywords:
- A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
ms.openlocfilehash: 591755a1d7066d8251f61d2a22b9601a9ccb9dcb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62178569"
---
# <a name="ml-fatal-error-a1011"></a>Błąd krytyczny ML A1011

**dyrektywa musi znajdować się w bloku sterowania**

Asembler znaleziono dyrektywy wysokiego poziomu, której nie oczekiwano jednej. Znaleziono jednej z następujących dyrektywach:

- [. ELSE](../../assembler/masm/dot-else.md) bez [. JEŚLI](../../assembler/masm/dot-if.md)

- [. ENDIF](../../assembler/masm/dot-endif.md) bez [. JEŚLI](../../assembler/masm/dot-if.md)

- [. ENDW](../../assembler/masm/dot-endw.md) bez [. WHILE](../../assembler/masm/dot-while.md)

- [. UNTILCXZ](../../assembler/masm/dot-untilcxz.md) bez [. POWTÓRZ](../../assembler/masm/dot-repeat.md)

- [. Kontynuuj](../../assembler/masm/dot-continue.md) bez [. GDY](../../assembler/masm/dot-while.md) lub [. POWTÓRZ](../../assembler/masm/dot-repeat.md)

- [. PRZERWIJ](../../assembler/masm/dot-break.md) bez [. GDY](../../assembler/masm/dot-while.md) lub [. POWTÓRZ](../../assembler/masm/dot-repeat.md)

- [. ELSE](../../assembler/masm/dot-else.md) następujące `.ELSE`

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>