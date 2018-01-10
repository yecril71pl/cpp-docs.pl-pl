---
title: "_rozszerz lokację | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _expand
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
- _bexpand
- fexpand
- expand
- nexpand
- _fexpand
- _nexpand
- bexpand
- _expand
dev_langs: C++
helpviewer_keywords:
- memory blocks, changing size
- _expand function
- expand function
ms.assetid: 4ac55410-39c8-45c7-bccd-3f1042ae2ed3
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 103ff4077bdc68b8886c5181ce317b5c0d0d2b79
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="expand"></a>_expand
Zmienia rozmiar bloku pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
void *_expand(   
   void *memblock,  
   size_t size   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `memblock`  
 Wskaźnik do bloku wcześniej alokacji pamięci.  
  
 `size`  
 Nowy rozmiar w bajtach.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_expand`Zwraca typ void wskaźnik do bloku przydzielić pamięci. `_expand`, w odróżnieniu od `realloc`, nie można przenieść bloku, aby zmienić jego rozmiaru. W związku z tym, jeśli istnieje wystarczająca ilość pamięci rozwinąć blok bez przenoszenia go, `memblock` parametr `_expand` jest taka sama jak wartość zwracaną.  
  
 `_expand`Zwraca `NULL` gdy zostaje wykryty błąd podczas jego działania. Na przykład jeśli `_expand` jest używany do zmniejszania blok pamięci, go może wykrywać uszkodzenia w stercie niewielki blok lub bloku nieprawidłowy wskaźnik i zwracać `NULL`.  
  
 Jeśli jest za mało pamięci rozwinąć blok na dany rozmiar bez przenoszenia go, funkcja zwraca `NULL`. `_expand`nigdy nie zwraca blok rozszerzony do rozmiaru mniej niż żądana. Jeśli wystąpi błąd, `errno` wskazuje naturę niepowodzenia. Aby uzyskać więcej informacji na temat `errno`, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Wartości zwracanej wskazuje miejsce do magazynowania, które na pewno jest odpowiednio dopasowany do przechowywania obiekty dowolnego typu. Aby sprawdzić nowy rozmiar elementu, użyj `_msize`. Aby otrzymywać wskaźnik do typu innego niż `void`, użyj typu rzutowania wartości zwracanej.  
  
## <a name="remarks"></a>Uwagi  
 `_expand` Funkcja zmienia rozmiar bloku wcześniej alokacji pamięci próbując rozwiń lub Zwiń bloku bez przenoszenia jego lokalizacji w stosie. `memblock` Parametr wskazuje na początku bloku. `size` Parametru zapewnia nowy rozmiar bloku, w bajtach. Treść bloku nie uległy zmianie do krótszej z nowym i starym rozmiary. `memblock`nie może być blokiem został zwolniony.  
  
> [!NOTE]
>  Na platformach 64-bitowych `_expand` nie może być kontraktu bloku, jeśli nowy rozmiar jest mniejszy niż bieżący rozmiar; w szczególności, jeśli blok był mniejszy niż 16 KB, rozmiar i w związku z tym przydzielić w stercie fragmentacji małej `_expand` opuszcza blok bez zmian i Zwraca `memblock`.  
  
 Gdy aplikacja jest połączony z wersją debugowania biblioteki wykonawcze języka C, `_expand` jest rozpoznawana jako [_expand_dbg —](../../c-runtime-library/reference/expand-dbg.md). Aby uzyskać więcej informacji dotyczących sposobu zarządzania infrastrukturą sterty podczas debugowania procesu, zobacz [sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 Ta funkcja weryfikuje jego parametrów. Jeśli `memblock` jest wskaźnika o wartości null, funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `errno` ustawiono `EINVAL` i funkcja zwraca `NULL`. Jeśli `size` jest większa niż `_HEAP_MAXREQ`, `errno` ustawiono `ENOMEM` i funkcja zwraca `NULL`.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`_expand`|\<malloc.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_expand.c  
  
#include <stdio.h>  
#include <malloc.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   char *bufchar;  
   printf( "Allocate a 512 element buffer\n" );  
   if( (bufchar = (char *)calloc( 512, sizeof( char ) )) == NULL )  
      exit( 1 );  
   printf( "Allocated %d bytes at %Fp\n",   
         _msize( bufchar ), (void *)bufchar );  
   if( (bufchar = (char *)_expand( bufchar, 1024 )) == NULL )  
      printf( "Can't expand" );  
   else  
      printf( "Expanded block to %d bytes at %Fp\n",   
            _msize( bufchar ), (void *)bufchar );  
   // Free memory   
   free( bufchar );  
   exit( 0 );  
}  
```  
  
```Output  
Allocate a 512 element buffer  
Allocated 512 bytes at 002C12BC  
Expanded block to 1024 bytes at 002C12BC  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Alokacja pamięci](../../c-runtime-library/memory-allocation.md)   
 [calloc —](../../c-runtime-library/reference/calloc.md)   
 [w warstwie bezpłatna](../../c-runtime-library/reference/free.md)   
 [— funkcja malloc](../../c-runtime-library/reference/malloc.md)   
 [_msize —](../../c-runtime-library/reference/msize.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)