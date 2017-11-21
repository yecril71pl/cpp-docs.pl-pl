---
title: "_aligned_offset_malloc — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _aligned_offset_malloc
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
dev_langs: C++
helpviewer_keywords:
- _aligned_offset_malloc function
- aligned_offset_malloc function
ms.assetid: 447681a3-7c95-4655-86ba-fa3a4ca4c521
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7322f5a3fbf7bf3d9352181a68db17fad4bc9fcb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="alignedoffsetmalloc"></a>_aligned_offset_malloc
Przydziela pamięć na określonej granicy wyrównania.  
  
## <a name="syntax"></a>Składnia  
  
```  
void * _aligned_offset_malloc(  
   size_t size,   
   size_t alignment,   
   size_t offset  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`size`  
 Rozmiar alokacji żądanej pamięci.  
  
 [in]`alignment`  
 Wartość wyrównania, która musi być całkowitą potęgą liczby 2.  
  
 [in]`offset`  
 Przesunięcie alokacji pamięci, aby wymusić wyrównanie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do bloku pamięci, która została przydzielona lub `NULL` Jeśli działanie nie powiodło się.  
  
## <a name="remarks"></a>Uwagi  
 `_aligned_offset_malloc` jest użyteczne w sytuacjach, w których potrzebne jest wyrównanie na elemencie zagnieżdżonym, na przykład jeśli wyrównanie było potrzebne na klasie zagnieżdżonej.  
  
 `_aligned_offset_malloc`jest oparta na `malloc`; Aby uzyskać więcej informacji, zobacz [— funkcja malloc](../../c-runtime-library/reference/malloc.md).  
  
 `_aligned_offset_malloc`jest oznaczony jako `__declspec(noalias)` i `__declspec(restrict)`, co oznacza zagwarantowanie funkcji nie można modyfikować zmienne globalne i czy wskaźnik zwrócone, nie jest używane z aliasem. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczyć](../../cpp/restrict.md).  
  
 Ta funkcja ustawia `errno` na `ENOMEM` jeśli alokacja pamięci nie powiodła się lub jeśli żądany rozmiar był większy niż `_HEAP_MAXREQ`. Aby uzyskać więcej informacji na temat `errno`, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). `_aligned_offset_malloc` również sprawdza poprawność parametrów. Jeśli `alignment` nie jest potęgą liczby 2 lub, jeśli `offset` jest większa niż lub równa `size` i różną od zera, ta funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, ta funkcja zwraca `NULL` i ustawia `errno` do `EINVAL`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_aligned_offset_malloc`|\<malloc.h >|  
  
## <a name="example"></a>Przykład  
 Aby uzyskać więcej informacji, zobacz [_aligned_malloc —](../../c-runtime-library/reference/aligned-malloc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrównywanie danych](../../c-runtime-library/data-alignment.md)