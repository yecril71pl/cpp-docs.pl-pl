---
title: "_aligned_malloc — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _aligned_malloc
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
- _aligned_malloc
- alligned_malloc
dev_langs: C++
helpviewer_keywords:
- aligned_malloc function
- _aligned_malloc function
ms.assetid: fb788d40-ee94-4039-aa4d-97d73dab1ca0
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e7e16801bed2063d60e9151e2afc22a128aeed97
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="alignedmalloc"></a>_aligned_malloc
Przydziela pamięć na określonej granicy wyrównania.  
  
## <a name="syntax"></a>Składnia  
  
```  
void * _aligned_malloc(  
    size_t size,   
    size_t alignment  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `size`  
 Rozmiar żądanej alokacji pamięci.  
  
 `alignment`  
 Wartość wyrównania, która musi być całkowitą potęgą liczby 2.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do bloku pamięci, która została przydzielona lub `NULL` Jeśli działanie nie powiodło się. Wskaźnik jest wielokrotnością liczby `alignment`.  
  
## <a name="remarks"></a>Uwagi  
 `_aligned_malloc`jest oparta na [— funkcja malloc](../../c-runtime-library/reference/malloc.md).  
  
 `_aligned_malloc`jest oznaczony jako `__declspec(noalias)` i `__declspec(restrict)`, co oznacza zagwarantowanie funkcji nie można modyfikować zmienne globalne i czy wskaźnik zwrócone, nie jest używane z aliasem. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczyć](../../cpp/restrict.md).  
  
 Ta funkcja ustawia `errno` na `ENOMEM` jeśli alokacja pamięci nie powiodła się lub jeśli żądany rozmiar był większy niż `_HEAP_MAXREQ`. Aby uzyskać więcej informacji na temat `errno`, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). `_aligned_malloc` również sprawdza poprawność parametrów. Jeśli `alignment` nie jest potęgą liczby 2 lub `size` wynosi zero, ta funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, ta funkcja zwraca `NULL` i ustawia `errno` do `EINVAL`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_aligned_malloc`|\<malloc.h >|  
  
## <a name="example"></a>Przykład  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Wyrównywanie danych](../../c-runtime-library/data-alignment.md)