---
title: _Crtmemdumpallobjectssince — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 24cf01facaba326c36454ea5410da8dbb05848f2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="crtmemdumpallobjectssince"></a>_CrtMemDumpAllObjectsSince

Zrzuty informacje dotyczące obiektów na stercie od początku wykonania programu, lub ze stanu sterty określony (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C
void _CrtMemDumpAllObjectsSince(
   const _CrtMemState *state
);
```

### <a name="parameters"></a>Parametry

*Stan* wskaźnik do stanu sterty, aby rozpocząć zrzucanie z lub **NULL**.

## <a name="remarks"></a>Uwagi

**_Crtmemdumpallobjectssince —** funkcja zrzuty informacji debugowania w nagłówku obiekty przydzielone na stercie w postaci czytelny dla użytkownika. Można informacji zrzutu przez aplikację do śledzenia alokacji i wykrywać problemy z pamięcią. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołań **_crtmemdumpallobjectssince —** są usuwane podczas przetwarzania wstępnego.

**_Crtmemdumpallobjectssince —** używa wartości *stanu* parametr, aby ustalić, gdzie można zainicjować operacji zrzutu. Aby rozpocząć zrzucanie ze stanu sterty określony *stanu* parametru musi być wskaźnikiem do **_crtmemstate —** strukturę, która ma zostać wypełnione podczas [_crtmemcheckpoint —](crtmemcheckpoint.md) przed **_Crtmemdumpallobjectssince —** została wywołana. Gdy *stanu* jest **NULL**, funkcja rozpoczyna zrzutu od początku wykonywania programu.

Jeśli aplikacja została zainstalowana funkcji punktów zaczepienia zrzutu wywołując [_crtsetdumpclient —](crtsetdumpclient.md), a następnie za każdym razem, gdy **_crtmemdumpallobjectssince —** zrzuty informacji o **_client_block —** typ bloku, wywołuje również funkcję zrzutu dostarczone przez aplikację. Domyślnie wewnętrzny bloki wykonawcze języka C (**_crt_block —**) nie są uwzględnione w operacji zrzutu pamięci. [_Crtsetdbgflag —](crtsetdbgflag.md) funkcji można włączyć **_crtdbg_check_crt_df —** bit z **_crtdbgflag —** aby uwzględnić te bloki. Ponadto bloki oznaczony jako zwolniony, lub zignorować (**_free_block —**, **_ignore_block —**) nie są uwzględniane w zrzut pamięci.

Aby uzyskać więcej informacji na temat funkcji stanu sterty i **_crtmemstate —** struktury, zobacz [funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać więcej informacji dotyczących sposobu bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtMemDumpAll-ObjectsSince**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="example"></a>Przykład

Przykładowe zastosowania **_crtmemdumpallobjectssince —**, zobacz [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
