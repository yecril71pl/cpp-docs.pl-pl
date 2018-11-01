---
title: Wywoływanie funkcji C++ w asemblerze wbudowanym
ms.date: 08/30/2018
helpviewer_keywords:
- functions [C++], calling in inline assembly
- function calls, C++ functions
- function calls, in inline assembly
- Visual C++, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: 1f0d1eb3-54cf-45d5-838d-958188616b38
ms.openlocfilehash: 666f7b2a59f0d48a14be54a439b6402f2a4d3128
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458231"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Wywoływanie funkcji C++ w asemblerze wbudowanym

**Microsoft Specific**

`__asm` Bloku można wywołać tylko globalne funkcje C++, które nie są przeciążone. Jeśli chcesz wywołać przeciążona funkcja globalna C++ lub funkcji składowej C++, kompilator generuje błąd.

Można również wywołać wszystkie funkcje zadeklarowane za pomocą **extern "C"** powiązania. Dzięki temu `__asm` bloku w programie C++ do wywołania funkcji biblioteki C, ponieważ wszystkie pliki nagłówkowe standard zadeklarować funkcji biblioteki, które mają mieć **extern "C"** powiązania.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Wbudowany asembler](../../assembler/inline/inline-assembler.md)<br/>