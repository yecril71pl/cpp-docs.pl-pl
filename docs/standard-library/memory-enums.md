---
title: '&lt;Pamięć&gt; wyliczenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
ms.openlocfilehash: 4d33cf941341f26c88f3a73c5a3d9ac0326db545
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="ltmemorygt-enums"></a>&lt;Pamięć&gt; wyliczenia

||
|-|
|[pointer_safety](#pointer_safety)|

## <a name="pointer_safety"></a>  pointer_safety — wyliczenie

Wyliczenia możliwych wartości zwracanych przez `get_pointer_safety`.

pointer_safety — klasa, {swobodna, preferowane, ograniczeniami};

### <a name="remarks"></a>Uwagi

Zakresie `enum` definiuje wartości, które mogą być zwrócone przez `get_pointer_safety()`:

`relaxed` --Wskaźniki nie bezpiecznie pochodnych (oczywiście wskaźników do obiektów zadeklarowane lub przydzielonego) są traktowane taki sam, jak te bezpiecznie pochodnych.

`preferred` --jak poprzednio, ale nie bezpiecznie pochodnych wskaźniki nie powinny wyłuskiwany.

`strict` --Wskaźniki nie bezpiecznie pochodnych może być traktowane inaczej niż te bezpiecznie pochodnych.

## <a name="see-also"></a>Zobacz także

[\<memory>](../standard-library/memory.md)<br/>
