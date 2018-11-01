---
title: Kompilator ostrzeżenie (poziom 1) C4532
ms.date: 11/04/2016
f1_keywords:
- C4532
helpviewer_keywords:
- C4532
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
ms.openlocfilehash: bcadf31eda079ebb8ea7a496efe4c945e16b1ab7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622849"
---
# <a name="compiler-warning-level-1-c4532"></a>Kompilator ostrzeżenie (poziom 1) C4532

"continue": skok poza __finally/blok finally ma niezdefiniowane zachowanie podczas obsługi zakończenia

Kompilator napotkał jedną z następujących słów kluczowych:

- [continue](../../cpp/continue-statement-cpp.md)

- [break](../../cpp/break-statement-cpp.md)

- [goto](../../cpp/goto-statement-cpp.md)

powoduje skok poza [__finally](../../cpp/try-finally-statement.md) lub [na koniec](../../dotnet/finally.md) blok podczas Nienormalne zakończenie.

Jeśli wystąpi wyjątek, a gdy jest on odwinięty stosu podczas wykonywania funkcji obsługi zakończenia ( `__finally` lub na końcu blokuje), a kod przechodzi z `__finally` blokować przed `__finally` kończy się blok, zachowanie jest niezdefiniowane. Kontrolki mogą nie zwracać odwijania kodu, więc wyjątek może nie być obsługiwane poprawnie.

Jeśli musisz przejść z **__finally** zablokować, najpierw sprawdzić Nienormalne zakończenie.

Poniższy przykład spowoduje wygenerowanie C4532; po prostu komentarz instrukcji skoku, aby rozwiązać problem z ostrzeżeniami.

```
// C4532.cpp
// compile with: /W1
// C4532 expected
int main() {
   int i;
   for (i = 0; i < 10; i++) {
      __try {
      } __finally {
         // Delete the following line to resolve.
         continue;
      }

      __try {
      } __finally {
         // Delete the following line to resolve.
         break;
      }
   }
}
```