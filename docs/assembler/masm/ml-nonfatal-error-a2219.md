---
title: Błąd niekrytyczny ML A2219
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2219
helpviewer_keywords:
- A2219
ms.assetid: 5ebc2f40-e47e-4f8e-b7b9-960b9cfc9f6d
ms.openlocfilehash: 611be49a1d4018eeb4edd9ee750d5a0614a83abe
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75311952"
---
# <a name="ml-nonfatal-error-a2219"></a>Błąd niekrytyczny ML A2219

> Złe wyrównanie do przesunięcia w kodzie operacji unwind

## <a name="remarks"></a>Uwagi

Operand dla [&period;ALLOCSTACK](dot-allocstack.md) i [&period;SAVEREG](dot-savereg.md) musi być wielokrotnością liczby 8.  Operand dla [&period;SAVEXMM128](dot-savexmm128.md) i [&period;SETFRAME](dot-setframe.md) musi być wielokrotnością 16.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](ml-error-messages.md)
