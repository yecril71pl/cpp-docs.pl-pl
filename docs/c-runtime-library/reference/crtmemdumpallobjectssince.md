---
title: "_Crtmemdumpallobjectssince — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtMemDumpAllObjectsSince
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
- CrtMemDumpAllObjectsSince
- _CrtMemDumpAllObjectsSince
dev_langs:
- C++
helpviewer_keywords:
- _CrtMemDumpAllObjectsSince function
- CrtMemDumpAllObjectsSince function
ms.assetid: c48a447a-e6bb-475c-9271-a3021182a0dc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c1c04d21b1c4009bd93e608d1c243d5b459e2422
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="crtmemdumpallobjectssince"></a>_CrtMemDumpAllObjectsSince
Zrzuty informacje dotyczące obiektów na stercie od początku wykonania programu, lub ze stanu sterty określony (tylko wersja do debugowania).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      void _CrtMemDumpAllObjectsSince(   
   const _CrtMemState *state   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `state`  
 Wskaźnik do stanu sterty, aby rozpocząć zrzucanie z lub **NULL**.  
  
## <a name="remarks"></a>Uwagi  
 `_CrtMemDumpAllObjectsSince` Funkcja zrzuty informacji debugowania w nagłówku obiekty przydzielone na stercie w postaci czytelny dla użytkownika. Można informacji zrzutu przez aplikację do śledzenia alokacji i wykrywać problemy z pamięcią. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołań `_CrtMemDumpAllObjectsSince` są usuwane podczas przetwarzania wstępnego.  
  
 `_CrtMemDumpAllObjectsSince`używa wartości `state` parametr, aby ustalić, gdzie można zainicjować operacji zrzutu. Aby rozpocząć zrzucanie ze stanu sterty określony `state` parametru musi być wskaźnikiem do **_crtmemstate —** strukturę, która ma zostać wypełnione podczas [_crtmemcheckpoint —](../../c-runtime-library/reference/crtmemcheckpoint.md) przed `_CrtMemDumpAllObjectsSince` został wywołuje się. Gdy `state` jest **NULL**, funkcja rozpoczyna zrzutu od początku wykonywania programu.  
  
 Jeśli aplikacja została zainstalowana funkcji punktów zaczepienia zrzutu przez wywołanie metody [_crtsetdumpclient —](../../c-runtime-library/reference/crtsetdumpclient.md), a następnie za każdym razem, gdy `_CrtMemDumpAllObjectsSince` zrzuty informacji o `_CLIENT_BLOCK` typu bloku, wywołuje również funkcję zrzutu dostarczone przez aplikację. Domyślnie wewnętrzny bloki wykonawcze języka C (`_CRT_BLOCK`) nie są uwzględnione w operacji zrzutu pamięci. [_Crtsetdbgflag —](../../c-runtime-library/reference/crtsetdbgflag.md) funkcji można włączyć `_CRTDBG_CHECK_CRT_DF` bit z **_crtdbgflag —** aby uwzględnić te bloki. Ponadto bloki oznaczony jako zwolniony, lub zignorować (**_free_block —**, **_ignore_block —**) nie są uwzględniane w zrzut pamięci.  
  
 Aby uzyskać więcej informacji na temat funkcji stanu sterty i `_CrtMemState` struktury, zobacz [funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać więcej informacji dotyczących sposobu bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|**_CrtMemDumpAll-ObjectsSince**|\<crtdbg.h>|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.  
  
## <a name="example"></a>Przykład  
 Przykładowe zastosowania `_CrtMemDumpAllObjectsSince`, zobacz [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury debugowania](../../c-runtime-library/debug-routines.md)   
 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)