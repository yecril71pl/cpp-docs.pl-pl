---
title: Błąd krytyczny ML A1010
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A1010
helpviewer_keywords:
- A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
ms.openlocfilehash: eb4d77b856e93a8d64ee6c51bec63ceae59b22e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62202068"
---
# <a name="ml-fatal-error-a1010"></a>Błąd krytyczny ML A1010

**Zagnieżdżanie niedopasowane bloku:**

Początek bloku nie ma pasującego zakończenia lub koniec bloku nie ma pasującego początku. Może być zaangażowany jedną z następujących czynności:

- Dyrektywy wysokiego poziomu, takie jak [. Jeśli](../../assembler/masm/dot-if.md), [. Powtórz](../../assembler/masm/dot-repeat.md), lub [. GDY](../../assembler/masm/dot-while.md).

- Dyrektywa zestawu warunkowego, takich jak [IF](../../assembler/masm/if-masm.md), [Powtórz](../../assembler/masm/repeat.md), lub **podczas**.

- Definicja struktury lub Unii.

- Definicja procedury.

- Definicja segmentu.

- A [popcontext —](../../assembler/masm/popcontext.md) dyrektywy.

- Zestaw warunkowe dyrektywy, takie jak [ELSE](../../assembler/masm/else-masm.md), [ELSEIF](../../assembler/masm/elseif-masm.md), lub **ENDIF** bez odpowiadającego mu [IF](../../assembler/masm/if-masm.md).

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>