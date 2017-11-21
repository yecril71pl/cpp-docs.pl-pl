---
title: "bezpłatne | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: free
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
f1_keywords: free
dev_langs: C++
helpviewer_keywords:
- memory blocks, deallocating
- free function
ms.assetid: 74ded9cf-1863-432e-9306-327a42080bb8
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 61d750fce6e31923636b4eb8c0181bf405b7be39
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="free"></a>free
Cofa alokację lub zwalnia blok pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
void free(   
   void *memblock   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `memblock`  
 Poprzednio przydzielony blok pamięci, które ma zostać zwolniony.  
  
## <a name="remarks"></a>Uwagi  
 `free` Funkcja zwalnia blok pamięci (`memblock`) wcześniej było przydzielone przez wywołanie do `calloc`, `malloc`, lub `realloc`. Liczba bajtów, gdy został przydzielony blok odpowiada liczba zwolnionych bajtów (lub przydzielone w odniesieniu `realloc`). Jeśli `memblock` jest `NULL`, wskaźnik jest ignorowany i `free` natychmiast zwraca. Próba zwolnienia nieprawidłowego wskaźnika (wskaźnik do bloku pamięci, który nie został przydzielony przez `calloc`, `malloc`, lub `realloc`) może wpłynąć na żądania alokacji kolejnych i spowodować błędy.  
  
 W przypadku wystąpienia błędu w zwolnić pamięć, `errno` ustawiono informacje z systemu operacyjnego od charakteru błędu. Aby uzyskać więcej informacji, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Po zwolnieniu blok pamięci, [_heapmin —](../../c-runtime-library/reference/heapmin.md) minimalizuje ilość wolnej pamięci na stercie łączenie nieużywane regionów, a ich zwolnienie do systemu operacyjnego. Zwolnionych pamięci, która nie jest zwalniany do systemu operacyjnego zostanie przywrócony do puli bezpłatnej i jest dostępne do alokacji ponownie.  
  
 Gdy aplikacja jest połączony z wersją debugowania biblioteki wykonawcze języka C, `free` jest rozpoznawana jako [_free_dbg —](../../c-runtime-library/reference/free-dbg.md). Aby uzyskać więcej informacji dotyczących sposobu zarządzania infrastrukturą sterty podczas debugowania procesu, zobacz [sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 `free`jest oznaczony jako `__declspec(noalias)`, co oznacza zagwarantowanie funkcji nie można modyfikować zmienne globalne. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md).  
  
 Aby zwolnić pamięć przydzielona z [_malloca —](../../c-runtime-library/reference/malloca.md), użyj [_freea —](../../c-runtime-library/reference/freea.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`free`|\<stdlib.h > i \<malloc.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [— funkcja malloc](../../c-runtime-library/reference/malloc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Alokacja pamięci](../../c-runtime-library/memory-allocation.md)   
 [_alloca](../../c-runtime-library/reference/alloca.md)   
 [calloc —](../../c-runtime-library/reference/calloc.md)   
 [— funkcja malloc](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [_free_dbg —](../../c-runtime-library/reference/free-dbg.md)   
 [_heapmin —](../../c-runtime-library/reference/heapmin.md)   
 [_freea —](../../c-runtime-library/reference/freea.md)