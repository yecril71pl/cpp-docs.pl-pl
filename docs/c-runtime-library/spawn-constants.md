---
title: spawn — stałe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _P_NOWAIT
- _P_OVERLAY
- _P_WAIT
- _P_DETACH
- _P_NOWAITO
dev_langs:
- C++
helpviewer_keywords:
- _P_OVERLAY constant
- P_DETACH constant
- P_OVERLAY constant
- P_NOWAIT constant
- _P_DETACH constant
- _P_NOWAIT constant
- _P_NOWAITO constant
- P_NOWAITO constant
- spawn constants
- P_WAIT constant
- _P_WAIT constant
ms.assetid: e0533e88-d362-46fc-b53c-5f193226d879
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8daaf38e60ca48b4a34deb2086bbd14eb45651e4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116935"
---
# <a name="spawn-constants"></a>spawn — Stałe

## <a name="syntax"></a>Składnia

```
#include <process.h>
```

## <a name="remarks"></a>Uwagi

`mode` Argument określa akcję podejmowaną przez proces wywołujący, przed, jak i podczas operacji wielokrotnego. Następujące wartości dla `mode` są możliwe:

|Stała|Znaczenie|
|--------------|-------------|
|`_P_OVERLAY`|Nakładki procesu przy użyciu nowego procesu wywołującego, niszczenie procesu wywołującego (efektu przez takie same jak `_exec` wywołania).|
|`_P_WAIT`|Wstrzymuje działanie wątku wywołującego do momentu wykonania nowego procesu (synchroniczne `_spawn`).|
|`_P_NOWAIT`, `_P_NOWAITO`|Kontynuuje wykonywanie procesu wywołującego wątkom nowego procesu (asynchroniczne `_spawn`).|
|`_P_DETACH`|Kontynuuje wykonywanie procesu wywołującego; nowy proces jest uruchamiany w tle bez dostępu do konsoli lub klawiatury. Wywołania `_cwait` względem nowy proces zakończy się niepowodzeniem. Jest to asynchronicznego `_spawn`.|

## <a name="see-also"></a>Zobacz też

[_spawn, _wspawn, funkcje](../c-runtime-library/spawn-wspawn-functions.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)