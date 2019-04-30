---
title: '&lt;Pamięć&gt; Typy wyliczeniowe'
ms.date: 11/04/2016
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
ms.openlocfilehash: 5c5f87905b772ef277a72ef11defef8cb1001661
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412842"
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
