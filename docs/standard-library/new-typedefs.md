---
title: '&lt;nowe&gt; definicje typów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: bbfe7d2c24cb589925c70c70235f6de112d274f1
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2018
ms.locfileid: "42464989"
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
