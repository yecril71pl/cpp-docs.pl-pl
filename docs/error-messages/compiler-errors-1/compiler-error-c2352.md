---
title: Błąd kompilatora C2352
ms.date: 11/04/2016
f1_keywords:
- C2352
helpviewer_keywords:
- C2352
ms.assetid: 0efad8cb-659f-4b3e-8f6f-9f8ec44d345c
ms.openlocfilehash: 95b3a3bae531170bf12c0e34613ad41f742304bb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218250"
---
# <a name="compiler-error-c2352"></a>Błąd kompilatora C2352

"Class:: Function": niedozwolone wywołanie niestatycznej funkcji składowej

**`static`** Funkcja członkowska o nazwie niestatycznej funkcji członkowskiej. Lub niestatyczna funkcja członkowska została wywołana spoza klasy jako funkcji statycznej.

Poniższy przykład generuje C2352 i pokazuje, jak to naprawić:

```cpp
// C2352.cpp
// compile with: /c
class CMyClass {
public:
   static void func1();
   void func2();
   static void func3() {
      func2();   // C2352 calls nonstatic func2
      func1();   // OK calls static func1
   }
};
```

Poniższy przykład generuje C2352 i pokazuje, jak to naprawić:

```cpp
// C2352b.cpp
class MyClass {
public:
   void MyFunc() {}
   static void MyFunc2() {}
};

int main() {
   MyClass::MyFunc();   // C2352
   MyClass::MyFunc2();   // OK
}
```
