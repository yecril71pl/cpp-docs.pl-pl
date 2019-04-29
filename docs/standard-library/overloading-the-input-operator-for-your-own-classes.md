---
title: Przeciążanie &gt; &gt; Operator dla własnych klas
ms.date: 11/04/2016
helpviewer_keywords:
- operator>>
- operator>>, overloading for your own classes
- operator >>, overloading for your own classes
ms.assetid: 40dab4e0-3f97-4745-9cc8-b86e740fa246
ms.openlocfilehash: 86b8af963345c8eb9b3f44cfb16332bc09420bf3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370726"
---
# <a name="overloading-the-gtgt-operator-for-your-own-classes"></a>Przeciążanie &gt; &gt; Operator dla własnych klas

Strumienie wejściowe Użyj wyodrębniania (`>>`) operator dla standardowych typów. Można napisać podobne operatorów wyodrębniania dla własnych typów; Twój sukces zależy od tego, dokładnie przy użyciu biały znak.

Oto przykład operator wyodrębniania `Date` klasy przedstawiony wcześniej:

```cpp
istream& operator>> (istream& is, Date& dt)
{
    is>> dt.mo>> dt.da>> dt.yr;
    return is;
}
```

## <a name="see-also"></a>Zobacz także

[Strumienie wejściowe](../standard-library/input-streams.md)<br/>
