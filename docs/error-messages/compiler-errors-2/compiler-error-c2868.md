---
title: Błąd kompilatora C2868
ms.date: 11/04/2016
f1_keywords:
- C2868
helpviewer_keywords:
- C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
ms.openlocfilehash: 0cbcf7dc80aedc554594f88992059f98b7091c21
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201642"
---
# <a name="compiler-error-c2868"></a>Błąd kompilatora C2868

> "*Identyfikator*": niedozwolona składnia dla deklaracji using; Oczekiwano kwalifikowanej nazwy

[Deklaracja using](../../cpp/using-declaration.md) wymaga *nazwy kwalifikowanej*, oddzielonej do operatora zakresu (`::`) sekwencji nazw, klasy lub wyliczenia, które kończą się nazwą identyfikatora. Aby wprowadzić nazwę z globalnej przestrzeni nazw, można użyć operatora rozpoznawania pojedynczego zakresu.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2868, a także wyświetla poprawne użycie:

```cpp
// C2868.cpp
class X {
public:
   int i;
};

class Y : X {
public:
   using X::i;   // OK
};

int main() {
   using X;   // C2868
}
```
