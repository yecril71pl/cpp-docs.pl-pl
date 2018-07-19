---
title: '&lt;Pamięć&gt; wyliczenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
ms.openlocfilehash: 9b9ea485bb66292c3c0509036c22dd161a694dd3
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961425"
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
