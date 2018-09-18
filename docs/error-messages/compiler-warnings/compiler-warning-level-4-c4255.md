---
title: Kompilator ostrzeżenie (poziom 4) C4255 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4255
dev_langs:
- C++
helpviewer_keywords:
- C4255
ms.assetid: 2087b635-4b4c-4182-8a01-c26770d2bb88
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72e07cc1077993e1bb22c5d8af4ce4445d38321b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032383"
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