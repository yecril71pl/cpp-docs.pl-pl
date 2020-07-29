---
title: Wyrażenia stałe języka C++
ms.date: 11/04/2016
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: b07245a5-4c21-4589-b503-e6ffd631996f
ms.openlocfilehash: 32d14650450d8047a5bc0e6cf7bb06788c9b3d81
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221760"
---
# <a name="c-constant-expressions"></a>Wyrażenia stałe języka C++

*Stała* wartość to taka, która nie zmienia się. Język C++ zawiera dwa słowa kluczowe, które umożliwiają wyrażenie zamiaru, że obiekt nie jest przeznaczony do modyfikacji i wymuszenie tego celu.

C++ wymaga wyrażeń stałych — wyrażenia, których wynikiem jest stała — dla deklaracji:

- Granice tablicy

- Selektory w instrukcjach Case

- Specyfikacja długości pola bitowego

- Inicjatory wyliczenia

Jedyne operandy, które są dozwolone w wyrażeniach stałych, to:

- Literały

- Stałe wyliczające

- Wartości zadeklarowane jako const, które są inicjowane za pomocą wyrażeń stałych

- **`sizeof`** wyrażeń

Stałe niecałkowite muszą zostać przekonwertowane (jawnie lub niejawnie) do typów całkowitych, aby były dozwolone w wyrażeniu stałym. W związku z tym Poniższy kod jest dozwolony:

```cpp
const double Size = 11.0;
char chArray[(int)Size];
```

Jawne konwersje typów całkowitych są dozwolone w wyrażeniach stałych; wszystkie inne typy i typy pochodne są niedozwolone, chyba że są używane jako operandy **`sizeof`** operatora.

Operatorów przecinek i operator przypisania nie można używać w wyrażeniach stałych.

## <a name="see-also"></a>Zobacz także

[Typy wyrażeń](../cpp/types-of-expressions.md)
