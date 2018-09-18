---
title: Kompilator ostrzeżenie (poziom 4) C4062 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4062
dev_langs:
- C++
helpviewer_keywords:
- C4062
ms.assetid: 36d1c6ae-c917-4b08-bf30-2eb49ee94169
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a9632c6b6259d67a8c3ad02f39dc5e61425550e4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114855"
---
# <a name="compiler-warning-level-4-c4062"></a>Kompilator ostrzeżenie (poziom 4) C4062

Moduł wyliczający 'Identyfikator' w przełączniku enum 'wyliczenie' nie jest obsługiwany.

Wyliczenia nie skojarzony program obsługi ma `switch` instrukcji i ma nie **domyślne** etykiety.

To ostrzeżenie jest domyślnie wyłączona. Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.

Poniższy przykład spowoduje wygenerowanie C4062:

```
// C4062.cpp
// compile with: /W4
#pragma warning(default : 4062)
enum E { a, b, c };
void func ( E e ) {
   switch(e) {
      case a:
      case b:
      break;   // no default label
   }   // C4062, enumerate 'c' not handled
}

int main() {
}
```