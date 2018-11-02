---
title: Błąd kompilatora C2144
ms.date: 11/04/2016
f1_keywords:
- C2144
helpviewer_keywords:
- C2144
ms.assetid: 49f3959b-324f-4c06-9588-c0ecef5dc5b3
ms.openlocfilehash: f6472fc70ee4a86bed1422941e758127009f14cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483333"
---
# <a name="compiler-error-c2144"></a>Błąd kompilatora C2144

> Błąd składniowy: "*typu*"powinien być poprzedzony"*tokenu*"

Kompilator oczekuje *tokenu* i znaleźć *typu* zamiast tego.

Ten błąd może być spowodowany przez brak zamykającego nawiasu klamrowego, prawy nawias okrągły lub średnika.

C2144 może również wystąpić podczas próby utworzenia makra ze słowem kluczowym CLR, która zawiera znak odstępu.

C2144 może być też widoczny, jeśli próbujesz przekazywanie dalej typu. Zobacz [przekazywania dalej typów (C + +/ CLI)](../../windows/type-forwarding-cpp-cli.md) Aby uzyskać więcej informacji.

## <a name="examples"></a>Przykłady

Poniższy przykład generuje C2144 i pokazuje sposób, aby rozwiązać ten problem:

```cpp
// C2144.cpp
// compile with: /clr /c
#define REF ref
REF struct MyStruct0;   // C2144

// OK
#define REF1 ref struct
REF1 MyStruct1;
```

Poniższy przykład generuje C2144 i pokazuje sposób, aby rozwiązać ten problem:

```cpp
// C2144_2.cpp
// compile with: /clr /c
ref struct X {

   property double MultiDimProp[,,] {   // C2144
   // try the following line instead
   // property double MultiDimProp[int , int, int] {
      double get(int, int, int) { return 1; }
      void set(int i, int j, int k, double l) {}
   }

   property double MultiDimProp2[] {   // C2144
   // try the following line instead
   // property double MultiDimProp2[int] {
      double get(int) { return 1; }
      void set(int i, double l) {}
   }
};
```