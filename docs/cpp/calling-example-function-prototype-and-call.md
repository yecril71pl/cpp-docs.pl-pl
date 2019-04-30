---
title: 'Przykład wywołania: Prototyp funkcji i wywołanie'
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
ms.openlocfilehash: f89f4f1917810baa585dd1661428e0809b93cca0
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345109"
---
# <a name="calling-example-function-prototype-and-call"></a>Przykład wywołania: Prototyp funkcji i wywołanie

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