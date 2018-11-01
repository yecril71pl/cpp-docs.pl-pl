---
title: _aligned_msize
ms.date: 11/04/2016
apiname:
- _aligned_msize
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
- _aligned_msize
- aligned_msize
helpviewer_keywords:
- aligned_msize function
- _aligned_msize function
ms.assetid: 10995edc-2110-4212-9ca9-5e0220a464f4
ms.openlocfilehash: 97c739eed1f54f0c6705d37542eb13c6ec6879d2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50524878"
---
# <a name="alignedmsize"></a>_aligned_msize

Zwraca rozmiar bloku pamięci przydzielone w stosie.

## <a name="syntax"></a>Składnia

```C
size_t _msize(
   void *memblock,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Wskaźnik do bloku pamięci.

*Wyrównanie*<br/>
Wartość wyrównania, która musi być całkowitą potęgą liczby 2.

*offset*<br/>
Przesunięcie alokacji pamięci, aby wymusić wyrównanie.

## <a name="return-value"></a>Wartość zwracana

Zwraca rozmiar (w bajtach) jako liczbę całkowitą bez znaku.

## <a name="remarks"></a>Uwagi

**_Aligned_msize —** funkcja zwraca rozmiar w bajtach, blok pamięci przydzielonej przez wywołanie [_aligned_malloc](aligned-malloc.md) lub [_aligned_realloc —](aligned-realloc.md). *Wyrównanie* i *przesunięcie* wartości muszą być takie same jak wartość przekazana do funkcji, która przydzielona bloku.

Gdy aplikacja jest połączona z wersji debugowania bibliotek uruchomieniowych C, **_aligned_msize —** jest rozpoznawana jako [_aligned_msize_dbg](aligned-msize-dbg.md). Aby uzyskać więcej informacji na temat sposobu zarządzania stosem podczas debugowania, zobacz [sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

Ta funkcja sprawdza poprawność swojego parametru. Jeśli *memblock* jest pustym wskaźnikiem lub *wyrównanie* nie jest potęgą liczby 2, **_msize —** wywołuje program obsługi nieprawidłowego parametru, zgodnie z opisem w [Walidacja parametru ](../../c-runtime-library/parameter-validation.md). Jeśli obsługiwany jest błąd, funkcja ustawia **errno** do **EINVAL** i zwraca wartość -1.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_msize**|\<malloc.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
