---
title: _aligned_offset_malloc
ms.date: 4/2/2020
api_name:
- _aligned_offset_malloc
- _o__aligned_offset_malloc
api_location:
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _aligned_offset_malloc
- aligned_offset_malloc
helpviewer_keywords:
- _aligned_offset_malloc function
- aligned_offset_malloc function
ms.assetid: 447681a3-7c95-4655-86ba-fa3a4ca4c521
ms.openlocfilehash: 1f13afbab75d2926d1c642c1430a3ffe5ecbac8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350587"
---
# <a name="_aligned_offset_malloc"></a>_aligned_offset_malloc

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

*Przesunięcie*<br/>
Przesunięcie alokacji pamięci, aby wymusić wyrównanie.

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do bloku pamięci, który został przydzielony lub **NULL,** jeśli operacja nie powiodła się.

## <a name="remarks"></a>Uwagi

**_aligned_offset_malloc** jest przydatne w sytuacjach, gdy wyrównanie jest potrzebne na element zagnieżdżony; na przykład, jeśli wyrównanie było potrzebne w klasie zagnieżdżonej.

**_aligned_offset_malloc** opiera się na **malloc**; aby uzyskać więcej informacji, zobacz [malloc](malloc.md).

**_aligned_offset_malloc** jest oznaczony `__declspec(noalias)` `__declspec(restrict)`i , co oznacza, że funkcja jest gwarantowana nie modyfikować zmiennych globalnych i że wskaźnik zwrócony nie jest aliasem. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczyć](../../cpp/restrict.md).

Ta funkcja ustawia **errno** na **ENOMEM,** jeśli alokacja pamięci nie powiodła się lub żądany rozmiar był większy niż **_HEAP_MAXREQ**. Aby uzyskać więcej informacji o **errno**, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Ponadto **_aligned_offset_malloc** sprawdza poprawność jego parametrów. Jeśli *wyrównanie* nie jest potęgą 2 lub jeśli *przesunięcie* jest większe lub równe *rozmiarowi* i niezerowej, ta funkcja wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w [zatwierdzeniu parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, ta funkcja zwraca **wartość NULL** i ustawia **errno** na **wartość EINVAL**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_aligned_offset_malloc**|\<> malloc.h|

## <a name="example"></a>Przykład

Aby uzyskać więcej informacji, zobacz [_aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Zobacz też

[Wyrównywanie danych](../../c-runtime-library/data-alignment.md)<br/>
