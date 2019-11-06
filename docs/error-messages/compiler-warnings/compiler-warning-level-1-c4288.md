---
title: Ostrzeżenie kompilatora (poziom 1) C4288
ms.date: 11/04/2016
f1_keywords:
- C4288
helpviewer_keywords:
- C4288
ms.assetid: 6aaeb139-90cd-457a-9d37-65687042736f
ms.openlocfilehash: 81094bf019060b56337347f7d364ead7c78c8128
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626656"
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