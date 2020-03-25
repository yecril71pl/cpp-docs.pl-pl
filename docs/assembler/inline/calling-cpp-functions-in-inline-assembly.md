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
ms.openlocfilehash: f16e466ebb5f31231411eaaf9a1a85bfcc46a34d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169581"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Wywoływanie funkcji C++ w asemblerze wbudowanym

**Specyficzne dla firmy Microsoft**

Blok `__asm` może wywoływać tylko funkcje C++ globalne, które nie są przeciążone. Jeśli wywołasz przeciążoną funkcję C++ globalną lub C++ funkcję członkowską, kompilator wygeneruje błąd.

Możesz również wywołać wszystkie funkcje zadeklarowane za pomocą zewnętrznego powiązania **"C"** . Umożliwia to blokowi `__asm` w ramach C++ programu wywoływanie funkcji biblioteki języka C, ponieważ wszystkie standardowe pliki nagłówkowe deklarują funkcje biblioteki jako zewnętrzne powiązania **"C"** .

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Wbudowany asembler](../../assembler/inline/inline-assembler.md)<br/>
