---
title: Dostęp do elementu członkowskiego
ms.date: 11/04/2016
helpviewer_keywords:
- member-selection operators [C++]
- pointers, smart
- member access, overloaded operators
- operator overloading [C++], member access operators
- smart pointers, definition
- smart pointers
ms.assetid: 8c7b2c43-eb92-4d42-9a8e-61aa37d71333
ms.openlocfilehash: 34527f818b135fd5af629ebb69feaffd03b715fc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50617301"
---
# <a name="member-access"></a>Dostęp do elementu członkowskiego

Dostęp do składowej klasy mogą być kontrolowane przez przeciążania operatora dostępu do elementu członkowskiego (**->**). Ten operator jest uznawany za operatora jednoargumentowego to wykorzystania, a funkcja przeciążonego operatora musi być funkcją składową klasy. Dlatego jest deklaracji pod kątem takich funkcji:

## <a name="syntax"></a>Składnia

```
class-type *operator->()
```

## <a name="remarks"></a>Uwagi

gdzie *typu klasy* jest nazwą klasy, do której należy ten operator. Funkcja operatora dostępu do elementu członkowskiego musi być funkcją niestatycznej składowej.

Ten operator jest używany (często w połączeniu z operatorem wyłuskanie wskaźnika) do zaimplementowania "inteligentne wskaźniki", sprawdzające przed wskaźniki wyłuskania lub liczba użycia.

**.** Nie można przeciążyć operator dostępu do elementu członkowskiego.

## <a name="see-also"></a>Zobacz także

[Przeładowanie operatora](../cpp/operator-overloading.md)