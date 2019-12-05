---
title: Błąd niekrytyczny ML A2219
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2219
helpviewer_keywords:
- A2219
ms.assetid: 5ebc2f40-e47e-4f8e-b7b9-960b9cfc9f6d
ms.openlocfilehash: cf2be5db2aa9c21597c199a6840f4aaa50e0a681
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74854592"
---
# <a name="ml-nonfatal-error-a2219"></a>Błąd niekrytyczny ML A2219

> Złe wyrównanie do przesunięcia w kodzie operacji unwind

## <a name="remarks"></a>Uwagi

Operand dla [&period;ALLOCSTACK](../../assembler/masm/dot-allocstack.md) i [&period;SAVEREG](../../assembler/masm/dot-savereg.md) musi być wielokrotnością liczby 8.  Operand dla [&period;SAVEXMM128](../../assembler/masm/dot-savexmm128.md) i [&period;SETFRAME](../../assembler/masm/dot-setframe.md) musi być wielokrotnością 16.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)
