---
title: _aligned_offset_malloc
ms.date: 11/04/2016
apiname:
- _aligned_offset_malloc
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _aligned_offset_malloc
- aligned_offset_malloc
helpviewer_keywords:
- _aligned_offset_malloc function
- aligned_offset_malloc function
ms.assetid: 447681a3-7c95-4655-86ba-fa3a4ca4c521
ms.openlocfilehash: 824edfd8bb96d805a030fb205dee62fa9eb4fd06
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644642"
---
# <a name="alignedoffsetmalloc"></a>_aligned_offset_malloc

Przydziela pamięć na określonej granicy wyrównania.

## <a name="syntax"></a>Składnia

```C
void * _aligned_offset_malloc(
   size_t size,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Rozmiar alokacji żądanej pamięci.

*Wyrównanie*<br/>
Wartość wyrównania, która musi być całkowitą potęgą liczby 2.

*offset*<br/>
Przesunięcie alokacji pamięci, aby wymusić wyrównanie.

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do bloku pamięci, która została przydzielona lub **NULL** Jeśli operacja nie powiodła się.

## <a name="remarks"></a>Uwagi

**_aligned_offset_malloc —** jest przydatne w sytuacjach, w których potrzebne jest wyrównanie na elemencie zagnieżdżonym; na przykład jeśli wyrównanie było potrzebne na klasie zagnieżdżonej.

**_aligned_offset_malloc —** opiera się na **— funkcja malloc**; Aby uzyskać więcej informacji, zobacz [— funkcja malloc](malloc.md).

**_aligned_offset_malloc —** jest oznaczony jako `__declspec(noalias)` i `__declspec(restrict)`, co oznacza, że funkcja daje gwarancję niemodyfikowania zmiennych globalnych i że zwrócony wskaźnik nie jest aliasem. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczyć](../../cpp/restrict.md).

Funkcja ta ustawia **errno** do **ENOMEM** Jeśli alokacja pamięci nie powiodła się lub Jeśli żądany rozmiar był większy niż **_heap_maxreq —**. Aby uzyskać więcej informacji na temat **errno**, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Ponadto **_aligned_offset_malloc —** sprawdza poprawność parametrów. Jeśli *wyrównanie* nie jest potęgą liczby 2 lub jeśli *przesunięcie* jest większa niż lub równa *rozmiar* i wartość różną od zera, funkcja wywoła procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [ Walidacja parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca **NULL** i ustawia **errno** do **EINVAL**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_aligned_offset_malloc**|\<malloc.h>|

## <a name="example"></a>Przykład

Aby uzyskać więcej informacji, zobacz [_aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Zobacz także

[Wyrównywanie danych](../../c-runtime-library/data-alignment.md)<br/>
