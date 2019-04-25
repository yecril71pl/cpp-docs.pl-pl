---
title: Optymalizacja wbudowanego asemblera
ms.date: 08/30/2018
helpviewer_keywords:
- storage, optimizing in inline assembly
- optimization, inline assembly
- inline assembly, optimizing
- optimizing performance, inline assembly
- __asm keyword [C++], optimizing
ms.assetid: 52a7ec83-9782-4d96-94c1-53bb2ac9e8c8
ms.openlocfilehash: d4956ba12e0bc268d78a895e6cb1ec6e2059262a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166883"
---
# <a name="optimizing-inline-assembly"></a>Optymalizacja wbudowanego asemblera

**Microsoft Specific**

Obecność `__asm` bloku w funkcji ma wpływ optymalizacji na kilka sposobów. Po pierwsze, kompilator nie próbuje zoptymalizować `__asm` block sam. Pisanie w języku zestawu jest dokładnie, co można uzyskać. Drugi, obecności `__asm` wpływa na blok zarejestrować zmiennej magazynu. Kompilator eliminuje rejestrowanie zmienne z różnych `__asm` zablokować, jeśli zawartość rejestru zostaną zmienione przez `__asm` bloku. Na koniec włączenia języka zestawu w funkcji wpływ inne optymalizacje całej funkcji.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Wbudowany asembler](../../assembler/inline/inline-assembler.md)<br/>