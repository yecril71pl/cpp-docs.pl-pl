---
title: '&lt;&gt;wyliczenia pamięci'
ms.date: 11/04/2016
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
ms.openlocfilehash: 507628628fcf8bbf8993ce5beb1e02c28ff82147
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222254"
---
# <a name="ltmemorygt-enums"></a>&lt;&gt;wyliczenia pamięci

## <a name="pointer_safety-enumeration"></a><a name="pointer_safety"></a>pointer_safety, Wyliczenie

Wyliczenie możliwych wartości zwracanych przez `get_pointer_safety` .

```cpp
class pointer_safety {
   relaxed,
   preferred,
   strict
};
```

### <a name="remarks"></a>Uwagi

Zakres **`enum`** definiuje wartości, które mogą być zwracane przez `get_pointer_safety()` :

`relaxed`--wskaźniki nie są bezpiecznie wyprowadzane (oczywiście wskaźniki do zadeklarowanych lub przyznanych obiektów) są traktowane jak te, które bezpiecznie pochodzą.

`preferred`--tak jak wcześniej, ale wskaźniki, które nie są bezpiecznie wyprowadzane, nie należy wywoływać.

`strict`— wskaźniki, które nie są bezpiecznie wyprowadzane, mogą być traktowane inaczej niż te, które są bezpiecznie wyprowadzane.
