---
title: _CrtGetAllocHook
ms.date: 11/04/2016
apiname:
- _CrtGetAllocHook
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
- CrtGetAllocHook
- _CrtGetAllocHook
helpviewer_keywords:
- _CrtGetAllocHook function
- CrtGetAllocHook function
ms.assetid: 036acf7c-547a-4b3f-a636-80451070d7ed
ms.openlocfilehash: b49c4cfc820a925187d0ea4d1562965295bea817
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62339913"
---
# <a name="crtgetallochook"></a>_CrtGetAllocHook

Pobiera bieżącą funkcję alokacji zdefiniowaną przez klienta dla przechwytywanie do procesu alokacji pamięci debugowania w czasie wykonywania C (tylko wersja debugowania).

## <a name="syntax"></a>Składnia

```C
_CRT_ALLOC_HOOK _CrtGetAllocHook( void );
```

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość funkcji podłączania alokacji aktualnie zdefiniowanych.

## <a name="remarks"></a>Uwagi

**_Crtgetallochook —** pobiera bieżącą funkcję podłączania zdefiniowaną przez klienta aplikacji do procesu alokacji pamięci biblioteki debugowania w czasie wykonywania C.

Aby uzyskać więcej informacji na temat korzystania innych funkcją podłączania funkcji wykonawczej i pisanie własnych zdefiniowaną przez klienta funkcje punktów zaczepienia, zobacz [debugowania pisania funkcji punktów zaczepienia](/visualstudio/debugger/debug-hook-function-writing).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtGetAllocHook**|\<crtdbg.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetAllocHook](crtsetallochook.md)<br/>
