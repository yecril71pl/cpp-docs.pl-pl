---
title: Błąd kompilatora C2144
ms.date: 11/04/2016
f1_keywords:
- C2144
helpviewer_keywords:
- C2144
ms.assetid: 49f3959b-324f-4c06-9588-c0ecef5dc5b3
ms.openlocfilehash: b917c0a2c15aeb70222c948bce9a6fb275c91068
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80207249"
---
# <a name="compiler-error-c2144"></a>Błąd kompilatora C2144

> Błąd składniowy: element "*Type*" powinien być poprzedzony "*tokenem*"

Kompilator oczekiwał *tokenu* i znaleziono *Typ* .

Ten błąd może być spowodowany brakiem zamykającego nawiasu klamrowego, prawego nawiasu lub średnika.

C2144 może również wystąpić podczas próby utworzenia makra ze słowa kluczowego CLR, które zawiera biały znak.

Jeśli próbujesz wykonać przekazywanie dalej, możesz również zobaczyć C2144. Aby uzyskać więcej informacji, zobacz [przekazywanie typu (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md) .

## <a name="examples"></a>Przykłady

Poniższy przykład generuje C2144 i przedstawia sposób jego rozwiązania:

```cpp
// C2144.cpp
// compile with: /clr /c
#define REF ref
REF struct MyStruct0;   // C2144

// OK
#define REF1 ref struct
REF1 MyStruct1;
```

Poniższy przykład generuje C2144 i przedstawia sposób jego rozwiązania:

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
