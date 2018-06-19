---
title: '&lt;nowe&gt; definicje typów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: 5ab0087a85cb2fce6fa300db136e7c60c66b0b5c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33852194"
---
# <a name="ltnewgt-typedefs"></a>&lt;nowe&gt; definicje typów

||
|-|
|[new_handler](#new_handler)|

## <a name="new_handler"></a>  new_handler

Użyj punktów typu odpowiednie dla funkcji jako nowy program obsługi.

```cpp
typedef void (*new_handler)();
```

### <a name="remarks"></a>Uwagi

Ten typ funkcji obsługi jest wywoływana przez **operatornew** lub `operator new[]` po nie może spełnić żądania dodatkowego miejsca do magazynowania.

### <a name="example"></a>Przykład

Zobacz [set_new_handler —](../standard-library/new-functions.md#set_new_handler) na przykład za pomocą `new_handler` jako do wartości zwracanej.

## <a name="see-also"></a>Zobacz także

[\<new>](../standard-library/new.md)<br/>
