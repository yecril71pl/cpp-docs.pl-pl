---
title: Przeciążanie &lt; &lt; operatora dla własnych klas | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- operator<<, overloading for your own classes
- operator <<, overloading for your own classes
ms.assetid: ad1d2c49-d84e-48a8-9c09-121f28b10bf0
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6ef542a20284d0b69d44f1092a1f311a16b999a4
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
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
