---
title: "_Crtdumpmemoryleaks — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CrtDumpMemoryLeaks
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
- CRTDBG_LEAK_CHECK_DF
- CRTDBG_CHECK_CRT_DF
- _CRTDBG_LEAK_CHECK_DF
- CrtDumpMemoryLeaks
- _CrtDumpMemoryLeaks
- _CRTDBG_CHECK_CRT_DF
dev_langs: C++
helpviewer_keywords:
- CrtDumpMemoryLeaks function
- CRTDBG_LEAK_CHECK_DF macro
- _CRTDBG_LEAK_CHECK_DF macro
- _CrtDumpMemoryLeaks function
- CRTDBG_CHECK_CRT_DF macro
- _CRTDBG_CHECK_CRT_DF macro
ms.assetid: 71b2eab4-7f55-44e8-a55a-bfea4f32d34c
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 799cb3a867af9695fcb72ae6d681168f604d880f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="crtdumpmemoryleaks"></a>_CrtDumpMemoryLeaks
Zrzuty całą pamięć blokuje w stercie debugowania gdy wystąpił wyciek pamięci (tylko wersja do debugowania).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
int _CrtDumpMemoryLeaks( void );  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 `_CrtDumpMemoryLeaks`Zwraca wartość PRAWDA, jeśli zostanie znaleziony przeciek pamięci. W przeciwnym razie funkcja zwraca wartość FALSE.  
  
## <a name="remarks"></a>Uwagi  
 `_CrtDumpMemoryLeaks` Funkcja określa, czy od czasu rozpoczęcia wykonywania programu wystąpił wyciek pamięci. W przypadku odnalezienia przeciek informacje o nagłówku debugowania dla wszystkich obiektów na stercie jest utworzyć zrzutu w postaci czytelny dla użytkownika. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołań `_CrtDumpMemoryLeaks` są usuwane podczas przetwarzania wstępnego.  
  
 `_CrtDumpMemoryLeaks`często jest wywoływana po zakończeniu wykonywania programu, aby sprawdzić, czy wszystkie pamięci przydzielonej przez aplikację został zwolniony. Funkcję można wywołać automatycznie Kończenie działania programu włączając `_CRTDBG_LEAK_CHECK_DF` pola bitowego ze [_crtdbgflag —](../../c-runtime-library/crtdbgflag.md) Flaga przy użyciu [_crtsetdbgflag —](../../c-runtime-library/reference/crtsetdbgflag.md) funkcji.  
  
 `_CrtDumpMemoryLeaks`wywołania [_crtmemcheckpoint —](../../c-runtime-library/reference/crtmemcheckpoint.md) można uzyskać bieżącego stanu sterty, a następnie skanuje stanu dla bloków, które nie został zwolniony. W przypadku bloku niezwolnionych `_CrtDumpMemoryLeaks` wywołania [_crtmemdumpallobjectssince —](../../c-runtime-library/reference/crtmemdumpallobjectssince.md) zrzutu informacji dla wszystkich obiektów przydzielić w stercie od początku wykonywania programu.  
  
 Domyślnie wewnętrzny bloki wykonawcze języka C (`_CRT_BLOCK`) nie są uwzględnione w operacji zrzutu pamięci. [_Crtsetdbgflag —](../../c-runtime-library/reference/crtsetdbgflag.md) funkcji można włączyć `_CRTDBG_CHECK_CRT_DF` bit z `_crtDbgFlag` do uwzględnienia w procesie wykrywania przeciek te bloki.  
  
 Aby uzyskać więcej informacji na temat funkcji stanu sterty i `_CrtMemState` struktury, zobacz [funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać więcej informacji dotyczących sposobu bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_CrtDumpMemoryLeaks`|\<crtdbg.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.  
  
## <a name="example"></a>Przykład  
 Przykładowe zastosowania `_CrtDumpMemoryLeaks`, zobacz [crt_dbg1](http://msdn.microsoft.com/en-us/17b4b20c-e849-48f5-8eb5-dca6509cbaf9).  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury debugowania](../../c-runtime-library/debug-routines.md)