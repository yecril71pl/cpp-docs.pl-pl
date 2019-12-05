---
title: Błąd niekrytyczny ML A2133
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2133
helpviewer_keywords:
- A2133
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
ms.openlocfilehash: c2d13aefe02543129340bcc307771a1026776d61
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74854618"
---
# <a name="ml-nonfatal-error-a2133"></a>Błąd niekrytyczny ML A2133

**wartość rejestru zastąpiona przez wywołanie**

Rejestr został przekazany jako argument do procedury, ale kod wygenerowany przez metodę [Invoke](../../assembler/masm/invoke.md) , aby przekazać inne argumenty zniszczone zawartość rejestru.

Rejestry AX, AL, AH, EAX, DX, DL, DH i EDX mogą być używane przez asembler do wykonywania konwersji danych.

Użyj innego rejestru.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>