---
title: _CrtCheckMemory
ms.date: 11/04/2016
apiname:
- _CrtCheckMemory
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
- CrtCheckMemory
- _CrtCheckMemory
helpviewer_keywords:
- _CrtCheckMemory function
- CrtCheckMemory function
ms.assetid: 457cc72e-60fd-4177-ab5c-6ae26a420765
ms.openlocfilehash: cb39a76c140934dabdd1269c02aba6018691f917
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537153"
---
# <a name="crtcheckmemory"></a>_CrtCheckMemory

Potwierdza integralność bloki pamięci przydzielane w stosie debugowania (tylko wersja debugowania).

## <a name="syntax"></a>Składnia

```C

int _CrtCheckMemory( void );
```

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia **_CrtCheckMemory** zwraca wartość PRAWDA; w przeciwnym razie funkcja zwraca wartość FALSE.

## <a name="remarks"></a>Uwagi

**_CrtCheckMemory** funkcja sprawdza poprawność pamięci przydzielonej przez menedżera stosu debugowania przez weryfikowanie bazowego stosu podstawowego i zapoznanie się każdy blok pamięci. Jeśli okaże się niespójność w pamięci lub błąd w podstawowej podstawowej sterty, informacji nagłówka debugowania lub zastąpienia buforów, **_CrtCheckMemory** generuje raport debugowania przy użyciu informacji opisujących warunku błędu. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołania **_CrtCheckMemory** są usuwane podczas przetwarzania wstępnego.

Zachowanie **_CrtCheckMemory** mogą być kontrolowane przez ustawienie pola bitowe [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) Flaga przy użyciu [_CrtSetDbgFlag](crtsetdbgflag.md) funkcji. Włączanie **_CRTDBG_CHECK_ALWAYS_DF** wyników ON pól bitowych **_CrtCheckMemory** wywoływana za każdym razem, gdy zażądano operacji alokacji pamięci. Chociaż ta metoda spowalnia wykonanie, jest przydatne w przypadku przechwytywania błędów szybko. Włączanie **_CRTDBG_ALLOC_MEM_DF** przyczyny OFF pola bitowe **_CrtCheckMemory** Sprawdź sterty i natychmiast przywrócić **TRUE**.

Ponieważ ta funkcja zwraca **TRUE** lub **FALSE**, mogą być przekazywane do jednego z [_ASSERT](assert-asserte-assert-expr-macros.md) makra, aby utworzyć prosty błąd debugowania mechanizm obsługi. Poniższy przykład powoduje błąd potwierdzenia, jeśli zostanie wykryte uszkodzenie w stosie:

```C
_ASSERTE( _CrtCheckMemory( ) );
```

Aby uzyskać więcej informacji o tym, jak **_CrtCheckMemory** mogą być używane z innych funkcji debugowania, zobacz [funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details). Omówienie zarządzania pamięcią i stosu debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtCheckMemory**|\<crtdbg.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="example"></a>Przykład

Przykład sposobu użycia **_CrtCheckMemory**, zobacz [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1).

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
