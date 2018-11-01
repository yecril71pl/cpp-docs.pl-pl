---
title: _aligned_realloc
ms.date: 11/04/2016
apiname:
- _aligned_realloc
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
- _aligned_realloc
- aligned_realloc
helpviewer_keywords:
- aligned_realloc function
- _aligned_realloc function
ms.assetid: 80ce96e8-6087-416f-88aa-4dbb8cb1d218
ms.openlocfilehash: 456d57eeebfd47a2133b8a5813b11aaf77a300a4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607381"
---
# <a name="alignedrealloc"></a>_aligned_realloc

Zmienia rozmiar bloku pamięci, która została przydzielona za pomocą [_aligned_malloc](aligned-malloc.md) lub [_aligned_offset_malloc —](aligned-offset-malloc.md).

## <a name="syntax"></a>Składnia

```C
void * _aligned_realloc(
   void *memblock,
   size_t size,
   size_t alignment
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Wskaźnik bieżącego bloku pamięci.

*Rozmiar*<br/>
Rozmiar alokacji żądanej pamięci.

*Wyrównanie*<br/>
Wartość wyrównania, która musi być całkowitą potęgą liczby 2.

## <a name="return-value"></a>Wartość zwracana

**_aligned_realloc —** zwraca pusty wskaźnik do bloku pamięci ponownie przydzielane (i ewentualnie przenoszenia). Wartość zwracana jest **NULL** Jeśli rozmiar wynosi zero, a argument bufor nie jest **NULL**, lub jeśli nie jest za mało dostępnej pamięci, aby rozwinąć blok na dany rozmiar. W pierwszym przypadku oryginalnego bloku jest zwalniana. W drugim oryginalnym bloku ulega zmianie. Zwracana wartość wskazuje miejsce do magazynowania, który gwarantuje bycia odpowiednio wyrównaną do przechowywania dowolnego typu obiektu. Aby uzyskać wskaźnik do typu innego niż void, użyj typu rzutowanego na wartość zwracaną.

Jest to błąd, ponownego przydzielenia pamięci i zmienić wyrównanie bloku.

## <a name="remarks"></a>Uwagi

**_aligned_realloc —** opiera się na **— funkcja malloc**. Aby uzyskać więcej informacji o korzystaniu z **_aligned_offset_malloc —**, zobacz [— funkcja malloc](malloc.md).

Funkcja ta ustawia **errno** do **ENOMEM** Jeśli alokacja pamięci nie powiodła się lub Jeśli żądany rozmiar był większy niż **_heap_maxreq —**. Aby uzyskać więcej informacji na temat **errno**, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Ponadto **_aligned_realloc —** sprawdza poprawność parametrów. Jeśli *wyrównanie* nie jest potęgą 2, funkcja wywoła procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca **NULL** i ustawia **errno** do **EINVAL**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_aligned_realloc**|\<malloc.h>|

## <a name="example"></a>Przykład

Aby uzyskać więcej informacji, zobacz [_aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Zobacz także

[Wyrównywanie danych](../../c-runtime-library/data-alignment.md)<br/>
