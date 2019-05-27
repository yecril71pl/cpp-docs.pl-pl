---
title: Błąd niekrytyczny ML A2219
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2219
helpviewer_keywords:
- A2219
ms.assetid: 5ebc2f40-e47e-4f8e-b7b9-960b9cfc9f6d
ms.openlocfilehash: 61fa6bc6d630f1e8a8ac84492b60690c9545fb3e
ms.sourcegitcommit: 79e985d3c6e8ccaf94f6e641972887cae8c6eeb0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66197681"
---
# <a name="ml-nonfatal-error-a2219"></a>Błąd niekrytyczny ML A2219

> Nieprawidłowe wyrównanie przesunięcie w kodzie operacji unwind

## <a name="remarks"></a>Uwagi

Argument [ &period;ALLOCSTACK](../../assembler/masm/dot-allocstack.md) i [ &period;SAVEREG](../../assembler/masm/dot-savereg.md) musi być wielokrotnością liczby 8.  Argument [ &period;SAVEXMM128](../../assembler/masm/dot-savexmm128.md) i [ &period;SETFRAME](../../assembler/masm/dot-setframe.md) musi być wielokrotnością liczby 16.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)
