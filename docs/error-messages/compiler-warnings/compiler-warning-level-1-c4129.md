---
title: Kompilator ostrzeżenie (poziom 1) C4129
ms.date: 11/04/2016
f1_keywords:
- C4129
helpviewer_keywords:
- C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
ms.openlocfilehash: dc4f4c4c1feeba543ce0baa71e1ee5dfd81fdcae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428680"
---
# <a name="compiler-warning-level-1-c4129"></a>Kompilator ostrzeżenie (poziom 1) C4129

"character": nierozpoznany znak sekwencji ucieczki

`character` Ukośniku odwrotnym (\\) znaku lub ciągu stała nie został rozpoznany jako prawidłowy sekwencje. Ukośnik odwrotny jest ignorowane i nie są wyświetlane. Znak po ukośniku odwrotnym jest drukowany.

Aby wydrukować pojedynczy ukośnik odwrotny, należy określić podwójny ukośnik odwrotny (\\\\).

Standard C++, w sekcji 2.13.2 omawia unikowe.

Poniższy przykład spowoduje wygenerowanie C4129:

```
// C4129.cpp
// compile with: /W1
int main() {
   char array1[] = "\/709";   // C4129
   char array2[] = "\n709";   // OK
}
```