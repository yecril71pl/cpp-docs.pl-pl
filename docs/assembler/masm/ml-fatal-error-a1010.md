---
title: Błąd krytyczny ML A1010 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1010
dev_langs:
- C++
helpviewer_keywords:
- A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 12b7e8698951e8ef59e0433134ec992af5d5f77f
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676300"
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