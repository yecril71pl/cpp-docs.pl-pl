---
title: Wywoływanie funkcji C++ w asemblerze wbudowanym | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], calling in inline assembly
- function calls, C++ functions
- function calls, in inline assembly
- Visual C++, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: 1f0d1eb3-54cf-45d5-838d-958188616b38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4717ae24dc1a0b6f51f7a00f68f6569c2f988c65
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678947"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Wywoływanie funkcji C++ w asemblerze wbudowanym

**Microsoft Specific**

`__asm` Bloku można wywołać tylko globalne funkcje C++, które nie są przeciążone. Jeśli chcesz wywołać przeciążona funkcja globalna C++ lub funkcji składowej C++, kompilator generuje błąd.

Można również wywołać wszystkie funkcje zadeklarowane za pomocą **extern "C"** powiązania. Dzięki temu `__asm` bloku w programie C++ do wywołania funkcji biblioteki C, ponieważ wszystkie pliki nagłówkowe standard zadeklarować funkcji biblioteki, które mają mieć **extern "C"** powiązania.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Wbudowany asembler](../../assembler/inline/inline-assembler.md)<br/>