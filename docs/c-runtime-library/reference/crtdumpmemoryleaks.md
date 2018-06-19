---
title: _Crtdumpmemoryleaks — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtDumpMemoryLeaks
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
dev_langs:
- C++
helpviewer_keywords:
- CrtDumpMemoryLeaks function
- CRTDBG_LEAK_CHECK_DF macro
- _CRTDBG_LEAK_CHECK_DF macro
- _CrtDumpMemoryLeaks function
- CRTDBG_CHECK_CRT_DF macro
- _CRTDBG_CHECK_CRT_DF macro
ms.assetid: 71b2eab4-7f55-44e8-a55a-bfea4f32d34c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 68a187283eedadcd2f435b0900fde648a5010368
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32396969"
---
# <a name="crtdumpmemoryleaks"></a>_CrtDumpMemoryLeaks

Zrzuty całą pamięć blokuje w stercie debugowania gdy wystąpił wyciek pamięci (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C

int _CrtDumpMemoryLeaks( void );
```

## <a name="return-value"></a>Wartość zwracana

**_Crtdumpmemoryleaks —** zwraca wartość PRAWDA, jeśli zostanie znaleziony przeciek pamięci. W przeciwnym razie funkcja zwraca wartość FALSE.

## <a name="remarks"></a>Uwagi

**_Crtdumpmemoryleaks —** funkcja określa, czy od czasu rozpoczęcia wykonywania programu wystąpił wyciek pamięci. W przypadku odnalezienia przeciek informacje o nagłówku debugowania dla wszystkich obiektów na stercie jest utworzyć zrzutu w postaci czytelny dla użytkownika. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołań **_crtdumpmemoryleaks —** są usuwane podczas przetwarzania wstępnego.

**_Crtdumpmemoryleaks —** jest często nazywany na końcu wykonania programu, aby sprawdzić, czy wszystkie pamięci przydzielonej przez aplikację został zwolniony. Funkcję można wywołać automatycznie Kończenie działania programu włączając **_crtdbg_leak_check_df —** pola bitowego ze [_crtdbgflag —](../../c-runtime-library/crtdbgflag.md) Flaga przy użyciu [_crtsetdbgflag —](crtsetdbgflag.md)funkcji.

**_Crtdumpmemoryleaks —** wywołania [_crtmemcheckpoint —](crtmemcheckpoint.md) można uzyskać bieżącego stanu sterty, a następnie skanuje stanu dla bloków, które nie został zwolniony. W przypadku bloku niezwolnionych **_crtdumpmemoryleaks —** wywołania [_crtmemdumpallobjectssince —](crtmemdumpallobjectssince.md) zrzutu informacji dla wszystkich obiektów przydzielić w stercie od początku wykonywania programu.

Domyślnie wewnętrzny bloki wykonawcze języka C (**_crt_block —**) nie są uwzględnione w operacji zrzutu pamięci. [_Crtsetdbgflag —](crtsetdbgflag.md) funkcji można włączyć **_crtdbg_check_crt_df —** bit z **_crtdbgflag —** do uwzględnienia w procesie wykrywania przeciek te bloki.

Aby uzyskać więcej informacji na temat funkcji stanu sterty i **_crtmemstate —** struktury, zobacz [funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać więcej informacji dotyczących sposobu bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtDumpMemoryLeaks**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="example"></a>Przykład

Przykładowe zastosowania **_crtdumpmemoryleaks —**, zobacz [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1).

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
