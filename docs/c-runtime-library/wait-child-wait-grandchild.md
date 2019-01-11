---
title: _WAIT_CHILD, _WAIT_GRANDCHILD
ms.date: 11/04/2016
f1_keywords:
- _WAIT_GRANDCHILD
- WAIT_CHILD
- WAIT_GRANDCHILD
- _WAIT_CHILD
helpviewer_keywords:
- WAIT_CHILD constant
- WAIT_GRANDCHILD constant
- _WAIT_CHILD constant
- _WAIT_GRANDCHILD constant
ms.assetid: 7acd96fa-d118-4339-bb00-e5afaf286945
ms.openlocfilehash: b484f068ce94ab7a2a637723641e1206072cf24b
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220273"
---
# <a name="waitchild-waitgrandchild"></a>_WAIT_CHILD, _WAIT_GRANDCHILD

## <a name="syntax"></a>Składnia

```
#include <process.h>
```

## <a name="remarks"></a>Uwagi

`_cwait` Funkcja może służyć przez żaden proces będzie poczekać jakiś inny proces (jeśli jest znany identyfikator procesu). Argument akcji może być jednym z następujących wartości:

|Stała|Znaczenie|
|--------------|-------------|
|`_WAIT_CHILD`|Proces wywoływania czeka, aż kończy się określonym nowego procesu.|
|`_WAIT_GRANDCHILD`|Wywołanie procesu w tym czasie czeka, aż do określonej nowy proces i wszystkie procesy utworzone przez ten nowy proces, Zakończ.|

## <a name="see-also"></a>Zobacz też

[_cwait](../c-runtime-library/reference/cwait.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)
