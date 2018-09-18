---
title: Kompilator ostrzeżenie (poziom 1) C4822 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4822
dev_langs:
- C++
helpviewer_keywords:
- C4822
ms.assetid: 0f231a30-2eb0-4722-aaa0-e2d19d3e7eea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33748a39eae4b6f2a84cadb818570f9a311b1fe1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078325"
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