---
title: Ostrzeżenie kompilatora (poziom 3) C4823
ms.date: 11/04/2016
f1_keywords:
- C4823
helpviewer_keywords:
- C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
ms.openlocfilehash: a96877252b0b7699f5e4033f8e695f4d9016a6c9
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541266"
---
# <a name="compiler-warning-level-3-c4823"></a>Ostrzeżenie kompilatora (poziom 3) C4823

"Function": używa przypiętych wskaźników, ale semantyka nieprzewinięcia nie jest włączona. Rozważ użycie/EHa

Aby odpiąć obiekt na stosie zarządzanym wskazywanym przez przypięty wskaźnik zadeklarowany w zakresie bloku, kompilator symuluje zachowanie destruktorów klas lokalnych, "" przesłanianie "wskaźnik przypięty ma destruktor, który NULLIFIES wskaźnik. Aby włączyć wywołanie do destruktora po występowaniu wyjątku, należy włączyć odrzucanie obiektów, które można wykonać za pomocą [/EHsc](../../build/reference/eh-exception-handling-model.md).

Można również ręcznie odpiąć obiekt i zignorować ostrzeżenie.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4823.

```cpp
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
