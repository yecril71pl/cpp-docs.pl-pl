---
title: Kompilator ostrzeżenie (poziom 1) C4258
ms.date: 11/04/2016
f1_keywords:
- C4258
helpviewer_keywords:
- C4258
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
ms.openlocfilehash: a3ce4c81a86920baddfc1b277df0236a96254be4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478278"
---
# <a name="compiler-warning-level-1-c4258"></a>Kompilator ostrzeżenie (poziom 1) C4258

'Zmienna': definicja z pętli for jest zignorowana; Służy definicji z otaczającego zakresu"

W obszarze [/Ze](../../build/reference/za-ze-disable-language-extensions.md) i [/Zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md), zmienne zdefiniowane w [dla](../../cpp/for-statement-cpp.md) pętli wykraczają poza zakres po **dla** zakończeniu pętli. To ostrzeżenie występuje, jeśli zmienna o takiej samej nazwie jako zmiennej pętli, ale zdefiniowanych w otaczającej pętli jest używany ponownie w zawierającym zakresie **dla** pętli. Na przykład:

```
// C4258.cpp
// compile with: /Zc:forScope /W1
int main()
{
   int i;
   {
      for (int i =0; i < 1; i++)
         ;
      i = 20;   // C4258 i (in for loop) has gone out of scope
   }
}
```