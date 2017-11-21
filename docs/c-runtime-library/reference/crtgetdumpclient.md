---
title: "_Crtgetdumpclient — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CrtGetDumpClient
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
- CrtGetDumpClient
- _CrtGetDumpClient
dev_langs: C++
helpviewer_keywords:
- _CrtGetDumpClient function
- CrtGetDumpClient function
ms.assetid: 9051867f-341b-493b-b53d-45d2b454a3ad
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5f75af68e7032d8365a2748624e75ef813b932bc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="crtgetdumpclient"></a>_CrtGetDumpClient
Pobiera bieżącą funkcję zrzucanie zdefiniowanym przez aplikację `_CLIENT_BLOCK` wpisz bloki pamięci (tylko wersja do debugowania).  
  
## <a name="syntax"></a>Składnia  
  
```  
_CRT_DUMP_CLIENT _CrtGetDumpClient( void );  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca bieżący procedury zrzutu.  
  
## <a name="remarks"></a>Uwagi  
 `_CrtGetDumpClient` Funkcja pobiera bieżącej funkcji punktów zaczepienia dla zrzucanie obiekty przechowywane w `_CLIENT_BLOCK` bloków pamięci dla C-run-time debugowania procesu zrzutu pamięci.  
  
 Aby uzyskać więcej informacji na temat korzystania innych obsługą punktu zaczepienia funkcji środowiska wykonawczego i pisanie własnych klienta zdefiniowane przez funkcje punktów zaczepienia, zobacz [debugowania pisanie funkcji punktów zaczepienia](/visualstudio/debugger/debug-hook-function-writing).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_CrtGetDumpClient`|\<crtdbg.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury debugowania](../../c-runtime-library/debug-routines.md)   
 [_Crtreportblocktype —](../../c-runtime-library/reference/crtreportblocktype.md)   
 [_Crtsetdumpclient —](../../c-runtime-library/reference/crtsetdumpclient.md)