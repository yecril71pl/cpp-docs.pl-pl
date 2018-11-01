---
title: Błąd kompilatora C3623
ms.date: 11/04/2016
f1_keywords:
- C3623
helpviewer_keywords:
- C3623
ms.assetid: a0341b45-062a-4f67-beb9-ba74201ed1ed
ms.openlocfilehash: dd12e64e775807220b4ece1f4c26a2f52437c69e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473466"
---
# <a name="compiler-error-c3623"></a>Błąd kompilatora C3623

'Zmienna': pola bitowe nie są obsługiwane w zarządzanych lub typów WinRT

Użyj pól bitowych nie jest dozwolona w zmiennych w zarządzanej lub klasa WinRT.

Poniższy przykład spowoduje wygenerowanie C3623:

```
// C3623.cpp
// compile with: /clr
using namespace System;
ref class CMyClass {
public:
   int i : 1;   // C3623
};

int main() {
   CMyClass^ pMyClass = gcnew CMyClass();
   pMyClass->i = 3;
   Console::Out->WriteLine(pMyClass->i);
}
```
