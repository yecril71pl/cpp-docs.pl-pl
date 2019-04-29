---
title: Kompilator ostrzeżenie (poziom 2) C4244
ms.date: 11/04/2016
f1_keywords:
- C4244
helpviewer_keywords:
- C4244
ms.assetid: 2c19d157-21d1-42c2-a6c0-3f30f2ce3813
ms.openlocfilehash: af821d80ff8c4c7717986f2ff4d0f3392cd6fca3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349727"
---
# <a name="compiler-warning-level-2-c4244"></a>Kompilator ostrzeżenie (poziom 2) C4244

"argument": konwersja z 'Typ1' na 'Typ2', możliwa utrata danych

Element typu punktu zmiennoprzecinkowego został przekonwertowany na typ liczby całkowitej.  Może wystąpić możliwa utrata danych.

Jeśli C4244, powinny albo zmienić program, aby używać zgodnych typów lub dodać logikę do kodu, aby upewnić się, że zakres możliwych wartości zawsze będzie zgodny z typami, którego używasz.

C4244 można również wyzwalać na poziomie 3 i 4; zobacz [ostrzeżenie kompilatora (poziomy 3 i 4) C4244](../../error-messages/compiler-warnings/compiler-warning-levels-3-and-4-c4244.md) Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4244:

```
// C4244_level2.cpp
// compile with: /W2

int f(int x){ return 0; }
int main() {
   double x = 10.1;
   int i = 10;
   return (f(x));   // C4244
   // try the following line instead
   // return (f(i));
}
```