---
title: _aligned_offset_malloc_dbg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _aligned_offset_malloc_dbg
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
- _aligned_offset_malloc_dbg
- aligned_offset_malloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- _aligned_offset_malloc_dbg function
- aligned_offset_malloc_dbg function
ms.assetid: 6c242307-c59e-4d63-aae5-d8cbec8e021c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd938b935ff5e69adf4d4e56cd70693cfd1a872d
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="alignedoffsetmallocdbg"></a>_aligned_offset_malloc_dbg

Przydziela pamięć na określonej granicy wyrównania (tylko w wersji do debugowania).

## <a name="syntax"></a>Składnia

```C
void * _aligned_offset_malloc_dbg(
   size_t size,
   size_t alignment,
   size_t offset,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Rozmiar alokacji żądanej pamięci.

*Wyrównanie*<br/>
Wartość wyrównania, która musi być całkowitą potęgą liczby 2.

*offset*<br/>
Przesunięcie alokacji pamięci, aby wymusić wyrównanie.

*Nazwa pliku*<br/>
Wskaźnik do nazwy pliku źródłowego, który żądanej operacji alokacji lub **NULL**.

*numer wiersza*<br/>
Numer w pliku źródłowym, której zażądano operacji alokacji wiersza lub **NULL**.

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do bloku pamięci, która została przydzielona lub **NULL** Jeśli działanie nie powiodło się.

## <a name="remarks"></a>Uwagi

**_aligned_offset_malloc_dbg —** jest wersja debugowania [_aligned_offset_malloc —](aligned-offset-malloc.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowana, każde wywołanie **_aligned_offset_malloc_dbg —** zostanie zmniejszona do wywołania **_aligned_offset_malloc —**. Zarówno **_aligned_offset_malloc —** i **_aligned_offset_malloc_dbg —** przydzielić bloku pamięci w stosie podstawowy, ale **_aligned_offset_malloc_dbg —** oferuje kilka debugowanie funkcji: buforów po obu stronach użytkownika część bloku do testowania przecieki, parametr typu bloku do śledzenia alokacji określonych typów, a *filename*/*numerwiersza* informacji do ustalenia źródła żądań alokacji.

**_aligned_offset_malloc_dbg —** przydziela bloku pamięci nieco więcej miejsca niż żądany *rozmiar*. Dodatkowe miejsce jest używane przez menedżera stosu debugowania, do łączenia bloków pamięci debugowania i do dostarczenia aplikacji informacji nagłówka debugowania i zastąpienia buforów. Gdy blok zostanie przydzielony, część użytkownika bloku jest wypełniania wartościami 0xCD a każdy bufor zastąpienia jest wypełniany wartościami 0xFD.

**_aligned_offset_malloc_dbg —** jest przydatne w sytuacjach, gdy jest potrzebne wyrównania w elemencie zagnieżdżonych; na przykład, jeśli wyrównanie było wymagane na klasy zagnieżdżonej.

**_aligned_offset_malloc_dbg —** opiera się na **— funkcja malloc**; Aby uzyskać więcej informacji, zobacz [— funkcja malloc](malloc.md).

Ta funkcja ustawia **errno** do **enomem —** Jeśli alokacja pamięci nie powiodła się lub jeśli była większa niż rozmiar żądanej **_heap_maxreq —**. Aby uzyskać więcej informacji na temat **errno**, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Ponadto **_aligned_offset_malloc —** sprawdza poprawność parametrów. Jeśli *wyrównanie* nie jest potęgą liczby 2 lub, jeśli *przesunięcie* jest większa niż lub równa *rozmiar* i różną od zera, ta funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [ Sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, ta funkcja zwraca **NULL** i ustawia **errno** do **einval —**.

Aby dowiedzieć się jak bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

Informacje o typach bloku alokacji i sposobu ich używania, zobacz [typów bloków w stercie debugowania](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_aligned_offset_malloc_dbg**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
