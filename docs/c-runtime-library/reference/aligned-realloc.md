---
title: "_aligned_realloc — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _aligned_realloc
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
dev_langs: C++
helpviewer_keywords:
- aligned_realloc function
- _aligned_realloc function
ms.assetid: 80ce96e8-6087-416f-88aa-4dbb8cb1d218
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 293e519cd107ef64d81d59f08cf7f8d4871e8e6a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="alignedrealloc"></a>_aligned_realloc
Zmienia rozmiar blok pamięci przydzielony przy [_aligned_malloc —](../../c-runtime-library/reference/aligned-malloc.md) lub [_aligned_offset_malloc —](../../c-runtime-library/reference/aligned-offset-malloc.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
void * _aligned_realloc(  
   void *memblock,   
   size_t size,   
   size_t alignment  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`memblock`  
 Bieżący wskaźnik bloku pamięci.  
  
 [in]`size`  
 Rozmiar alokacji żądanej pamięci.  
  
 [in]`alignment`  
 Wartość wyrównania, która musi być całkowitą potęgą liczby 2.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_aligned_realloc`Zwraca typ void wskaźnik do bloku pamięci przydzielić (i prawdopodobnie przenoszenia). Wartość zwracana jest `NULL` rozmiar wynosi zero, jeśli argument bufor nie jest `NULL`, lub jeśli nie ma dostatecznej ilości dostępnej pamięci, aby rozwinąć blok na dany rozmiar. W pierwszym przypadku oryginalnego bloku zostanie zwolniona. W ciągu sekundy oryginalnego bloku jest bez zmian. Wartości zwracanej wskazuje miejsce do magazynowania, które na pewno jest odpowiednio dopasowany do przechowywania obiekty dowolnego typu. Aby uzyskać wskaźnik do typu innego niż void, użyj typu rzutowania wartości zwracanej.  
  
 Jest błędem ponowne przydzielenie pamięci i zmienić wyrównania bloku.  
  
## <a name="remarks"></a>Uwagi  
 `_aligned_realloc`jest oparta na `malloc`. Aby uzyskać więcej informacji o korzystaniu z `_aligned_offset_malloc`, zobacz [— funkcja malloc](../../c-runtime-library/reference/malloc.md).  
  
 Ta funkcja ustawia `errno` na `ENOMEM` jeśli alokacja pamięci nie powiodła się lub jeśli żądany rozmiar był większy niż `_HEAP_MAXREQ`. Aby uzyskać więcej informacji na temat `errno`, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). `_aligned_realloc` również sprawdza poprawność parametrów. Jeśli `alignment` nie jest potęgą 2, ta funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, ta funkcja zwraca `NULL` i ustawia `errno` do `EINVAL`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_aligned_realloc`|\<malloc.h >|  
  
## <a name="example"></a>Przykład  
 Aby uzyskać więcej informacji, zobacz [_aligned_malloc —](../../c-runtime-library/reference/aligned-malloc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrównywanie danych](../../c-runtime-library/data-alignment.md)