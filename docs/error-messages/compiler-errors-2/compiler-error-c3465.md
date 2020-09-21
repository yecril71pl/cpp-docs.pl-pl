---
title: Błąd kompilatora C3465
ms.date: 11/04/2016
f1_keywords:
- C3465
helpviewer_keywords:
- C3465
ms.assetid: aeb815e5-b3fc-4525-afe2-d738e9321df1
ms.openlocfilehash: 56eeac18d5b8efc32501bf54e2de3aa216e05a13
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742024"
---
# <a name="compiler-error-c3465"></a>Błąd kompilatora C3465

Aby użyć typu "Type", należy odwołać się do zestawu "Assembly"

Przekazywanie typu będzie działało dla aplikacji klienckiej do momentu ponownego skompilowania klienta. Po ponownym skompilowaniu wymagane jest odwołanie do każdego zestawu zawierającego definicję typu używanego w aplikacji klienckiej.

Aby uzyskać więcej informacji, zobacz [przekazywanie dalej typu (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="examples"></a>Przykłady

Poniższy przykład kompiluje zestaw, który zawiera nową lokalizację typu.

```cpp
// C3465.cpp
// compile with: /clr /LD
public ref class R {
public:
   ref class N {};
};
```

Poniższy przykład kompiluje zestaw, który zawiera definicję typu, ale teraz zawiera składnię przekazywania dla tego typu.

```cpp
// C3465_b.cpp
// compile with: /clr /LD
#using "C3465.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
```

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
