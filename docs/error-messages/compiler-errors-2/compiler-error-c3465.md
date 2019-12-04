---
title: Błąd kompilatora C3465
ms.date: 11/04/2016
f1_keywords:
- C3465
helpviewer_keywords:
- C3465
ms.assetid: aeb815e5-b3fc-4525-afe2-d738e9321df1
ms.openlocfilehash: 1d82d367c5b77f54548403b7b142aa740919b6c2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756568"
---
# <a name="compiler-error-c3465"></a>Błąd kompilatora C3465

Aby użyć typu "Type", należy odwołać się do zestawu "Assembly"

Przekazywanie typu będzie działało dla aplikacji klienckiej do momentu ponownego skompilowania klienta. Po ponownym skompilowaniu wymagane jest odwołanie do każdego zestawu zawierającego definicję typu używanego w aplikacji klienckiej.

Aby uzyskać więcej informacji, zobacz [przekazywanie typuC++(/CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład kompiluje zestaw, który zawiera nową lokalizację typu.

```cpp
// C3465.cpp
// compile with: /clr /LD
public ref class R {
public:
   ref class N {};
};
```

## <a name="example"></a>Przykład

Poniższy przykład kompiluje zestaw, który zawiera definicję typu, ale teraz zawiera składnię przekazywania dla tego typu.

```cpp
// C3465_b.cpp
// compile with: /clr /LD
#using "C3465.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
```

## <a name="example"></a>Przykład

Poniższy przykład generuje C3465.

```cpp
// C3465_c.cpp
// compile with: /clr
// C3465 expected
#using "C3465_b.dll"
// Uncomment the following line to resolve.
// #using "C3465.dll"

int main() {
   R^ r = gcnew R();
}
```
