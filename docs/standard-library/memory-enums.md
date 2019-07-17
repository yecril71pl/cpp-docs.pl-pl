---
title: '&lt;Pamięć&gt; Typy wyliczeniowe'
ms.date: 11/04/2016
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
ms.openlocfilehash: b2f5b50dc1344b95e88742d346e32fc55f821336
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243845"
---
# <a name="ltmemorygt-enums"></a>&lt;Pamięć&gt; Typy wyliczeniowe

## <a name="pointer_safety"></a> pointer_safety — wyliczenie

Wyliczenia możliwych wartości zwracanych przez `get_pointer_safety`.

```
class pointer_safety {
   relaxed,
   preferred,
   strict
};
```

### <a name="remarks"></a>Uwagi

O określonym zakresie **wyliczenia** definiuje wartości, które mogą być zwrócone przez `get_pointer_safety()`:

`relaxed` --traktowania wskaźników nie bezpiecznie pochodnych (oczywiście wskaźników do obiektów zadeklarowanych lub przydzielonego) takie same jak te bezpiecznie pochodnych.

`preferred` — tak jak poprzednio, ale wskaźniki nie bezpiecznie pochodnej nie powinny zostać wyłuskany.

`strict` --Wskaźniki nie bezpiecznie pochodne może być traktowane inaczej niż te bezpiecznie pochodnych.
