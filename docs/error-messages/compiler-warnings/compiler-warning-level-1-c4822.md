---
title: Kompilator ostrzeżenie (poziom 1) C4822
ms.date: 11/04/2016
f1_keywords:
- C4822
helpviewer_keywords:
- C4822
ms.assetid: 0f231a30-2eb0-4722-aaa0-e2d19d3e7eea
ms.openlocfilehash: 02e7ba11f7bda134bcc98ce2c494a3ef367c0d6f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591246"
---
# <a name="compiler-warning-level-1-c4822"></a>Kompilator ostrzeżenie (poziom 1) C4822

"członek": funkcja składowa klasy lokalnej nie ma treści

Funkcja składowa klasy lokalnej został zadeklarowany, ale nie jest zdefiniowany w klasie. Aby korzystać z funkcji składowej klasy lokalnej, należy zdefiniować go w klasie. Nie można zadeklarować ją w klasie i definiowania go z klasy.

Wszelkie definicji klasy dla funkcji członkowskiej klasy lokalnej będzie błąd.

Poniższy przykład spowoduje wygenerowanie C4822:

```
// C4822.cpp
// compile with: /W1
int main() {
   struct C {
      void func1(int);   // C4822
      // try the following line instead
      // void func1(int){}
  };
}
```