---
title: _aligned_realloc_dbg — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _aligned_realloc_dbg
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
- aligned_realloc_dbg
- _aligned_realloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- _aligned_realloc_dbg function
- aligned_realloc_dbg function
ms.assetid: 8aede920-991e-44cd-867f-83dc2165db47
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 546ad1b4bb745274894754a185c57bacb82b0061
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="alignedreallocdbg"></a>_aligned_realloc_dbg

Zmienia rozmiar blok pamięci przydzielony przy [_aligned_malloc —](aligned-malloc.md) lub [_aligned_offset_malloc —](aligned-offset-malloc.md) (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C
void * _aligned_realloc_dbg(
   void *memblock,
   size_t size,
   size_t alignment,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Bieżący wskaźnik bloku pamięci.

*Rozmiar*<br/>
Rozmiar alokacji żądanej pamięci.

*Wyrównanie*<br/>
Wartość wyrównania, która musi być całkowitą potęgą liczby 2.

*Nazwa pliku*<br/>
Wskaźnik do nazwy pliku źródłowego, który zażądał **realloc** operacji ani mieć wartości NULL.

*numer wiersza*<br/>
Numer wiersza na plik źródłowy gdzie **realloc** operacja była żądana ani mieć wartości NULL.

## <a name="return-value"></a>Wartość zwracana

**_aligned_realloc_dbg —** zwraca typ void wskaźnik do bloku pamięci przydzielić (i prawdopodobnie przenoszenia). Wartość zwracana jest **NULL** Jeśli rozmiar wynosi zero, a argument bufor nie jest **NULL**, lub jeśli nie ma dostatecznej ilości dostępnej pamięci, aby rozwinąć blok na dany rozmiar. W pierwszym przypadku oryginalnego bloku zostanie zwolniona. W ciągu sekundy oryginalnego bloku jest bez zmian. Wartości zwracanej wskazuje miejsce do magazynowania, które na pewno jest odpowiednio dopasowany do przechowywania obiekty dowolnego typu. Aby uzyskać wskaźnik do typu innego niż void, użyj typu rzutowania wartości zwracanej.

Jest błędem ponowne przydzielenie pamięci i zmienić wyrównania bloku.

## <a name="remarks"></a>Uwagi

**_aligned_realloc_dbg —** jest wersja debugowania [_aligned_realloc —](aligned-realloc.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowana, każde wywołanie **_aligned_realloc_dbg —** zostanie zmniejszona do wywołania **_aligned_realloc —**. Zarówno **_aligned_realloc —** i **_aligned_realloc_dbg —** ponownie przydzielić bloku pamięci w stosie podstawowy, ale **_aligned_realloc_dbg —** bierze pod uwagę kilka funkcji debugowania : buforów po obu stronach użytkownika część bloku do testowania przecieki, parametr typu bloku do śledzenia alokacji określonych typów, a *filename*/*numer wiersza* informacji do ustalenia źródła żądań alokacji.

**_aligned_realloc_dbg —** przydziela ponownie bloku pamięci określony nieco więcej miejsca niż żądany *newSize*. *newSize* może być większa lub mniejsza niż rozmiar bloku pierwotnie alokacji pamięci. Dodatkowe miejsce jest używane przez menedżera stosu debugowania, do łączenia bloków pamięci debugowania i do dostarczenia aplikacji informacji nagłówka debugowania i zastąpienia buforów. Ponowne przydzielenie może spowodować przeniesienie do innej lokalizacji w stercie oryginalnego bloku pamięci, jak również zmiana rozmiaru bloku pamięci. Jeśli blok pamięci jest przenoszony, zawartość oryginalnego bloku zostaną zastąpione.

**_aligned_realloc_dbg —** ustawia **errno** do **enomem —** Jeśli alokacja pamięci nie powiedzie się lub jeśli przekracza ilość pamięci potrzebnej (łącznie z czynności wymienionych wcześniej) **_ Heap_maxreq —**. Aby uzyskać informacji dotyczących tego i innych kodów błędów, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Ponadto **_aligned_realloc_dbg —** sprawdza poprawność parametrów. Jeśli *wyrównanie* nie jest potęgą 2, ta funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, ta funkcja zwraca **NULL** i ustawia **errno** do **einval —**.

Aby dowiedzieć się jak bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Informacje o typach bloku alokacji i sposobu ich używania, zobacz [typów bloków w stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje o różnicach między wywoływanie funkcji sterty standardowe i jego wersji do debugowania w kompilację debugowania aplikacji, zobacz [debugowania wersji z funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_aligned_realloc_dbg**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
