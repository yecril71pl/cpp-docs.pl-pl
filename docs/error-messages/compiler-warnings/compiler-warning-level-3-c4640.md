---
title: Kompilator ostrzeżenie (poziom 3) C4640
ms.date: 11/04/2016
f1_keywords:
- C4640
helpviewer_keywords:
- C4640
ms.assetid: f76871f6-e436-4c35-9793-d2f22f7e1c7f
ms.openlocfilehash: ccfb82852325437a739d7a8f8a5c5b06ce5f9714
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538540"
---
# <a name="compiler-warning-level-3-c4640"></a>Kompilator ostrzeżenie (poziom 3) C4640

'instancja': konstrukcja lokalnego obiektu statycznego nie jest bezpieczna dla wątków

Statyczne wystąpienie obiektu nie jest bezpieczny dla wątków.

To ostrzeżenie jest domyślnie wyłączona. Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.

Poniższy przykład spowoduje wygenerowanie C4640:

```
// C4640.cpp
// compile with: /W3
#pragma warning(default:4640)

class X {
public:
   X() {
   }
};

void f() {
   static X aX;   // C4640
}

int main() {
   f();
}
```