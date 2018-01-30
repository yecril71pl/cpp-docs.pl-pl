---
title: "_Crtgetreporthook — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtGetReportHook
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- CrtGetReportHook
- _CrtGetReportHook
dev_langs:
- C++
helpviewer_keywords:
- CrtGetReportHook function
- _CrtGetReportHook function
ms.assetid: 922758ed-7edd-4359-9c92-0535192dc11a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 94b92ee2bc6f30df99db23cb1417f1e490d24fa5
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="crtgetreporthook"></a>_CrtGetReportHook
Pobiera zdefiniowane przez klienta funkcji raportowania dla Przechwytywanie go do C wykonawczego do debugowania raportowania procesu (tylko wersja do debugowania).  
  
## <a name="syntax"></a>Składnia  
  
```  
_CRT_REPORT_HOOK _CrtGetReportHook( void );  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca bieżącą funkcję raportowania zdefiniowane przez klienta.  
  
## <a name="remarks"></a>Uwagi  
 `_CrtGetReportHook`umożliwia aplikacji można pobrać bieżącą funkcję raportowania dla biblioteki wykonawcze debugowania C raportowania procesu.  
  
 Aby uzyskać więcej informacji na temat korzystania innych obsługą punktu zaczepienia funkcji środowiska wykonawczego i pisanie własnych klienta zdefiniowane przez funkcje punktów zaczepienia, zobacz [debugowania pisanie funkcji punktów zaczepienia](/visualstudio/debugger/debug-hook-function-writing).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_CrtGetReportHook`|\<crtdbg.h>|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.  
  
## <a name="example"></a>Przykład  
 Przykładowe zastosowania `_CrtSetReportHook`, zobacz [raport](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/report).  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury debugowania](../../c-runtime-library/debug-routines.md)   
 [_CrtSetReportHook](../../c-runtime-library/reference/crtsetreporthook.md)