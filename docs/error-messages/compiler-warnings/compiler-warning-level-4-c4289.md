---
title: Kompilator ostrzeżenie (poziom 4) C4289 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4289
dev_langs:
- C++
helpviewer_keywords:
- C4289
ms.assetid: 0dbd2863-4cde-4e16-894b-104a2d5fa724
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 35cb22c767c0ea64a1536bd4d02ad8653bb94250
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102843"
---
# <a name="compiler-warning-level-4-c4289"></a>Kompilator ostrzeżenie (poziom 4) C4289

użyte rozszerzenie niestandardowe: 'var' : zmienna sterowania pętlą zadeklarowana w pętli for jest używana poza zakresem pętli for

Podczas kompilowania za pomocą [/Ze](../../build/reference/za-ze-disable-language-extensions.md) i **/Zc:forScope-**, Zmienna zadeklarowana w [dla](../../cpp/for-statement-cpp.md) pętli został użyty po **dla**-zakresu pętli.

Zobacz [/Zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) informacji o sposobie określania standardowe zachowanie w **dla** pętli z **/Ze**.

To ostrzeżenie jest domyślnie wyłączona. Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.

Poniższy przykład spowoduje wygenerowanie C4289:

```
// C4289.cpp
// compile with: /W4 /Zc:forScope-
#pragma warning(default:4289)
int main() {
   for (int i = 0 ; ; )   // C4289
      break;
   i++;
}
```