---
title: Kompilatora (poziom 1) ostrzeżenie C4288 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4288
dev_langs:
- C++
helpviewer_keywords:
- C4288
ms.assetid: 6aaeb139-90cd-457a-9d37-65687042736f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b8b9e82f8cb24c4635fb64c3ac0a1c82e301c086
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056494"
---
# <a name="compiler-warning-level-1-c4288"></a>Kompilatora (poziom 1) ostrzeżenie C4288

użyto niestandardowego rozszerzenia: "var": zmienna sterująca pętli zadeklarowana w pętli for jest używana poza zakresem pętli for; powoduje on konflikt z deklaracją w zewnętrznym zakresie

Podczas kompilowania za pomocą [/Ze](../../build/reference/za-ze-disable-language-extensions.md) i **/Zc:forscope-**, Zmienna zadeklarowana w **dla** pętli został użyty po [dla](../../cpp/for-statement-cpp.md)-zakresu pętli. Rozszerzenie Microsoft do języka C++ umożliwia ta zmienna ma pozostawać w zakresie, a C4288 przypomina o tym, że pierwszej deklaracji zmiennej nie jest używany.

Zobacz [/Zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) informacji o sposobie określania rozszerzeń firmy Microsoft w **dla** pętli for z /Ze.

Poniższy przykład spowoduje wygenerowanie C4288:

```
// C4288.cpp
// compile with: /W1 /c /Zc:forScope-
int main() {
   int i = 0;    // not used in this program
   for (int i = 0 ; ; ) ;
   i++;   // C4288 using for-loop declaration of i
}
```