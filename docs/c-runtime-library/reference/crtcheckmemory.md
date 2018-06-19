---
title: _Crtcheckmemory — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _CrtCheckMemory function
- CrtCheckMemory function
ms.assetid: 457cc72e-60fd-4177-ab5c-6ae26a420765
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b6d4b84fd717525e7206956964204794fe6b88c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32396667"
---
# <a name="crtcheckmemory"></a>_CrtCheckMemory

Potwierdza integralność bloki pamięci przydzielić w stercie debugowania (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C

int _CrtCheckMemory( void );
```

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia **_crtcheckmemory —** zwraca wartość PRAWDA; w przeciwnym razie funkcja zwraca wartość FALSE.

## <a name="remarks"></a>Uwagi

**_Crtcheckmemory —** funkcja weryfikuje pamięci przydzielonej przez menedżera sterty debugowania przez sprawdzanie poprawności podstawowej sterty podstawowej i sprawdzania każdego bloku pamięci. Po napotkaniu niespójność pamięci lub błąd w podstawowej sterty podstawowej, informacje o nagłówku debugowania lub buforów Zastąp **_crtcheckmemory —** generuje raport debugowania informacje opisujące warunku błędu. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołań **_crtcheckmemory —** są usuwane podczas przetwarzania wstępnego.

Zachowanie **_crtcheckmemory —** mogą być kontrolowane przez ustawienie pola bitowego [_crtdbgflag —](../../c-runtime-library/crtdbgflag.md) Flaga przy użyciu [_crtsetdbgflag —](crtsetdbgflag.md) funkcji. Włączanie **_crtdbg_check_always_df —** bit powoduje ON pole **_crtcheckmemory —** wywoływana za każdym razem, gdy zażądano operacji alokacji pamięci. Mimo że ta metoda spowalnia wykonywania, jest przydatne w przypadku przechwytywania błędów szybko. Włączanie **_crtdbg_alloc_mem_df —** bit przyczyny OFF pola **_crtcheckmemory —** Sprawdź stos i natychmiast zwraca **TRUE**.

Ponieważ ta funkcja zwraca **TRUE** lub **FALSE**, mogą być przekazywane do jednego z [_ASSERT](assert-asserte-assert-expr-macros.md) makra, aby utworzyć prosty błąd debugowania mechanizmu obsługi. Poniższy przykład powoduje błąd potwierdzenia wykryje uszkodzenie w stercie:

```C
_ASSERTE( _CrtCheckMemory( ) );
```

Aby uzyskać więcej informacji o tym, jak **_crtcheckmemory —** może być używany z innymi funkcjami debugowania, zobacz [funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details). Omówienie zarządzania pamięcią i sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtCheckMemory**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="example"></a>Przykład

Przykładowe zastosowania **_crtcheckmemory —**, zobacz [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1).

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
