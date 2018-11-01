---
title: Konwersje wywołania funkcji
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, converting
- function calls, argument type conversions
- functions [C], argument conversions
ms.assetid: 04ea0f81-509a-4913-8b12-0937a81babcf
ms.openlocfilehash: 9fdc9ef467980a079198ca06360766d84a85923f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441148"
---
# <a name="function-call-conversions"></a>Konwersje wywołania funkcji

Typ konwersji wykonywane względem argumentów w wywołaniu funkcji zależy od obecności prototypu funkcji (deklaracja) z typami argumentów zadeklarowane dla wywołanej funkcji.

Jeśli prototyp funkcji jest obecny i zawiera typy argumentów zadeklarowane, kompilator wykonuje sprawdzanie typu (zobacz [funkcje](../c-language/functions-c.md)).

Jeśli nie prototypu funkcji jest obecny, tylko zwykle konwersje arytmetyczne są wykonywane na argumentów w wywołaniu funkcji. Te konwersje są wykonywane niezależnie dla każdego argumentu w wywołaniu. Oznacza to, że **float** wartość jest konwertowana na **double**; `char` lub **krótki** wartość jest konwertowana na `int`; i `unsigned char` lub **typ unsigned short** jest konwertowana na `unsigned int`.

## <a name="see-also"></a>Zobacz też

[Konwersje typów](../c-language/type-conversions-c.md)