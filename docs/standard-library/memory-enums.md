---
title: '&lt;Pamięć&gt; wyliczenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
caps.latest.revision: 11
manager: ghogen
ms.openlocfilehash: 035175b2fea506fa341e260f042ae426e85421e4
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
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
