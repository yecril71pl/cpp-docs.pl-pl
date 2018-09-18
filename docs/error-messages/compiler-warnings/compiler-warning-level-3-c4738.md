---
title: Kompilator ostrzeżenie (poziom 3) C4738 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4738
dev_langs:
- C++
helpviewer_keywords:
- C4738
ms.assetid: 9094895f-7eec-46c2-83d3-249b761d585e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8e017ef94dd28de8d4c66ab89b1509f755beeb07
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053223"
---
# <a name="compiler-warning-level-3-c4738"></a>Kompilator ostrzeżenie (poziom 3) C4738

przechowywanie 32-bitowego wyniku zmiennopozycyjnego w pamięci, możliwa utrata wydajności

C4738 ostrzega, że wynik przypisania, cast przekazany argument lub inna operacja może być konieczne ma zostać zaokrąglona lub za mało rejestruje działanie, a potrzebnych do korzystania z pamięci (rozlanie). Może to spowodować utratę wydajności.

Aby rozwiązać tego ostrzeżenia i uniknąć zaokrąglania, należy skompilować z [Fast](../../build/reference/fp-specify-floating-point-behavior.md) lub użyj `double` zamiast `float`.

Aby rozwiązać tego ostrzeżenia i uniknąć korzystającym z rejestrów, zmienić kolejność obliczeń i zmodyfikuj użytkowania wbudowanie

To ostrzeżenie jest domyślnie wyłączona. Aby uzyskać więcej informacji, zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4738:

```
// C4738.cpp
// compile with: /c /fp:precise /O2 /W3
// processor: x86
#include <stdio.h>

#pragma warning(default : 4738)

float func(float f)
{
    return f;
}

int main()
{
    extern float f, f1, f2;
    double d = 0.0;

    f1 = func(d);
    f2 = (float) d;
    f = f1 + f2;   // C4738
    printf_s("%f\n", f);
}
```