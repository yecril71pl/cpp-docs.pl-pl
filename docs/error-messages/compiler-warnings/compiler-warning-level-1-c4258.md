---
title: Ostrzeżenie kompilatora (poziom 1) C4258
ms.date: 11/04/2016
f1_keywords:
- C4258
helpviewer_keywords:
- C4258
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
ms.openlocfilehash: 198873792743a9ccdee94d44e2a0599348589ee6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163209"
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
