---
title: Kompilator ostrzeżenie (poziom 4) C4255
ms.date: 11/04/2016
f1_keywords:
- C4255
helpviewer_keywords:
- C4255
ms.assetid: 2087b635-4b4c-4182-8a01-c26770d2bb88
ms.openlocfilehash: 1796e28e88bbe52c4c21ffdf0a8a96a278a44388
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566637"
---
# <a name="compiler-warning-level-4-c4255"></a>Kompilator ostrzeżenie (poziom 4) C4255

'Funkcja': nie podano prototypu funkcji: konwertowanie '()"na"(void)"

Kompilator nie znalazł jawną listę argumentów funkcji. To ostrzeżenie jest tylko kompilator języka C.

To ostrzeżenie jest domyślnie wyłączona. Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.

Poniższy przykład spowoduje wygenerowanie C4255:

```
// C4255.c
// compile with: /W4 /WX
#pragma warning (default : 4255)

void f()  { // C4255
// try the following line instead
//void f(void) {
}

int main(int argc, char *argv[]) {
   f();
}
```