---
title: Konwersje wywołania funkcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function calls, converting
- function calls, argument type conversions
- functions [C], argument conversions
ms.assetid: 04ea0f81-509a-4913-8b12-0937a81babcf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3a1a245511f0ab849c28ab9a03ba76903609643
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065663"
---
# <a name="function-call-conversions"></a>Konwersje wywołania funkcji

Typ konwersji wykonywane względem argumentów w wywołaniu funkcji zależy od obecności prototypu funkcji (deklaracja) z typami argumentów zadeklarowane dla wywołanej funkcji.

Jeśli prototyp funkcji jest obecny i zawiera typy argumentów zadeklarowane, kompilator wykonuje sprawdzanie typu (zobacz [funkcje](../c-language/functions-c.md)).

Jeśli nie prototypu funkcji jest obecny, tylko zwykle konwersje arytmetyczne są wykonywane na argumentów w wywołaniu funkcji. Te konwersje są wykonywane niezależnie dla każdego argumentu w wywołaniu. Oznacza to, że **float** wartość jest konwertowana na **double**; `char` lub **krótki** wartość jest konwertowana na `int`; i `unsigned char` lub **typ unsigned short** jest konwertowana na `unsigned int`.

## <a name="see-also"></a>Zobacz też

[Konwersje typów](../c-language/type-conversions-c.md)