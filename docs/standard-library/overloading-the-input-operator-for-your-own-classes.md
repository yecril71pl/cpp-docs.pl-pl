---
title: Przeciążanie &gt; &gt; operatora dla własnych klas | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- operator>>
- operator>>, overloading for your own classes
- operator >>, overloading for your own classes
ms.assetid: 40dab4e0-3f97-4745-9cc8-b86e740fa246
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d98372009090b0241d9f0190a1d53a9416bbd7ba
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="overloading-the-gtgt-operator-for-your-own-classes"></a>Przeciążanie &gt; &gt; operatora dla własnych klas

Strumienie wejściowe Użyj wyodrębniania (`>>`) operatora dla standardowych typów. Podobny operatory wyodrębniania może zapisywać do własnych typów; Twój sukces zależy od tego, dokładnie przy użyciu biały znak.

Oto przykład operator wyodrębniania `Date` klasy przedstawione wcześniej:

```cpp
istream& operator>> (istream& is, Date& dt)
{
    is>> dt.mo>> dt.da>> dt.yr;
    return is;
}
```

## <a name="see-also"></a>Zobacz także

[Strumienie wejściowe](../standard-library/input-streams.md)<br/>
