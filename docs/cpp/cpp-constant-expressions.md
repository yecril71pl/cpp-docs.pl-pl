---
title: Wyrażenia stałe języka C++
ms.date: 11/04/2016
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: b07245a5-4c21-4589-b503-e6ffd631996f
ms.openlocfilehash: 97059066adadc3a7897cbd2c4c747e2a673e7201
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154675"
---
# <a name="c-constant-expressions"></a>Wyrażenia stałe języka C++

A *stałej* wartość to taki, który nie powoduje zmiany. C++ zawiera dwa słowa kluczowe umożliwiające express celem obiektu nie jest przeznaczony do modyfikacji i wymusić tym przeznaczeniem.

C++ wymaga wyrażenia stałe — wyrażeń, które oszacowane jako stała — dla deklaracji:

- Granice tablicy

- Selektory w instrukcji case

- Specyfikacja długości pole bitowe

- Inicjatory wyliczenia

Tylko argumentów operacji, które są dopuszczalne w wyrażenia stałe są następujące:

- Literały

- Stałe wyliczeń

- Jako const zadeklarowane jako wartości, które są inicjowane przy użyciu wyrażeń stałych

- **Operator sizeof** wyrażeń

Stałe nonintegral muszą zostać przekonwertowane (jawnie lub niejawnie) typów całkowitych pod kątem w wyrażeniu stałym. W związku z tym poniższy kod jest dozwolony:

```cpp
const double Size = 11.0;
char chArray[(int)Size];
```

Jawne konwersje typów całkowitych są niedozwolone w wyrażeniach stałych innych typów i typów pochodnych są niedozwolone z wyjątkiem sytuacji, gdy używana jako argumenty do **sizeof** operatora.

Nie można użyć operatora przecinka i operatory przypisania w wyrażeniach stałych.

## <a name="see-also"></a>Zobacz także

[Typy wyrażeń](../cpp/types-of-expressions.md)