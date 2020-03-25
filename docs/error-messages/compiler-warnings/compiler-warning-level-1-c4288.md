---
title: Ostrzeżenie kompilatora (poziom 1) C4288
ms.date: 11/04/2016
f1_keywords:
- C4288
helpviewer_keywords:
- C4288
ms.assetid: 6aaeb139-90cd-457a-9d37-65687042736f
ms.openlocfilehash: e706a448f4264eceedbb4fa8932c0fc30e88d532
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175743"
---
# <a name="compiler-warning-level-1-c4288"></a>Ostrzeżenie kompilatora (poziom 1) C4288

użyto niestandardowego rozszerzenia: "var": Zmienna sterująca pętli zadeklarowana w pętli for jest używana poza zakresem pętli for; powoduje konflikt z deklaracją w zewnętrznym zakresie

Podczas kompilowania z [/ze](../../build/reference/za-ze-disable-language-extensions.md) i **/Zc: forScope-** , zmienna zadeklarowana w pętli **for** została użyta po zakresie pętli [for](../../cpp/for-statement-cpp.md). Rozszerzenie firmy Microsoft do C++ języka pozwala, aby ta zmienna pozostawała w zakresie, a C4288 przypomina o tym, że pierwsza deklaracja zmiennej nie jest używana.

Zobacz [/Zc: forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) , aby uzyskać informacje na temat sposobu określania rozszerzenia firmy Microsoft w programie **for** pętle with/ze.

Poniższy przykład generuje C4288:

```cpp
// C4288.cpp
// compile with: /W1 /c /Zc:forScope-
int main() {
   int i = 0;    // not used in this program
   for (int i = 0 ; ; ) ;
   i++;   // C4288 using for-loop declaration of i
}
```
