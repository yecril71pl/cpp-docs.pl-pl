---
title: Kompilator ostrzeżenie (poziom 3) C4823
ms.date: 11/04/2016
f1_keywords:
- C4823
helpviewer_keywords:
- C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
ms.openlocfilehash: 28d490c341c4d14c2e6c03e13007b5a8be423622
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625917"
---
# <a name="compiler-warning-level-3-c4823"></a>Kompilator ostrzeżenie (poziom 3) C4823

'Funkcja': unieruchamiania wskaźników ale unwind używa semantyki nie są włączone. Rozważ użycie opcji/eha

Aby odpiąć obiektu w zarządzanym stosie, wskazywana przez wskaźnik przypinania, zadeklarowana w zakresie bloku, kompilator symuluje działanie destruktory klas lokalnych "imitujących" przypiętego wskaźnika ma destruktor, który nullifies wskaźnika. Aby włączyć po wywołaniu destruktora po zostanie zgłoszony wyjątek, należy włączyć rozwinięcia obiektu, co można zrobić za pomocą [/ehsc](../../build/reference/eh-exception-handling-model.md).

Można też ręcznie Odepnij obiektu i zignorować to ostrzeżenie.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4823.

```
// C4823.cpp
// compile with: /clr /W3 /EHa-
using namespace System;

ref struct G {
   int m;
};

void f(G ^ pG) {
   try {
      pin_ptr<int> p = &pG->m;
      // manually unpin, ignore warning
      // p = nullptr;
      throw gcnew Exception;
   }
   catch(Exception ^) {}
}   // C4823 warning

int main() {
   f( gcnew G );
}
```
