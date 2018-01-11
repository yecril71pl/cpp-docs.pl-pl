---
title: "_freea — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _freea
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
- freea
- _freea
dev_langs: C++
helpviewer_keywords:
- _freea function
- freea function
- memory deallocation
ms.assetid: dcd30584-dd9d-443b-8c4c-13237a1cecac
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 921687fbc5d8ab0b509e5a2e43c9c9ff4b18727a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="freea"></a>_freea
Cofa alokację lub zwalnia blok pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
void _freea(   
   void *memblock   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `memblock`  
 Poprzednio przydzielony blok pamięci, które ma zostać zwolniony.  
  
## <a name="return-value"></a>Wartość zwracana  
 Brak.  
  
## <a name="remarks"></a>Uwagi  
 `_freea` Funkcja zwalnia blok pamięci (`memblock`) wcześniej było przydzielone przez wywołanie do [_malloca —](../../c-runtime-library/reference/malloca.md). `_freea`sprawdza, czy pamięć została przydzielona na stercie lub stosu. Jeśli został przydzielony na stosie, `_freea` nie działają. Jeśli został przydzielony na stosie, liczba zwolnionych bajtów jest odpowiednikiem liczbę bajtów, gdy został przydzielony blok. Jeśli `memblock` jest `NULL`, wskaźnik jest ignorowany i `_freea` natychmiast zwraca. Próba zwolnienia nieprawidłowego wskaźnika (wskaźnik do bloku pamięci, który nie został przydzielony przez `_malloca`) może wpłynąć na żądania alokacji kolejnych i spowodować błędy.  
  
 `_freea`wywołania `free` wewnętrznie, jeśli stwierdzi, że pamięć jest przydzielony na stosie. Stos jest określany przez znacznik czy pamięć jest na stercie umieszczane w pamięci pod adresem poprzedzającego alokacji pamięci.  
  
 W przypadku wystąpienia błędu w zwolnić pamięć, `errno` ustawiono informacje z systemu operacyjnego od charakteru błędu. Aby uzyskać więcej informacji, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Po zwolnieniu blok pamięci, [_heapmin —](../../c-runtime-library/reference/heapmin.md) minimalizuje ilość wolnej pamięci na stercie łączenie nieużywane regionów, a ich zwolnienie do systemu operacyjnego. Zwolnionych pamięci, która nie jest zwalniany do systemu operacyjnego zostanie przywrócony do puli bezpłatnej i jest dostępne do alokacji ponownie.  
  
 Wywołanie `_freea` musi towarzyszyć wszystkie wywołania `_malloca`. Istnieje również błąd do wywołania `_freea` dwukrotnie dla tej samej pamięci. Gdy aplikacja jest połączony z debugowania wersji biblioteki wykonawcze języka C, zwłaszcza w przypadku [_malloc_dbg —](../../c-runtime-library/reference/malloc-dbg.md) funkcje włączone, definiując `_CRTDBG_MAP_ALLOC`, łatwiej znaleźć brakujące lub zduplikowane wywołania `_freea`. Aby uzyskać więcej informacji dotyczących sposobu zarządzania infrastrukturą sterty podczas debugowania procesu, zobacz [sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 `_freea`jest oznaczony jako `__declspec(noalias)`, co oznacza zagwarantowanie funkcji nie można modyfikować zmienne globalne. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`_freea`|\<stdlib.h > i \<malloc.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [_malloca —](../../c-runtime-library/reference/malloca.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Alokacja pamięci](../../c-runtime-library/memory-allocation.md)   
 [_malloca —](../../c-runtime-library/reference/malloca.md)   
 [calloc —](../../c-runtime-library/reference/calloc.md)   
 [— funkcja malloc](../../c-runtime-library/reference/malloc.md)   
 [_malloc_dbg —](../../c-runtime-library/reference/malloc-dbg.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [_free_dbg —](../../c-runtime-library/reference/free-dbg.md)   
 [_heapmin](../../c-runtime-library/reference/heapmin.md)