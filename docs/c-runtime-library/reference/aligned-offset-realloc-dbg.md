---
title: _aligned_offset_realloc_dbg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _aligned_offset_realloc_dbg
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
- aligned_offset_realloc_dbg
- _aligned_offset_realloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- aligned_offset_realloc_dbg function
- _aligned_offset_realloc_dbg function
ms.assetid: 64e30a12-887e-453b-aea8-aed793fca9d8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ee9dec91e8e5173d3933b8637ec767bd160cc225
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="alignedoffsetreallocdbg"></a>_aligned_offset_realloc_dbg

Zmienia rozmiar blok pamięci przydzielony przy [_aligned_malloc —](aligned-malloc.md) lub [_aligned_offset_malloc —](aligned-offset-malloc.md) (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C
void * _aligned_offset_realloc_dbg(
   void *memblock,
   size_t size,
   size_t alignment,
   size_t offset,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Bieżący wskaźnik bloku pamięci.

*Rozmiar*<br/>
Rozmiar alokacji pamięci.

*Wyrównanie*<br/>
Wartość wyrównania, która musi być całkowitą potęgą liczby 2.

*offset*<br/>
Przesunięcie alokacji pamięci, aby wymusić wyrównanie.

*Nazwa pliku*<br/>
Wskaźnik do nazwy pliku źródłowego, który zażądał **aligned_offset_realloc —** operacji lub **NULL**.

*numer wiersza*<br/>
Numer wiersza na plik źródłowy gdzie **aligned_offset_realloc —** zażądano operacji lub **NULL**.

## <a name="return-value"></a>Wartość zwracana

**_aligned_offset_realloc_dbg —** zwraca typ void wskaźnik do bloku pamięci przydzielić (i prawdopodobnie przenoszenia). Wartość zwracana jest **NULL** Jeśli rozmiar wynosi zero, a argument bufor nie jest **NULL**, lub jeśli nie ma dostatecznej ilości dostępnej pamięci, aby rozwinąć blok na dany rozmiar. W pierwszym przypadku oryginalnego bloku zostanie zwolniona. W drugim przypadku oryginalnego bloku jest bez zmian. Wartości zwracanej wskazuje miejsce do magazynowania, które na pewno jest odpowiednio dopasowany do przechowywania obiekty dowolnego typu. Aby uzyskać wskaźnik do typu innego niż void, użyj typu rzutowania wartości zwracanej.

## <a name="remarks"></a>Uwagi

**_aligned_offset_realloc_dbg —** jest wersja debugowania [_aligned_offset_realloc —](aligned-offset-realloc.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowana, każde wywołanie **_aligned_offset_realloc_dbg —** zostanie zmniejszona do wywołania **_aligned_offset_realloc —**. Zarówno **_aligned_offset_realloc —** i **_aligned_offset_realloc_dbg —** ponownie przydzielić bloku pamięci w stosie podstawowy, ale **_aligned_offset_realloc_dbg —** bierze pod uwagę kilka funkcji debugowania: buforów po obu stronach użytkownika część bloku do testowania przecieki, parametr typu bloku do śledzenia alokacji określonych typów, a *filename*/*numer wiersza*  informacji do ustalenia źródła żądań alokacji.

Podobnie jak [_aligned_offset_malloc —](aligned-offset-malloc.md), **_aligned_offset_realloc_dbg —** umożliwia struktury wyrównania przy przesunięciu w strukturze.

**_realloc_dbg —** przydziela ponownie bloku pamięci określony nieco więcej miejsca niż żądany *newSize*. *newSize* może być większa lub mniejsza niż rozmiar bloku pierwotnie alokacji pamięci. Dodatkowe miejsce jest używane przez menedżera stosu debugowania, do łączenia bloków pamięci debugowania i do dostarczenia aplikacji informacji nagłówka debugowania i zastąpienia buforów. Ponowne przydzielenie może spowodować przeniesienie do innej lokalizacji w stercie oryginalnego bloku pamięci, jak również zmiana rozmiaru bloku pamięci. Jeśli blok pamięci jest przenoszony, zawartość oryginalnego bloku zostaną zastąpione.

Ta funkcja ustawia **errno** do **enomem —** Jeśli alokacja pamięci nie powiodła się lub jeśli była większa niż rozmiar żądanej **_heap_maxreq —**. Aby uzyskać więcej informacji na temat **errno**, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Ponadto **_aligned_offset_realloc_dbg —** sprawdza poprawność parametrów. Jeśli *wyrównanie* nie jest potęgą liczby 2 lub, jeśli *przesunięcie* jest większa niż lub równa *rozmiar* i różną od zera, ta funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [ Sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, ta funkcja zwraca **NULL** i ustawia **errno** do **einval —**.

Aby dowiedzieć się jak bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Informacje o typach bloku alokacji i sposobu ich używania, zobacz [typów bloków w stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje o różnicach między wywoływanie funkcji sterty standardowe i jego wersji do debugowania w kompilację debugowania aplikacji, zobacz [debugowania wersji z funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_aligned_offset_realloc_dbg**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
