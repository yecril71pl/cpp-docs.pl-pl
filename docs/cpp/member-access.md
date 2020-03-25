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
ms.openlocfilehash: 12ea612625e21a8a13021b75e92f3752b0b5ce80
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179422"
---
# <a name="member-access"></a>Dostęp do elementu członkowskiego

Dostęp do elementu członkowskiego klasy może być kontrolowany przez przeładowanie operatora dostępu do elementu członkowskiego ( **->** ). Ten operator jest traktowany jako operator jednoargumentowy w tym użyciu, a funkcja przeciążonego operatora musi być funkcją składową klasy. W związku z tym Deklaracja dla takiej funkcji jest:

## <a name="syntax"></a>Składnia

```
class-type *operator->()
```

## <a name="remarks"></a>Uwagi

gdzie *Class-Type* jest nazwą klasy, do której należy ten operator. Funkcja operatora dostępu do elementu członkowskiego musi być niestatyczną funkcją składową.

Ten operator jest używany (często w połączeniu z operatorem odwołującym wskaźnik) do implementowania "inteligentnych wskaźników", które weryfikują wskaźniki przed wymienieniem lub licznikiem użycia.

**.** operator dostępu do składowych nie może być przeciążony.

## <a name="see-also"></a>Zobacz też

[Przeładowanie operatora](../cpp/operator-overloading.md)
