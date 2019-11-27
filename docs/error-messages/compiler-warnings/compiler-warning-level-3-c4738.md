---
title: Ostrzeżenie kompilatora (poziom 3) C4738
ms.date: 11/04/2016
f1_keywords:
- C4738
helpviewer_keywords:
- C4738
ms.assetid: 9094895f-7eec-46c2-83d3-249b761d585e
ms.openlocfilehash: 5162a03b213b35913ed1fc7f39360796ccf2c4a0
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2019
ms.locfileid: "74189393"
---
# <a name="compiler-warning-level-3-c4738"></a>Ostrzeżenie kompilatora (poziom 3) C4738

przechowywanie 32-bitowego wyniku zmiennopozycyjnego w pamięci, możliwa utrata wydajności

C4738 ostrzega, że wynik przypisywania, rzutowania, pomyślnego argumentu lub innej operacji może być zaokrąglony lub że operacja została wykonana z rejestrów i jest wymagana do użycia pamięci (rozłożenie). Może to spowodować utratę wydajności.

Aby rozwiązać to ostrzeżenie i uniknąć zaokrąglania, Kompiluj z [/FP: Fast](../../build/reference/fp-specify-floating-point-behavior.md) lub użyj `double` zamiast `float`.

Aby rozwiązać to ostrzeżenie i uniknąć braku rejestrów, Zmień kolejność obliczeń i zmodyfikuj użycie funkcji tworzenia konspektu

To ostrzeżenie jest domyślnie wyłączone. Aby uzyskać więcej informacji, zobacz [ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C4738:

```cpp
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