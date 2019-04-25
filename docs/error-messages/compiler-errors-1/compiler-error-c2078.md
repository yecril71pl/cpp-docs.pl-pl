---
title: Błąd kompilatora C2078
ms.date: 11/04/2016
f1_keywords:
- C2078
helpviewer_keywords:
- C2078
ms.assetid: 9bead850-4123-46cf-a634-5c77ba974b2b
ms.openlocfilehash: a800a6efa6e02f323b4b6597f1aa983f13674e83
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182811"
---
# <a name="compiler-error-c2078"></a>Błąd kompilatora C2078

zbyt wiele inicjatorów

Inicjatory przekracza liczbę obiektów do zainicjowania.

Kompilator może wywnioskować prawidłowe przypisanie inicjatory obiektów i obiektów wewnętrznych, gdy wewnętrzny nawiasy klamrowe są czy opuszczony na liście inicjatora. Pełne tężników również eliminuje niejednoznaczności i powoduje przypisanie poprawne. Częściowe tężników może spowodować C2078 z powodu niejednoznaczności w przypisaniu inicjatorów obiektów.

Poniższy przykład generuje C2078 i pokazuje, jak go naprawić:

```
// C2078.cpp
// Compile by using: cl /c /W4 C2078.cpp
struct S {
   struct {
      int x, y;
   } z[2];
};

int main() {
   int d[2] = {1, 2, 3};   // C2078
   int e[2] = {1, 2};      // OK

   char a[] = {"a", "b"};  // C2078
   char *b[] = {"a", "b"}; // OK
   char c[] = {'a', 'b'};  // OK

   S s1{1, 2, 3, 4};       // OK
   S s2{{1, 2}, {3, 4}};   // C2078
   S s3{{1, 2, 3, 4}};     // OK
   S s4{{{1, 2}, {3, 4}}}; // OK
}
```