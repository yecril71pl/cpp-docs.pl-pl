---
title: Przeciążanie &lt; &lt; operatora dla własnych klas
ms.date: 11/04/2016
helpviewer_keywords:
- operator<<, overloading for your own classes
- operator <<, overloading for your own classes
ms.assetid: ad1d2c49-d84e-48a8-9c09-121f28b10bf0
ms.openlocfilehash: c470bb7335a5997ae26327f99b8c5f31d20b4edb
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452050"
---
# <a name="overloading-the-ltlt-operator-for-your-own-classes"></a>Przeciążanie &lt; &lt; operatora dla własnych klas

Strumienie wyjściowe używają operatora wstawiania`<<`() dla typów standardowych. Można również przeciążyć `<<` operatora dla własnych klas.

## <a name="example"></a>Przykład

W `write` przykładzie funkcji pokazano użycie `Date` struktury. Data jest idealnym kandydatem dla C++ klasy, w której elementy członkowskie danych (miesiąc, dzień i rok) są ukryte przed wyświetleniem. Strumień wyjściowy jest logicznym miejscem docelowym do wyświetlania takiej struktury. Ten kod wyświetla datę przy użyciu `cout` obiektu:

```cpp
Date dt(1, 2, 92);

cout <<dt;
```

Aby zaakceptować obiekt po operatorze wstawiania, `ostream` przeciążać operator wstawiania, aby rozpoznać obiekt po lewej stronie i `Date` po prawej stronie. `Date` `cout` Funkcja przeciążonego `<<` operatora musi być zadeklarowana jako zaprzyjaźniona Klasa `Date` , aby można było uzyskać dostęp do danych prywatnych w `Date` obiekcie.

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

[Strumienie wyjściowe](../standard-library/output-streams.md)
