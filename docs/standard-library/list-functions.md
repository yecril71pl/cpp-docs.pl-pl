---
title: '&lt;listy funkcji&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- list/std::swap
ms.openlocfilehash: 04f00a9274018432cd03917ae5485f2d395649e4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78874441"
---
# <a name="ltlistgt-functions"></a>funkcje&gt; listy &lt;

## <a name="swap"></a>wymiany

Wymienia elementy dwóch list.

```cpp
template <class T, class Allocator>
    void swap(list<T, Allocator>& left, list<T, Allocator>& right)
```

### <a name="parameters"></a>Parametry

\ *lewo*
Obiekt typu `list`.

*prawa*\
Obiekt typu `list`.

### <a name="remarks"></a>Uwagi

Ta funkcja szablonu wykonuje `left.swap(right)`.
