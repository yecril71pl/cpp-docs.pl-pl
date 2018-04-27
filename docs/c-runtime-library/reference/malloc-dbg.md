---
title: _malloc_dbg — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _malloc_dbg
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
- malloc_dbg
- _malloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- malloc_dbg function
- memory allocation
- _malloc_dbg function
ms.assetid: c97eca51-140b-4461-8bd2-28965b49ecdb
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 080bd3813fe14187df7f6b6184a0cfe21e9c5243
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="mallocdbg"></a>_malloc_dbg

Przydziela blok pamięci sterty z dodatkowym miejscem dla nagłówka debugowania i zastąpić buforów (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C
void *_malloc_dbg(
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Żądany rozmiar bloku pamięci (w bajtach).

*blockType*<br/>
Żądany typ bloku pamięci: **_client_block —** lub **_normal_block —**.

*Nazwa pliku*<br/>
Wskaźnik na nazwę pliku źródłowego, który zażądał operacji alokacji lub NULL.

*numer wiersza*<br/>
Numer wiersza w pliku źródłowym, gdzie zażądano operacji alokacji lub NULL.

*Filename* i *numer wiersza* parametry są dostępne tylko podczas **_malloc_dbg —** została jawnie wywołana lub [_crtdbg_map_alloc —](../../c-runtime-library/crtdbg-map-alloc.md)stała preprocesora została zdefiniowana.

## <a name="return-value"></a>Wartość zwracana

Po pomyślnym ukończeniu ta funkcja zwraca wskaźnik do użytkownika części blok pamięci przydzielony, nowych funkcji programu obsługi lub zwraca wartość NULL. Pełny opis zwracany zachowania zobacz sekcję poniżej uwagi. Aby uzyskać więcej informacji o sposobie korzystania z nowych funkcji programu obsługi, zobacz [— funkcja malloc](malloc.md) funkcji.

## <a name="remarks"></a>Uwagi

**_malloc_dbg —** jest wersja debugowania [— funkcja malloc](malloc.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowana, każde wywołanie **_malloc_dbg —** zostanie zmniejszona do wywołania **— funkcja malloc**. Zarówno **— funkcja malloc** i **_malloc_dbg —** przydzielić bloku pamięci w stosie podstawowej, ale **_malloc_dbg —** oferuje kilka funkcji debugowania: buforów po obu stronach użytkownika część bloku do testowania przecieki, parametr typu bloku do śledzenia alokacji określonych typów, a *filename*/*numer wiersza* informacji do ustalenia pochodzenia żądań alokacji.

**_malloc_dbg —** przydziela bloku pamięci nieco więcej miejsca niż żądany *rozmiar*. Dodatkowe miejsce jest używane przez menedżera stosu debugowania, do łączenia bloków pamięci debugowania i do dostarczenia aplikacji informacji nagłówka debugowania i zastąpienia buforów. Gdy blok zostanie przydzielony, część użytkownika bloku jest wypełniania wartościami 0xCD a każdy bufor zastąpienia jest wypełniany wartościami 0xFD.

**_malloc_dbg —** ustawia **errno** do **enomem —** Jeśli alokacja pamięci nie powiedzie się lub jeśli przekracza ilość pamięci potrzebnej (łącznie z czynności wymienionych wcześniej) **_HEAP_ MAXREQ**. Aby uzyskać informacji dotyczących tego i innych kodów błędów, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Aby dowiedzieć się jak bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Informacje o typach bloku alokacji i sposobu ich używania, zobacz [typów bloków w stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje o różnicach między wywoływanie funkcji sterty standardowe i jego wersji do debugowania w kompilację debugowania aplikacji, zobacz [debugowania wersji z funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_malloc_dbg**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="example"></a>Przykład

Przykładowe zastosowania **_malloc_dbg —**, zobacz [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1).

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[malloc](malloc.md)<br/>
[_calloc_dbg](calloc-dbg.md)<br/>
[_calloc_dbg](calloc-dbg.md)<br/>
