---
title: Ostrzeżenie kompilatora (poziom 1) C4822
ms.date: 11/04/2016
f1_keywords:
- C4822
helpviewer_keywords:
- C4822
ms.assetid: 0f231a30-2eb0-4722-aaa0-e2d19d3e7eea
ms.openlocfilehash: f54f29fcbc6fb71033bc6d1d87c7ddb31622ee40
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051256"
---
# <a name="compiler-warning-level-1-c4822"></a>Ostrzeżenie kompilatora (poziom 1) C4822

"member": Funkcja składowa klasy lokalnej nie ma treści

Funkcja składowej klasy lokalnej została zadeklarowana, ale nie została zdefiniowana w klasie. Aby użyć funkcji składowej klasy lokalnej, należy ją zdefiniować w klasie. Nie można zadeklarować go w klasie i zdefiniować go poza klasą.

Każda definicja poza klasą dla funkcji składowej klasy lokalnej będzie błędem.

Poniższy przykład generuje C4822:

```cpp
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