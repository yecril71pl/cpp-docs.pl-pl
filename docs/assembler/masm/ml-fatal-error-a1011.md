---
title: Błąd krytyczny ML A1011
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A1011
helpviewer_keywords:
- A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
ms.openlocfilehash: 5607d6d56e0b3889332dcf2624d519529819b1c9
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318084"
---
# <a name="ml-fatal-error-a1011"></a>Błąd krytyczny ML A1011

**dyrektywa musi być w bloku sterowania**

Asembler znalazł dyrektywę wysokiego poziomu, której nie oczekiwano. Znaleziono jedną z następujących dyrektyw:

- [. INACZEJ](dot-else.md) bez [. Jeśli](dot-if.md)

- [. ENDIF](dot-endif.md) bez [. Jeśli](dot-if.md)

- [. ENDW](dot-endw.md) bez [. WHILE](dot-while.md)

- [. UNTILCXZ](dot-untilcxz.md) bez [. Powtórz](dot-repeat.md)

- [. Kontynuuj](dot-continue.md) bez [. WHILE](dot-while.md) lub [. Powtórz](dot-repeat.md)

- [. Przerwij](dot-break.md) bez [. WHILE](dot-while.md) lub [. Powtórz](dot-repeat.md)

- [. ELSE](dot-else.md) `.ELSE`

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](ml-error-messages.md)
