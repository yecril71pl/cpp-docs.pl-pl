---
title: _aligned_malloc
ms.date: 12/11/2019
api_name:
- _aligned_malloc
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _aligned_malloc
- alligned_malloc
helpviewer_keywords:
- aligned_malloc function
- _aligned_malloc function
ms.assetid: fb788d40-ee94-4039-aa4d-97d73dab1ca0
ms.openlocfilehash: c06c822ae4e7584a172c260a5c06e25019a1ce5e
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300134"
---
# <a name="_aligned_malloc"></a>_aligned_malloc

Przydziela pamięć na określonej granicy wyrównania.

## <a name="syntax"></a>Składnia

```C
void * _aligned_malloc(
    size_t size,
    size_t alignment
);
```

### <a name="parameters"></a>Parametry

*zmienia*<br/>
Rozmiar żądanego przydziału pamięci.

*struktury*<br/>
Wartość wyrównania, która musi być całkowitą potęgą liczby 2.

## <a name="return-value"></a>Wartość zwrócona

Wskaźnik do bloku pamięci, który został przydzielony lub ma wartość NULL, jeśli operacja nie powiodła się. Wskaźnik jest wielokrotnością *wyrównania*.

## <a name="remarks"></a>Uwagi

**_aligned_malloc** jest oparty na [malloc](malloc.md).

**_aligned_malloc** jest oznaczona `__declspec(noalias)` i `__declspec(restrict)`, co oznacza, że funkcja nie modyfikuje zmiennych globalnych i że zwrócony wskaźnik nie ma aliasu. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczaj](../../cpp/restrict.md).

Ta funkcja ustawia `errno` na `ENOMEM` jeśli alokacja pamięci nie powiodła się lub jeśli żądany rozmiar był większy niż `_HEAP_MAXREQ`. Aby uzyskać więcej informacji na temat `errno`, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Ponadto **_aligned_malloc** sprawdza poprawność jego parametrów. Jeśli *wyrównanie* *nie jest potęgą 2 lub ma* wartość zero, ta funkcja wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja zwraca wartość NULL i ustawia `errno` na `EINVAL`.

Użyj [_aligned_free](aligned-free.md) , aby cofnąć alokację pamięci uzyskaną przez **_aligned_malloc** i `_aligned_offset_malloc`. Nie używaj `free`, które nie odzyska prawidłowo wyrównanej pamięci i może prowadzić do wypróbowania błędów.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_aligned_malloc**|\<malloc.h>|

## <a name="example"></a>Przykład

```C
// crt_aligned_malloc.c

#include <malloc.h>
#include <stdio.h>

int main() {
    void    *ptr;
    size_t  alignment,
            off_set;

    // Note alignment should be 2^N where N is any positive int.
    alignment = 16;
    off_set = 5;

    // Using _aligned_malloc
    ptr = _aligned_malloc(100, alignment);
    if (ptr == NULL)
    {
        printf_s( "Error allocation aligned memory.");
        return -1;
    }
    if (((unsigned long long)ptr % alignment ) == 0)
        printf_s( "This pointer, %p, is aligned on %zu\n",
                  ptr, alignment);
    else
        printf_s( "This pointer, %p, is not aligned on %zu\n",
                  ptr, alignment);

    // Using _aligned_realloc
    ptr = _aligned_realloc(ptr, 200, alignment);
    if ( ((unsigned long long)ptr % alignment ) == 0)
        printf_s( "This pointer, %p, is aligned on %zu\n",
                  ptr, alignment);
    else
        printf_s( "This pointer, %p, is not aligned on %zu\n",
                  ptr, alignment);
    _aligned_free(ptr);

    // Using _aligned_offset_malloc
    ptr = _aligned_offset_malloc(200, alignment, off_set);
    if (ptr == NULL)
    {
        printf_s( "Error allocation aligned offset memory.");
        return -1;
    }
    if ( ( (((unsigned long long)ptr) + off_set) % alignment ) == 0)
        printf_s( "This pointer, %p, is offset by %zu on alignment of %zu\n",
                  ptr, off_set, alignment);
    else
        printf_s( "This pointer, %p, does not satisfy offset %zu "
                  "and alignment %zu\n",ptr, off_set, alignment);

    // Using _aligned_offset_realloc
    ptr = _aligned_offset_realloc(ptr, 200, alignment, off_set);
    if (ptr == NULL)
    {
        printf_s( "Error reallocation aligned offset memory.");
        return -1;
    }
    if ( ( (((unsigned long long)ptr) + off_set) % alignment ) == 0)
        printf_s( "This pointer, %p, is offset by %zu on alignment of %zu\n",
                  ptr, off_set, alignment);
    else
        printf_s( "This pointer, %p, does not satisfy offset %zu and "
                  "alignment %zu\n", ptr, off_set, alignment);

    // Note that _aligned_free works for both _aligned_malloc
    // and _aligned_offset_malloc. Using free is illegal.
    _aligned_free(ptr);
}
```

```Output
This pointer, 3280880, is aligned on 16
This pointer, 3280880, is aligned on 16
This pointer, 3280891, is offset by 5 on alignment of 16
This pointer, 3280891, is offset by 5 on alignment of 16
```

## <a name="see-also"></a>Zobacz także

[Wyrównywanie danych](../../c-runtime-library/data-alignment.md)
