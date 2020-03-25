---
title: Ostrzeżenie kompilatora (poziom 1) C4002
ms.date: 11/04/2016
f1_keywords:
- C4002
helpviewer_keywords:
- C4002
ms.assetid: 6bda1dfe-e2e4-4771-9794-5a404c466dd5
ms.openlocfilehash: cb1e36a606f5c8bb0a1622260d64124264f0db32
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164771"
---
# <a name="compiler-warning-level-1-c4002"></a>Ostrzeżenie kompilatora (poziom 1) C4002

zbyt wiele parametrów rzeczywistych dla makra "identifier"

Liczba rzeczywistych parametrów w makrze przekracza liczbę parametrów formalnych w definicji makra. Preprocesor zbiera dodatkowe parametry, ale ignoruje je podczas rozwinięcia makra.

C4002 może wystąpić w przypadku nieprawidłowego użycia [makr wariadyczne](../../preprocessor/variadic-macros.md).

Poniższy przykład generuje C4002:

```cpp
// C4002.cpp
// compile with: /W1
#define test(a) (a)

int main() {
   int a = 1;
   int b = 2;
   a = test(a,b);   // C4002
   // try..
   a = test(a);
}
```

Ten błąd może być również wygenerowany jako wynik zgodności kompilatora, który został wykonany dla programu Visual Studio .NET 2003: dodatkowe przecinki w makrze nie są już akceptowane.

Kompilator nie będzie już akceptować dodatkowych przecinków w makrze. Aby kod był prawidłowy zarówno w programie Visual Studio .NET 2003, jak i w wersji Visual Studio .NET C++, Usuń dodatkowe przecinki.

```cpp
// C4002b.cpp
// compile with: /W1
#define F(x,y)
int main()
{
   F(2,,,,,,3,,,,,,)   // C4002
   // Try the following line instead:
   // F(2,3)
}
```
