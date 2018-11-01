---
title: Błąd kompilatora C2993
ms.date: 11/04/2016
f1_keywords:
- C2993
helpviewer_keywords:
- C2993
ms.assetid: 4ffd2b78-654b-46aa-95a6-b62101cf91c8
ms.openlocfilehash: 5be4836332f67f2064f60a3b058db159a18ca1e0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605029"
---
# <a name="compiler-error-c2993"></a>Błąd kompilatora C2993

'Identyfikator': niedozwolony typ dla parametru szablonu bez typu "parametru"

Nie można zadeklarować szablon ze struktury lub Unii argumentu. Użycie wskaźników do przekazywania struktur i Unii jako parametry szablonu.

Poniższy przykład spowoduje wygenerowanie C2993:

```
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

Ten błąd będzie też można wygenerować w wyniku pracy zgodności kompilatora, która została wykonana w Visual Studio .NET 2003: zmiennoprzecinkowa parametry szablonu bez typu nie są już dozwolone. C++ standard nie zezwala na zmiennoprzecinkowej parametrów szablonu-typu.

Jeśli jest szablonem funkcji, użyj argumentu funkcji do przekazania w zmeinnoprzecinkowych punktu parametru szablonu bez typu (ten kod będzie prawidłowy w wersjach programu Visual Studio .NET 2003 i Visual Studio .NET, Visual c++). Jeśli szablon klasy, nie ma łatwego sposobu obejścia.

```
// C2993b.cpp
// compile with: /c
template<class T, float f> void func(T) {}   // C2993

// OK
template<class T>   void func2(T, float) {}
```