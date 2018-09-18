---
title: Kompilator ostrzeżenie (poziom 3) C4823 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4823
dev_langs:
- C++
helpviewer_keywords:
- C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c3a6f24a32267f221dbc37e242bae48c0056af5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044655"
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
