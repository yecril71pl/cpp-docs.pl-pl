---
title: Błąd kompilatora C2993
ms.date: 11/04/2016
f1_keywords:
- C2993
helpviewer_keywords:
- C2993
ms.assetid: 4ffd2b78-654b-46aa-95a6-b62101cf91c8
ms.openlocfilehash: 5aa0d27b2d469f53ec521f587172398b7d4c2d1b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761234"
---
# <a name="compiler-error-c2993"></a>Błąd kompilatora C2993

"Identyfikator": niedozwolony typ dla parametru szablonu bez typu "parameter"

Nie można zadeklarować szablonu ze strukturą lub argumentem Union. Użyj wskaźników, aby przekazać struktury i związki jako parametry szablonu.

Poniższy przykład generuje C2993:

```cpp
// C2993.cpp
// compile with: /c
// C2993 expected
struct MyStruct {
   int a;char b;
};

template <class T, struct MyStruct S>   // C2993

// try the following line instead
// template <class T, struct MyStruct * S>
class CMyClass {};
```

Ten błąd zostanie również wygenerowany w wyniku działania kompilatora, który został wykonany w programie Visual Studio .NET 2003: parametry szablonu bez typu zmiennoprzecinkowego nie są już dozwolone. C++ Standard nie zezwala na zmiennoprzecinkowe parametry szablonu bez typu.

Jeśli jest to szablon funkcji, należy użyć argumentu funkcji, aby przekazać parametr szablonu bez typu zmiennoprzecinkowego (ten kod będzie prawidłowy w Visual Studio .NET 2003 i Visual Studio .NET wersjach wizualizacji C++). Jeśli jest to szablon klasy, nie ma żadnego prostego obejścia.

```cpp
// C2993b.cpp
// compile with: /c
template<class T, float f> void func(T) {}   // C2993

// OK
template<class T>   void func2(T, float) {}
```
