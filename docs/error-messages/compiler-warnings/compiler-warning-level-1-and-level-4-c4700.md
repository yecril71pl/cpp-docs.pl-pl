---
title: Kompilator C4700 ostrzegawcze (poziom 1 i 4) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 02/21/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4700
dev_langs:
- C++
helpviewer_keywords:
- C4700
ms.assetid: 2da0deb4-77dd-4b05-98d3-b78d74ac4ca7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 00b871d6199338cc3040d6bddedb85f8732dfccd
ms.sourcegitcommit: 4e416049665819ac62f5300ddf86e94adede4ba0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="compiler-warning-level-1-and-level-4-c4700"></a>Ostrzeżenie C4700 kompilatora (poziom 1 i 4)

> niezainicjowanej zmiennej lokalnej "*nazwa*" używane

Zmienna lokalna *nazwa* został *używane*, oznacza to, odczytywać, zanim ma zostanie przypisana wartość. C i C++ zmienne lokalne nie są domyślnie zainicjowane. Niezainicjowanych zmiennych może zawierać żadnej wartości, i ich użycia prowadzi do niezdefiniowane zachowanie. Ostrzeżenie C4700 prawie zawsze informuje usterkę, która może spowodować nieoczekiwane wyniki lub awarie w programie.

Aby rozwiązać ten problem, można zainicjować zmienne lokalne, gdy są one zgłoszone lub przypisać wartość do nich, zanim zostaną użyte. Funkcja można zainicjować zmiennej, który jest przekazywany jako parametru odwołania lub po jego adres jest przekazywana jako parametr wskaźnika.

## <a name="example"></a>Przykład

W tym przykładzie generuje C4700, gdy zmienne t, u i v są używane przed zainicjowaniem i przedstawia rodzaj wartość pamięci, która może spowodować. Zmienne x, y oraz czy z powodują ostrzeżenia, ponieważ są one inicjowane przed użyciem:

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

Gdy ten kod jest uruchamianie, t, u i v niezainicjowanej, i dane wyjściowe dla s nieprzewidywalne:

```Output
Value in s: 37816963
Value in w: 42
```
