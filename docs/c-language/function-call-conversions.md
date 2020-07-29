---
title: Konwersje wywołania funkcji
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, converting
- function calls, argument type conversions
- functions [C], argument conversions
ms.assetid: 04ea0f81-509a-4913-8b12-0937a81babcf
ms.openlocfilehash: e4e84c9d4e1f25a56c0bcabcec99e5e75fcaa321
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229678"
---
# <a name="function-call-conversions"></a>Konwersje wywołania funkcji

Typ konwersji wykonywanej na argumentach wywołania funkcji zależy od obecności prototypu funkcji (deklaracji do przodu) z zadeklarowanymi typami argumentów dla wywołanej funkcji.

Jeśli prototyp funkcji jest obecny i zawiera zadeklarowane typy argumentów, kompilator wykonuje sprawdzanie typu (zobacz [funkcje](../c-language/functions-c.md)).

Jeśli nie ma prototypu funkcji, tylko standardowe konwersje arytmetyczne są wykonywane na argumentach wywołania funkcji. Te konwersje są wykonywane niezależnie od każdego argumentu w wywołaniu. Oznacza to, że **`float`** wartość jest konwertowana na **`double`** ; a **`char`** lub **`short`** wartość jest konwertowana na **`int`** ; i **`unsigned char`** lub **`unsigned short`** jest konwertowana na **`unsigned int`** .

## <a name="see-also"></a>Zobacz także

[Konwersje typów](../c-language/type-conversions-c.md)
