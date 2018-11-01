---
title: Ostrzeżenie C4700 kompilatora (poziom 1 i 4)
ms.date: 02/21/2018
f1_keywords:
- C4700
helpviewer_keywords:
- C4700
ms.assetid: 2da0deb4-77dd-4b05-98d3-b78d74ac4ca7
ms.openlocfilehash: fa3326bd5ab495dbc4c54130bb168422eb827dce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463222"
---
# <a name="compiler-warning-level-1-and-level-4-c4700"></a>Ostrzeżenie C4700 kompilatora (poziom 1 i 4)

> niezainicjowanej zmiennej lokalnej "*nazwa*" używane

Zmienna lokalna *nazwa* został *używane*, oznacza to, odczytywanie, zanim ma przypisaną wartość. W językach C i C++ zmienne lokalne nie są inicjowane domyślnie. Niezainicjowane zmienne może zawierać żadnej wartości, a ich użycie prowadzi do niezdefiniowanego zachowania. Ostrzeżenie C4700 prawie zawsze wskazuje usterkę, która może spowodować nieprzewidywalne skutki lub awarie w programach.

Aby rozwiązać ten problem, można zainicjować zmienne lokalne, gdy są one zadeklarowane lub przypisać wartość do nich, zanim zostaną użyte. Funkcja może służyć do zainicjowania zmiennej, który jest przekazywany jako parametr przekazany przez odwołanie, lub po jego adres jest przekazywany jako parametr wskaźnika.

## <a name="example"></a>Przykład

Ten przykład generuje C4700, gdy zmienne t, u i v są używane przed są inicjowane i pokazuje rodzaj wartość pamięci, która może spowodować. Zmienne x, y i z czy powoduje ostrzeżenie, ponieważ są one zainicjowane przed użyciem:

```cpp
// c4700.cpp
// compile by using: cl /EHsc /W4 c4700.cpp
#include <iostream>

// function takes an int reference to initialize
void initialize(int& i)
{
    i = 21;
}

int main()
{
    int s, t, u, v;   // Danger, uninitialized variables

    s = t + u + v;    // C4700: t, u, v used before initialization
    std::cout << "Value in s: " << s << std::endl;

    int w, x;         // Danger, uninitialized variables
    initialize(x);    // fix: call function to init x before use
    int y{10};        // fix: initialize y, z when declared
    int z{11};        // This C++11 syntax is recommended over int z = 11;

    w = x + y + z;    // Okay, all values initialized before use
    std::cout << "Value in w: " << w << std::endl;
}
```

Gdy ten kod jest Uruchom "," t "," u "i" v są niezainicjowanej, a dane wyjściowe s jest nieprzewidywalne:

```Output
Value in s: 37816963
Value in w: 42
```
