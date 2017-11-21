---
title: "_Crtgetreporthook — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CrtGetReportHook
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
dev_langs: C++
helpviewer_keywords:
- CrtGetReportHook function
- _CrtGetReportHook function
ms.assetid: 922758ed-7edd-4359-9c92-0535192dc11a
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2c98e0d6a41be7a5d472f6412fdee454db564ffe
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
|`_CrtGetReportHook`|\<crtdbg.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.  
  
## <a name="example"></a>Przykład  
 Przykładowe zastosowania `_CrtSetReportHook`, zobacz [raport](http://msdn.microsoft.com/en-us/f6e08c30-6bd9-459a-830a-56deec0d2051).  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury debugowania](../../c-runtime-library/debug-routines.md)   
 [_Crtsetreporthook —](../../c-runtime-library/reference/crtsetreporthook.md)