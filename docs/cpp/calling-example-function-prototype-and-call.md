---
title: 'Przykład wywołania: prototyp funkcji i wywołanie'
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
ms.openlocfilehash: f89f4f1917810baa585dd1661428e0809b93cca0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508189"
---
# <a name="calling-example-function-prototype-and-call"></a>Przykład wywołania: prototyp funkcji i wywołanie

## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft

Poniższy przykład pokazuje wyniki wywołania funkcji, za pomocą różnych konwencji wywoływania.

Ten przykład jest oparty na następujący szkielet funkcji. Zastąp `calltype` przy użyciu odpowiednich konwencji wywoływania.

```
void    calltype MyFunc( char c, short s, int i, double f );
.
.
.
void    MyFunc( char c, short s, int i, double f )
    {
    .
    .
    .
    }
.
.
.
MyFunc ('x', 12, 8192, 2.7183);
```

Aby uzyskać więcej informacji, zobacz [wyniki podczas wywoływania przykład](../cpp/results-of-calling-example.md).

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Konwencje wywoływania](../cpp/calling-conventions.md)