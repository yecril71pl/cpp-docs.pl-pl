---
title: Przeciążanie &lt; &lt; operatora dla własnych klas | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- operator<<, overloading for your own classes
- operator <<, overloading for your own classes
ms.assetid: ad1d2c49-d84e-48a8-9c09-121f28b10bf0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5f5129be6ebf7cac336373f00c7f9e989c23489
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="overloading-the-ltlt-operator-for-your-own-classes"></a>Przeciążanie &lt; &lt; operatora dla własnych klas

Strumienie wyjściowe użyć wstawiania (`<<`) operatora dla standardowych typów. Można także przeciążać `<<` operatora dla własnych klas.

## <a name="example"></a>Przykład

`write` Funkcja przykładzie pokazano użycie `Date` struktury. Data jest idealny kandydatem do klasy C++, w którym elementy członkowskie danych (miesiąc, dzień i rok) są ukrywane. Strumień wyjściowy jest wyświetlanie takie struktury logicznej miejsca docelowego. Ten kod wyświetla data using `cout` obiektu:

```cpp
Date dt(1, 2, 92);

cout <<dt;
```

Aby uzyskać `cout` do akceptowania `Date` obiektu po operatorze wstawiania, przeciążenia operatora wstawiania, aby rozpoznać `ostream` obiektu po lewej stronie i `Date` po prawej stronie. Przeciążone `<<` funkcji operatora następnie musi być zadeklarowany jako przyjaciel klasy `Date` , można uzyskać dostępu do danych prywatnych w `Date` obiektu.

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

Przeciążony operator zwraca odwołanie do oryginalnej `ostream` obiektu, co oznacza, że można łączyć wstawienia:

```cpp
cout <<"The date is" <<dt <<flush;
```

## <a name="see-also"></a>Zobacz także

[Strumienie wyjściowe](../standard-library/output-streams.md)<br/>
