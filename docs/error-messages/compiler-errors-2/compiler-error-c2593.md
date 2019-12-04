---
title: Błąd kompilatora C2593
ms.date: 11/04/2016
f1_keywords:
- C2593
helpviewer_keywords:
- C2593
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
ms.openlocfilehash: 2a385e35376ddce528678980705595bfb98aca95
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759350"
---
# <a name="compiler-error-c2593"></a>Błąd kompilatora C2593

"Identyfikator operatora" jest niejednoznaczny

Zdefiniowano więcej niż jeden możliwy operator dla przeciążonego operatora.

Ten błąd może zostać naprawiony, jeśli używasz jawnego rzutowania dla co najmniej jednego rzeczywistego parametru.

Poniższy przykład generuje C2593:

```cpp
// C2593.cpp
struct A {};
struct B : A {};
struct X {};
struct D : B, X {};
void operator+( X, X );
void operator+( A, B );
D d;

int main() {
   d +  d;         // C2593, D has an A, B, and X
   (X)d + (X)d;    // OK, uses operator+( X, X )
}
```

Ten błąd może być spowodowany serializacji zmiennej zmiennoprzecinkowej przy użyciu obiektu `CArchive`. Kompilator identyfikuje operatora `<<` jako niejednoznaczny. Tylko typy pierwotne C++ , które `CArchive` mogą serializować, są typami o ustalonym rozmiarze `BYTE`, `WORD`, `DWORD`i `LONG`. Wszystkie typy całkowite muszą być rzutowane na jeden z tych typów do serializacji. Typy zmiennoprzecinkowe muszą być archiwizowane przy użyciu funkcji składowej `CArchive::Write()`.

Poniższy przykład pokazuje, jak zarchiwizować zmienną zmiennoprzecinkową (`f`) do `ar`archiwum:

```
ar.Write(&f, sizeof( float ));
```
