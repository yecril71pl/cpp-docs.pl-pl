---
title: _WAIT_CHILD, _WAIT_GRANDCHILD | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _WAIT_GRANDCHILD
- WAIT_CHILD
- WAIT_GRANDCHILD
- _WAIT_CHILD
dev_langs:
- C++
helpviewer_keywords:
- WAIT_CHILD constant
- WAIT_GRANDCHILD constant
- _WAIT_CHILD constant
- _WAIT_GRANDCHILD constant
ms.assetid: 7acd96fa-d118-4339-bb00-e5afaf286945
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7dd7b3fab51c382413c507831572afedd824c3f7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018343"
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