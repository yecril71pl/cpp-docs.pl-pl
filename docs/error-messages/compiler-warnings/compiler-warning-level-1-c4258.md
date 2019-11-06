---
title: Ostrzeżenie kompilatora (poziom 1) C4258
ms.date: 11/04/2016
f1_keywords:
- C4258
helpviewer_keywords:
- C4258
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
ms.openlocfilehash: 75d706fafacc5c1524915d063a7fa392cea01b4c
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624878"
---
# <a name="compiler-warning-level-1-c4258"></a>Ostrzeżenie kompilatora (poziom 1) C4258

"zmienna": definicja z pętli for jest ignorowana; używana jest definicja z otaczającego zakresu "

W obszarze [/ze](../../build/reference/za-ze-disable-language-extensions.md) i [/Zc: forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)zmienne zdefiniowane w pętli [for](../../cpp/for-statement-cpp.md) wykraczają poza zakres po zakończeniu pętli **for** . To ostrzeżenie występuje, jeśli zmienna o takiej samej nazwie jak zmienna pętli, ale zdefiniowana w otaczającej pętli, jest używana ponownie w zakresie zawierającym pętlę **for** . Na przykład:

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