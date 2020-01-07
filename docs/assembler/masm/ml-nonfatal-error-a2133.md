---
title: Błąd niekrytyczny ML A2133
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2133
helpviewer_keywords:
- A2133
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
ms.openlocfilehash: 1ffdf5fb6577dbd4e24312b3c57a4186173ddcf6
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75312641"
---
# <a name="ml-nonfatal-error-a2133"></a>Błąd niekrytyczny ML A2133

**wartość rejestru zastąpiona przez wywołanie**

Rejestr został przekazany jako argument do procedury, ale kod wygenerowany przez metodę [Invoke](invoke.md) , aby przekazać inne argumenty zniszczone zawartość rejestru.

Rejestry AX, AL, AH, EAX, DX, DL, DH i EDX mogą być używane przez asembler do wykonywania konwersji danych.

Użyj innego rejestru.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](ml-error-messages.md)
