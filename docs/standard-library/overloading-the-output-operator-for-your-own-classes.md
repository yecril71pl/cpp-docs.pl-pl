---
title: Przeciążanie &lt; &lt; Operator dla własnych klas
ms.date: 11/04/2016
helpviewer_keywords:
- operator<<, overloading for your own classes
- operator <<, overloading for your own classes
ms.assetid: ad1d2c49-d84e-48a8-9c09-121f28b10bf0
ms.openlocfilehash: 290491f7afb22873d60abb6662b470d8e7abefc1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370687"
---
# <a name="overloading-the-ltlt-operator-for-your-own-classes"></a>Przeciążanie &lt; &lt; Operator dla własnych klas

Strumienie wyjściowe użyć wstawiania (`<<`) operator dla standardowych typów. Możesz także przeciążać `<<` operator dla własnych klas.

## <a name="example"></a>Przykład

`write` Funkcja przykładzie pokazano użycie `Date` struktury. Data jest idealnym rozwiązaniem Release candidate dla klasy języka C++, w której elementy członkowskie danych (miesiąc, dzień i rok) są ukryte w widoku. Strumień wyjściowy jest logiczne miejsce docelowe do wyświetlania takiej struktury. Ten kod wyświetla datę przy użyciu `cout` obiektu:

```cpp
Date dt(1, 2, 92);

cout <<dt;
```

Aby uzyskać `cout` do akceptowania `Date` obiektu po operatorze wstawiania, przeciążanie operatora wstawiania, rozpoznawał `ostream` obiektu po lewej stronie i `Date` po prawej stronie. Przeciążone `<<` funkcji operatora następnie musi być zadeklarowana jako zaprzyjaźniona klasy `Date` aby mogą uzyskiwać dostęp do prywatnych danych w ramach `Date` obiektu.

```cpp
// overload_date.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

class Date
{
    int mo, da, yr;
public:
    Date(int m, int d, int y)
    {
        mo = m; da = d; yr = y;
    }
    friend ostream& operator<<(ostream& os, const Date& dt);
};

ostream& operator<<(ostream& os, const Date& dt)
{
    os << dt.mo << '/' << dt.da << '/' << dt.yr;
    return os;
}

int main()
{
    Date dt(5, 6, 92);
    cout << dt;
}
```

```Output
5/6/92
```

## <a name="remarks"></a>Uwagi

Przeciążony operator zwraca odwołanie do oryginalnego `ostream` obiektu, co oznacza, że można łączyć wstawienia:

```cpp
cout <<"The date is" <<dt <<flush;
```

## <a name="see-also"></a>Zobacz także

[Strumienie wyjściowe](../standard-library/output-streams.md)<br/>
