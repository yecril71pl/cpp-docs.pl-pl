---
title: Ostrzeżenie kompilatora (poziom 1) C4532
ms.date: 11/04/2016
f1_keywords:
- C4532
helpviewer_keywords:
- C4532
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
ms.openlocfilehash: b47eb192bc01e6fe2c6c9423ed2c672f16c6818f
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966252"
---
# <a name="compiler-warning-level-1-c4532"></a>Ostrzeżenie kompilatora (poziom 1) C4532

"Kontynuuj": Wyskocz z __finally bloku/finally ma niezdefiniowane zachowanie podczas obsługi zakończenia

Kompilator napotkał jedno z następujących słów kluczowych:

- [continue](../../cpp/continue-statement-cpp.md)

- [break](../../cpp/break-statement-cpp.md)

- [goto](../../cpp/goto-statement-cpp.md)

powodowanie przejścia z [__finally](../../cpp/try-finally-statement.md) lub [finally](../../dotnet/finally.md) bloku podczas nietypowego zakończenia.

Jeśli wystąpi wyjątek, a podczas gdy stos jest usuwany podczas wykonywania programów obsługi zakończenia (`__finally` lub finally), a kod przechodzi z bloku `__finally` przed zakończeniem bloku `__finally`, zachowanie jest niezdefiniowane. Formant nie może powrócić do kodu odwinięcia, więc wyjątek może nie być obsługiwany prawidłowo.

Jeśli musisz wyskoczyć z bloku **__finally** , najpierw sprawdź, czy nie określono nietypowego zakończenia.

Poniższy przykład generuje C4532; po prostu Dodaj komentarz do instrukcji skoku, aby rozwiązać ostrzeżenia.

```cpp
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