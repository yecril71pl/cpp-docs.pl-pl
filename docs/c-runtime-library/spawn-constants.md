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
ms.openlocfilehash: f3a069f9f29f6fd15c3ce21111a37757519af229
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="spawn-constants"></a>spawn — Stałe
## <a name="syntax"></a>Składnia  
  
```  
#include <process.h>  
```  
  
## <a name="remarks"></a>Uwagi  
 `mode` Argument określa akcję wykonywaną przez proces wywoływania przed i wykonywania operacji na duplikowały. Następujące wartości `mode` są możliwe:  
  
|Stała|Znaczenie|  
|--------------|-------------|  
|`_P_OVERLAY`|Nakładki wywoływania procesu z nowego procesu, niszczenie procesu wywołującego (sam wpływ jako `_exec` wywołania).|  
|`_P_WAIT`|Wstrzymuje wątek wywołujący przed zakończeniem wykonywania nowego procesu (synchroniczne `_spawn`).|  
|`_P_NOWAIT`, `_P_NOWAITO`|Kontynuuje wykonywanie procesu wywołującego równocześnie z nowego procesu (asynchroniczne `_spawn`).|  
|`_P_DETACH`|Kontynuuje wykonywanie procesu wywołującego; nowy proces jest uruchamiane w tle bez dostępu do konsoli i klawiatury. Wywołuje się `_cwait` nowy proces zakończy się niepowodzeniem. To jest asynchroniczne `_spawn`.|  
  
## <a name="see-also"></a>Zobacz też  
 [_spawn, _wspawn — funkcje](../c-runtime-library/spawn-wspawn-functions.md)   
 [Stałe globalne](../c-runtime-library/global-constants.md)