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
ms.openlocfilehash: 714b4e79f1c229817a12908aad0d726f74023036
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524394"
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