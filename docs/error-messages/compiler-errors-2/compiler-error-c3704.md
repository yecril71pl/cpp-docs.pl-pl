---
title: Błąd kompilatora C3704
ms.date: 11/04/2016
f1_keywords:
- C3704
helpviewer_keywords:
- C3704
ms.assetid: ee40ea35-a214-4dec-9489-d7f155dd0ac2
ms.openlocfilehash: 4e26742de6c294018f81c6f49c1719fdb11d5149
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467119"
---
# <a name="compiler-error-c3704"></a>Błąd kompilatora C3704

'Funkcja': metoda vararg nie może wyzwalać zdarzeń

Podjęto próbę użycia [__event](../../cpp/event.md) na metoda vararg. Aby naprawić ten błąd, należy zastąpić `fireEvent(int i, ...)` wywołanie `fireEvent(int i)` wywołania, jak pokazano w następującym przykładzie kodu.

Poniższy przykład spowoduje wygenerowanie C3704:

```
// C3704.cpp
[ event_source(native) ]
class CEventSrc {
   public:
      __event void fireEvent(int i, ...);   // C3704
      // try the following line instead:
      // __event void fireEvent(int i);
};

int main() {
}
```