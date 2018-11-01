---
title: '&lt;Pamięć&gt; Typy wyliczeniowe'
ms.date: 11/04/2016
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
ms.openlocfilehash: 5c5f87905b772ef277a72ef11defef8cb1001661
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495007"
---
# <a name="ltmemorygt-enums"></a>&lt;Pamięć&gt; Typy wyliczeniowe

||
|-|
|[pointer_safety](#pointer_safety)|

## <a name="pointer_safety"></a>  pointer_safety — wyliczenie

Wyliczenia możliwych wartości zwracanych przez `get_pointer_safety`.

pointer_safety klasy — {swobodna, preferowany strict};

### <a name="remarks"></a>Uwagi

O określonym zakresie **wyliczenia** definiuje wartości, które mogą być zwrócone przez `get_pointer_safety()`:

`relaxed` --traktowania wskaźników nie bezpiecznie pochodnych (oczywiście wskaźników do obiektów zadeklarowanych lub przydzielonego) takie same jak te bezpiecznie pochodnych.

`preferred` — tak jak poprzednio, ale wskaźniki nie bezpiecznie pochodnej nie powinny zostać wyłuskany.

`strict` --Wskaźniki nie bezpiecznie pochodne może być traktowane inaczej niż te bezpiecznie pochodnych.

## <a name="see-also"></a>Zobacz także

[\<memory>](../standard-library/memory.md)<br/>
