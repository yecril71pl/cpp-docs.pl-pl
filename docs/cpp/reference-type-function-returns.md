---
title: Zwracanie funkcji typu odwołania
ms.date: 11/04/2016
helpviewer_keywords:
- function return types [C++], reference type
- data types [C++], function return types
- functions [C++], return types
ms.assetid: 5b73be1d-2dc7-41df-ab0a-adcba36f2ad1
ms.openlocfilehash: 5e84643713dcbcb278fe7ce07c5d55f3593ec2ef
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188301"
---
# <a name="reference-type-function-returns"></a>Zwracanie funkcji typu odwołania

Funkcje mogą być deklarowane jako zwracające typ referencyjny. Istnieją dwie przyczyny takiego zgłoszenia:

- Zwracane informacje są wystarczającą liczbą obiektów, które zwracają odwołanie, są bardziej wydajne niż zwracające kopię.

- Typ funkcji musi być l-wartością.

- Obiekt, do którego się odwołuje, nie będzie wykraczał poza zakres, gdy funkcja zwróci wartość.

Tak samo jak w przypadku przekazywania dużych obiektów *do* funkcji przez odwołanie może być bardziej wydajne, aby zwrócić duże obiekty *z* funkcji przez odwołanie. Odwołanie — protokół powrotu eliminuje konieczność kopiowania obiektu do tymczasowej lokalizacji przed zwróceniem.

Typy zwracające odwołanie mogą być również przydatne, gdy funkcja musi oszacować wartość l. Większość przeciążonych operatorów należy do tej kategorii, w szczególności operatora przypisania. Przeciążone operatory są objęte [przeciążonymi operatorami](../cpp/operator-overloading.md).

## <a name="example"></a>Przykład

Rozważmy przykład `Point`:

```cpp
// refType_function_returns.cpp
// compile with: /EHsc

#include <iostream>
using namespace std;

class Point
{
public:
// Define "accessor" functions as
//  reference types.
unsigned& x();
unsigned& y();
private:
// Note that these are declared at class scope:
unsigned obj_x;
unsigned obj_y;
};

unsigned& Point :: x()
{
return obj_x;
}
unsigned& Point :: y()
{
return obj_y;
}

int main()
{
Point ThePoint;
// Use x() and y() as l-values.
ThePoint.x() = 7;
ThePoint.y() = 9;

// Use x() and y() as r-values.
cout << "x = " << ThePoint.x() << "\n"
<< "y = " << ThePoint.y() << "\n";
}
```

## <a name="output"></a>Dane wyjściowe

```Output
x = 7
y = 9
```

Zwróć uwagę, że funkcje `x` i `y` są zadeklarowane jako zwracające typy odwołań. Te funkcje mogą być używane po obu stronach instrukcji przypisania.

Zwróć uwagę na to, że w głównym obiekcie ThePoint pozostaje w zakresie, a w związku z tym jego członkowie odniesienia nadal są obsługiwani i mogą być bezpiecznie dostępne.

Deklaracje typów referencyjnych muszą zawierać inicjatory, z wyjątkiem następujących przypadków:

- Jawna deklaracja **extern**

- Deklaracja składowej klasy

- Deklaracja w obrębie klasy

- Deklaracja argumentu do funkcji lub zwracanego typu dla funkcji

## <a name="caution-returning-address-of-local"></a>Przestroga zwracająca adres lokalny

Jeśli obiekt jest zadeklarowany w zakresie lokalnym, ten obiekt zostanie zniszczony, gdy funkcja zwróci wartość. Jeśli funkcja zwraca odwołanie do tego obiektu, odwołanie to prawdopodobnie spowoduje naruszenie zasad dostępu w czasie wykonywania, jeśli obiekt wywołujący próbuje użyć odwołania o wartości null.

```cpp
// C4172 means Don’t do this!!!
Foo& GetFoo()
{
    Foo f;
    ...
    return f;
} // f is destroyed here
```

Kompilator generuje ostrzeżenie w tym przypadku: `warning C4172: returning address of local variable or temporary`. W przypadku prostych programów możliwe jest, że czasami nie zostanie naruszone naruszenie dostępu, jeśli odwołanie jest dostępne przez wywołującego przed zastąpieniem lokalizacji pamięci. Jest to spowodowane zawiera szczęściem. Zwróć ostrzeżenie.

## <a name="see-also"></a>Zobacz też

[Odwołania](../cpp/references-cpp.md)
