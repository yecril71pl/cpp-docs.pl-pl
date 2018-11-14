---
title: Argumenty funkcji typu odwołania
ms.date: 08/27/2018
helpviewer_keywords:
- arguments [C++], function
- functions [C++], parameters
- function parameters [C++], reference-type
- function arguments [C++], reference-type
- passing parameters [C++], reference-type arguments
ms.assetid: 0a70e831-9e76-46c0-821d-aeba13d73cc0
ms.openlocfilehash: 2a0bd21023bd1c6bc14b1f587c85960cf1e8b820
ms.sourcegitcommit: 31a2a9845f5e1d35ab054906d8cdc6582a5220bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2018
ms.locfileid: "51597719"
---
# <a name="reference-type-function-arguments"></a>Argumenty funkcji typu odwołania

Jest często bardziej wydajnym sposobem przekazywania odwołania, a nie dużych obiektów, do funkcji. Dzięki temu kompilator mógł przekazać adres obiektu, przy zachowaniu składni, która będzie używana do dostępu do obiektu. Rozważmy następujący przykład, który używa `Date` strukturę:

```cpp
// reference_type_function_arguments.cpp
#include <iostream>

struct Date
{
    short Month;
    short Day;
    short Year;
};

// Create a date of the form DDDYYYY (day of year, year)
// from a Date.
long DateOfYear( Date& date )
{
    static int cDaysInMonth[] = {
        31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31
    };
    long dateOfYear = 0;

    // Add in days for months already elapsed.
    for ( int i = 0; i < date.Month - 1; ++i )
        dateOfYear += cDaysInMonth[i];

    // Add in days for this month.
    dateOfYear += date.Day;

    // Check for leap year.
    if ( date.Month > 2 &&
        (( date.Year % 100 != 0 || date.Year % 400 == 0 ) &&
        date.Year % 4 == 0 ))
        dateOfYear++;

    // Add in year.
    dateOfYear *= 10000;
    dateOfYear += date.Year;

    return dateOfYear;
}

int main()
{
    Date date{ 8, 27, 2018 };
    long dateOfYear = DateOfYear(date);
    std::cout << dateOfYear << std::endl;
}
```

Poprzedni kod pokazuje dostępne elementy członkowskie struktury przekazywany przez odwołanie za pomocą operatora wyboru składowej (**.**) zamiast operatora wyboru elementu członkowskiego wskaźnika (**->**).

Mimo że argumenty przekazane jako typy odwołań, Sprawdź składnię typów nie będącego wskaźnikiem, zachowują jedną z ważnych cech typów wskaźnika: są one można modyfikować, chyba że zadeklarowany jako **const**. Ponieważ celem poprzedni kod nie może modyfikować dany obiekt `date`, jest bardziej odpowiednia prototypu funkcji:

```cpp
long DateOfYear( const Date& date );
```

Prototyp to gwarantuje, że funkcja `DateOfYear` nie zmieni się z jej argument.

Dowolnej funkcji prototypowej jako biorąc typu odwołania może zaakceptować obiekt tego samego typu, w tym miejscu, ponieważ nie istnieje konwersja standardowa ze *typename* do *typename* <strong>&</strong>.

## <a name="see-also"></a>Zobacz także

[Odwołania](../cpp/references-cpp.md)<br/>
