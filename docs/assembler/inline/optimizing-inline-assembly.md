---
title: Optymalizacja wbudowanego asemblera | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- storage, optimizing in inline assembly
- optimization, inline assembly
- inline assembly, optimizing
- optimizing performance, inline assembly
- __asm keyword [C++], optimizing
ms.assetid: 52a7ec83-9782-4d96-94c1-53bb2ac9e8c8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 49660bdc6d2eb84e6e1bbaeb5ebf0d57e484e9e1
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43687879"
---
# <a name="optimizing-inline-assembly"></a>Optymalizacja wbudowanego asemblera

**Microsoft Specific**

Obecność `__asm` bloku w funkcji ma wpływ optymalizacji na kilka sposobów. Po pierwsze, kompilator nie próbuje zoptymalizować `__asm` block sam. Pisanie w języku zestawu jest dokładnie, co można uzyskać. Drugi, obecności `__asm` wpływa na blok zarejestrować zmiennej magazynu. Kompilator eliminuje rejestrowanie zmienne z różnych `__asm` zablokować, jeśli zawartość rejestru zostaną zmienione przez `__asm` bloku. Na koniec włączenia języka zestawu w funkcji wpływ inne optymalizacje całej funkcji.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Wbudowany asembler](../../assembler/inline/inline-assembler.md)<br/>