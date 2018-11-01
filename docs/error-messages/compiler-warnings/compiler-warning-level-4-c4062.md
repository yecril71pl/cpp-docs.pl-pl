---
title: Kompilator ostrzeżenie (poziom 4) C4062
ms.date: 11/04/2016
f1_keywords:
- C4062
helpviewer_keywords:
- C4062
ms.assetid: 36d1c6ae-c917-4b08-bf30-2eb49ee94169
ms.openlocfilehash: 6a7129f71eebb33e7bde333dfd90ed4ca173d44c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602647"
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