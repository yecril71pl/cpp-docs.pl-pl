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
ms.openlocfilehash: 5a409efbe2908954d394656cb989ad6b80a9ce22
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233642"
---
# <a name="reference-type-function-arguments"></a>Argumenty funkcji typu odwołania

Często bardziej wydajne jest przekazanie odwołań, a nie dużych obiektów, do funkcji. Dzięki temu kompilator może przekazać adres obiektu przy zachowaniu składni, która mogłaby zostać użyta w celu uzyskania dostępu do obiektu. Rozważmy następujący przykład, który używa `Date` struktury:

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

Poprzedni kod pokazuje, że elementy członkowskie struktury przekazana przez odwołanie są dostępne przy użyciu operatora wyboru elementu członkowskiego (**.**) zamiast operatora wyboru elementu członkowskiego wskaźnika ( **->** ).

Chociaż argumenty przekazane jako typy referencyjne obserwują składnię typów niebędących wskaźnikami, zachowują jedną ważną cechę typów wskaźnika: można je modyfikować, chyba że zostanie zadeklarowany jako **`const`** . Ponieważ przeznaczenie powyższego kodu nie powoduje modyfikacji obiektu `date` , bardziej odpowiedni prototyp funkcji to:

```cpp
long DateOfYear( const Date& date );
```

Ten prototyp gwarantuje, że funkcja `DateOfYear` nie zmieni jej argumentu.

Każda funkcja zaprototypowa jako pobierająca typ referencyjny może zaakceptować obiekt tego samego typu w jego miejscu, ponieważ istnieje konwersja standardowa z *TypeName* do *TypeName* <strong>&</strong> .

## <a name="see-also"></a>Zobacz także

[Dokumentacja](../cpp/references-cpp.md)<br/>
