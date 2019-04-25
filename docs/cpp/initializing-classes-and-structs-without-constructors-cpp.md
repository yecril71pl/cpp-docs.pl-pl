---
title: Inicjowanie klas i struktur bez konstruktorów (C++)
ms.date: 10/17/2018
ms.assetid: 3e55c3d6-1c6b-4084-b9e5-221b151402f4
ms.openlocfilehash: 4f696f4fc8862b953e40a03c96b88d1a0b7f720b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183417"
---
# <a name="initializing-classes-and-structs-without-constructors-c"></a>Inicjowanie klas i struktur bez konstruktorów (C++)

Nie zawsze jest konieczne zdefiniować Konstruktor dla klasy, szczególnie te, które są stosunkowo proste. Użytkownicy mogą Inicjowanie obiektów klasy lub struktury za pomocą jednolite inicjowanie, jak pokazano w poniższym przykładzie:

```cpp
// no_constructor.cpp
// Compile with: cl /EHsc no_constructor.cpp
#include <time.h>

// No constructor
struct TempData
{
    int StationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

// Has a constructor
struct TempData2
{
    TempData2(double minimum, double maximum, double cur, int id, time_t t) :
       stationId{id}, timeSet{t}, current{cur}, maxTemp{maximum}, minTemp{minimum} {}
    int stationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

int main()
{
    time_t time_to_set;

    // Member initialization (in order of declaration):
    TempData td{ 45978, time(&time_to_set), 28.9, 37.0, 16.7 };

    // Default initialization = {0,0,0,0,0}
    TempData td_default{};

    // Uninitialized = if used, emits warning C4700 uninitialized local variable
    TempData td_noInit;

    // Member declaration (in order of ctor parameters)
    TempData2 td2{ 16.7, 37.0, 28.9, 45978, time(&time_to_set) };

    return 0;
}
```

Należy pamiętać, że po klasie lub strukturze nie ma konstruktora, zapewniasz elementy listy w kolejności, że elementy członkowskie są zadeklarowane w klasie. Jeśli klasa ma Konstruktor, należy podać elementów zgodnie z kolejnością parametrów.

## <a name="see-also"></a>Zobacz także

[Klasy i struktury](../cpp/classes-and-structs-cpp.md)<br/>
[Konstruktory](../cpp/constructors-cpp.md)
