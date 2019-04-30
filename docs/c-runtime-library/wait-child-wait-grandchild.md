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
ms.openlocfilehash: 98858058add6a0a11d4f9331989c6816e38130aa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377831"
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

## <a name="see-also"></a>Zobacz także

[_cwait](../c-runtime-library/reference/cwait.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)
