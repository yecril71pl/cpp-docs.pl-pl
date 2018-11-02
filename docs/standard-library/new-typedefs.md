---
title: '&lt;nowe&gt; definicje typów'
ms.date: 11/04/2016
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: 85c8d0c2974f734783e3d9c2ad1269f84d605dec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549126"
---
# <a name="ltnewgt-typedefs"></a>&lt;nowe&gt; definicje typów

| |
| - |
|[new_handler](#new_handler)|

## <a name="new_handler"></a>  new_handler

Punkty typu do funkcji odpowiedni do użycia jako nowy program obsługi.

```cpp
typedef void (*new_handler)();
```

### <a name="remarks"></a>Uwagi

Tego rodzaju funkcji obsługi jest wywoływana przez **operatornew** lub `operator new[]` kiedy nie może spełnić żądania dodatkowego miejsca do magazynowania.

### <a name="example"></a>Przykład

Zobacz [set_new_handler](../standard-library/new-functions.md#set_new_handler) dla przykłady dotyczące używania `new_handler` jako wartości zwracanej.

## <a name="see-also"></a>Zobacz także

[\<new>](../standard-library/new.md)<br/>
