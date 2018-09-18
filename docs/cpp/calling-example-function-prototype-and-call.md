---
title: 'Przykład wywołania: Prototyp funkcji i wywołanie | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 04e681560854be4c93b1c93786d38771c07244ea
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099580"
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