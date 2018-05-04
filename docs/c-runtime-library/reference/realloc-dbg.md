---
title: _realloc_dbg — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _realloc_dbg
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
- _realloc_dbg
- realloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- reallocating memory blocks
- realloc_dbg function
- memory blocks, reallocating
- memory, reallocating
- _realloc_dbg function
ms.assetid: 7c3cb780-51ed-4d9c-9929-cdde606d846a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 91d04e78c6f3521c56cd74968a761a2d436e36bf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="reallocdbg"></a>_realloc_dbg

Przydziela ponownie określony blok pamięci w stercie przez przeniesienie lub zmiana rozmiaru bloku (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C
void *_realloc_dbg(
   void *userData,
   size_t newSize,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*Danych użytkownika*<br/>
Wskaźnik do bloku wcześniej alokacji pamięci.

*newSize*<br/>
Żądany rozmiar bloku reallocated (w bajtach).

*blockType*<br/>
Żądany typ bloku reallocated: **_client_block —** lub **_normal_block —**.

*Nazwa pliku*<br/>
Wskaźnik do nazwy pliku źródłowego, który zażądał **realloc** operacji ani mieć wartości NULL.

*numer wiersza*<br/>
Numer wiersza na plik źródłowy gdzie **realloc** operacja była żądana ani mieć wartości NULL.

*Filename* i *numer wiersza* parametry są dostępne tylko podczas **_realloc_dbg —** została jawnie wywołana lub [_crtdbg_map_alloc —](../../c-runtime-library/crtdbg-map-alloc.md) stała preprocesora została zdefiniowana.

## <a name="return-value"></a>Wartość zwracana

Po pomyślnym ukończeniu ta funkcja zwraca wskaźnik do użytkownika części bloku przydzielić pamięci, nowych funkcji programu obsługi albo zwraca wartość NULL. Pełny opis zwracany zachowania zobacz sekcję poniżej uwagi. Aby uzyskać więcej informacji o sposobie korzystania z nowych funkcji programu obsługi, zobacz [realloc](realloc.md) funkcji.

## <a name="remarks"></a>Uwagi

**_realloc_dbg —** jest wersja debugowania [realloc](realloc.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowana, każde wywołanie **_realloc_dbg —** zostanie zmniejszona do wywołania **realloc**. Zarówno **realloc** i **_realloc_dbg —** ponownie przydzielić bloku pamięci w stosie podstawowy, ale **_realloc_dbg —** bierze pod uwagę kilka funkcji debugowania: buforów po obu stronach Użytkownik część bloku do testowania przecieki, parametr typu bloku do śledzenia alokacji określonych typów, i *filename*/*numer wiersza* informacji do ustalenia pochodzenia żądań alokacji.

**_realloc_dbg —** przydziela ponownie bloku pamięci określony nieco więcej miejsca niż żądany *newSize*. *newSize* może być większa lub mniejsza niż rozmiar bloku pierwotnie alokacji pamięci. Dodatkowe miejsce jest używane przez menedżera stosu debugowania, do łączenia bloków pamięci debugowania i do dostarczenia aplikacji informacji nagłówka debugowania i zastąpienia buforów. Ponowne przydzielenie może spowodować przeniesienie do innej lokalizacji w stercie oryginalnego bloku pamięci, jak również zmiana rozmiaru bloku pamięci. Jeśli blok pamięci jest przenoszony, zawartość oryginalnego bloku zostaną zastąpione.

**_realloc_dbg —** ustawia **errno** do **enomem —** Jeśli alokacja pamięci nie powiedzie się lub jeśli przekracza ilość pamięci potrzebnej (łącznie z czynności wymienionych wcześniej) **_HEAP_ MAXREQ**. Aby uzyskać informacji dotyczących tego i innych kodów błędów, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Aby dowiedzieć się jak bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Informacje o typach bloku alokacji i sposobu ich używania, zobacz [typów bloków w stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje o różnicach między wywoływanie funkcji sterty standardowe i jego wersji do debugowania w kompilację debugowania aplikacji, zobacz [debugowania wersji z funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_realloc_dbg**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="example"></a>Przykład

Zapoznaj się z przykładem w [_msize_dbg —](msize-dbg.md) tematu.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
