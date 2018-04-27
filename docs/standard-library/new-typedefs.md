---
title: '&lt;nowe&gt; definicje typów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
caps.latest.revision: 7
manager: ghogen
ms.openlocfilehash: 53a13168986171d3240cc15e405fc08b3db07e96
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
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
