---
title: Ostrzeżenie kompilatora (poziom 1) C4258
ms.date: 11/04/2016
f1_keywords:
- C4258
helpviewer_keywords:
- C4258
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
ms.openlocfilehash: a192fb9d8dc046bb3493b90b85371175520ccf95
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230730"
---
# <a name="compiler-warning-level-1-c4258"></a>Ostrzeżenie kompilatora (poziom 1) C4258

"zmienna": definicja z pętli for jest ignorowana; używana jest definicja z otaczającego zakresu "

W obszarze [/ze](../../build/reference/za-ze-disable-language-extensions.md) i [/Zc: forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)zmienne zdefiniowane w pętli [for](../../cpp/for-statement-cpp.md) wykraczają poza zakres po **`for`** zakończeniu pętli. To ostrzeżenie występuje, jeśli zmienna o takiej samej nazwie jak zmienna pętli, ale zdefiniowana w otaczającej pętli, jest używana ponownie w zakresie zawierającym **`for`** pętlę. Na przykład:

```cpp
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
