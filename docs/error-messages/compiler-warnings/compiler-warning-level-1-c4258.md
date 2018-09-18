---
title: Kompilator ostrzeżenie (poziom 1) C4258 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4258
dev_langs:
- C++
helpviewer_keywords:
- C4258
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4d9aacd6e3681a1eb42073df8a13d7ce72c5634
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46083538"
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