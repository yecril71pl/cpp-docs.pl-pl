---
title: Błąd niekrytyczny ML A2219 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2219
dev_langs:
- C++
helpviewer_keywords:
- A2219
ms.assetid: 5ebc2f40-e47e-4f8e-b7b9-960b9cfc9f6d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 365997181b0d4f4471162d7cf8f65a4429e69e74
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43681648"
---
# <a name="ml-nonfatal-error-a2219"></a>Błąd niekrytyczny ML A2219

**Nieprawidłowe wyrównanie przesunięcie w kodzie operacji unwind**

Argument [. ALLOCSTACK](../../assembler/masm/dot-allocstack.md) i [. SAVEREG](../../assembler/masm/dot-savereg.md) musi być wielokrotnością liczby 8.  Argument [. SAVEXMM128](../../assembler/masm/dot-savexmm128.md) i [. SETFRAME](../../assembler/masm/dot-setframe.md) musi być wielokrotnością liczby 16.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>