---
title: '&lt;nowe&gt; definicje typów'
ms.date: 11/04/2016
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: 85c8d0c2974f734783e3d9c2ad1269f84d605dec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223639"
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
