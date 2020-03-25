---
title: Ostrzeżenie kompilatora (poziom 1) C4822
ms.date: 11/04/2016
f1_keywords:
- C4822
helpviewer_keywords:
- C4822
ms.assetid: 0f231a30-2eb0-4722-aaa0-e2d19d3e7eea
ms.openlocfilehash: 59c42227c7e8be9bd31c37776d9724d23db61837
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174872"
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
