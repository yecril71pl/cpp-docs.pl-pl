---
title: Konwersje wywołania funkcji
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, converting
- function calls, argument type conversions
- functions [C], argument conversions
ms.assetid: 04ea0f81-509a-4913-8b12-0937a81babcf
ms.openlocfilehash: d9f205bbbbac353b57743f8e1211b20fa3d32f05
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233226"
---
# <a name="function-call-conversions"></a>Konwersje wywołania funkcji

Typ konwersji wykonywanej na argumentach wywołania funkcji zależy od obecności prototypu funkcji (deklaracji do przodu) z zadeklarowanymi typami argumentów dla wywołanej funkcji.

Jeśli prototyp funkcji jest obecny i zawiera zadeklarowane typy argumentów, kompilator wykonuje sprawdzanie typu (zobacz [funkcje](../c-language/functions-c.md)).

Jeśli nie ma prototypu funkcji, tylko standardowe konwersje arytmetyczne są wykonywane na argumentach wywołania funkcji. Te konwersje są wykonywane niezależnie od każdego argumentu w wywołaniu. Oznacza to, że wartość **zmiennoprzecinkowa** jest konwertowana na **podwójną**; wartość `char` a lub **krótka** jest konwertowana na `int`; a `unsigned char` lub **bez znaku Short** jest konwertowany na `unsigned int`.

## <a name="see-also"></a>Zobacz też

[Konwersje typu](../c-language/type-conversions-c.md)
