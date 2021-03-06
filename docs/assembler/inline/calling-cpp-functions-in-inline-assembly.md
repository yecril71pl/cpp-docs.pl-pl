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
ms.openlocfilehash: 781b60c8973593039c0fdfa2f457170e95048597
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87192538"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Wywoływanie funkcji C++ w asemblerze wbudowanym

**Specyficzne dla firmy Microsoft**

**`__asm`** Blok może wywoływać tylko globalne funkcje C++, które nie są przeciążone. Jeśli wywołasz przeciążoną globalną funkcję C++ lub funkcję członkowską języka C++, kompilator wygeneruje błąd.

Możesz również wywołać wszystkie funkcje zadeklarowane za pomocą zewnętrznego powiązania **"C"** . Dzięki temu **`__asm`** blok w ramach programu C++ może wywoływać funkcje biblioteki języka C, ponieważ wszystkie standardowe pliki nagłówkowe deklarują funkcje biblioteki jako zewnętrzne powiązania **"C"** .

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Asembler wbudowany](../../assembler/inline/inline-assembler.md)<br/>
