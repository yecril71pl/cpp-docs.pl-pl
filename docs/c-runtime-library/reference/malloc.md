---
title: malloc | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- malloc
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
- malloc
dev_langs:
- C++
helpviewer_keywords:
- malloc function
- memory allocation
ms.assetid: 144fcee2-be34-4a03-bb7e-ed6d4b99eea0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 65b70ba6be4837a36d5987e60b1d7229134ceb99
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="malloc"></a>malloc
Przydziela bloki pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
void *malloc(  
   size_t size   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `size`  
 Liczba bajtów do przydzielenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 `malloc` Zwraca typ void wskaźnik do przydzielone miejsce, lub `NULL` Jeśli dostępnych jest za mało pamięci. Aby zwraca wskaźnik do typu innego niż `void`, użyj typu rzutowania wartości zwracanej. Miejsca do magazynowania wskazywanej przez wartość zwracana jest gwarantowana odpowiednio dopasowany do przechowywania dowolnego typu obiektu, który ma wyrównanie wymaganie mniej niż lub równa niż podstawowych wyrównania. (W programie Visual C++, podstawowe wyrównania jest wyrównania, która jest wymagana dla `double`, lub 8 bajtów. W kodzie, przeznaczonego dla platformy 64-bitowych jest 16 bajtów). Użyj [_aligned_malloc —](../../c-runtime-library/reference/aligned-malloc.md) Aby przydzielić magazyn dla obiektów, które mają większe wymagania wyrównania — na przykład typy SSE [__m128](../../cpp/m128.md) i `__m256`oraz typy, które są zadeklarowane za pomocą `__declspec(align( n ))`gdzie `n` jest większa niż 8. Jeśli `size` ma wartość 0, `malloc` przydziela elementu o zerowej długości w stercie i zwraca prawidłowego wskaźnika do elementu. Zawsze sprawdzaj powrót z `malloc`nawet wtedy, gdy jest mała ilość pamięci żądana.  
  
## <a name="remarks"></a>Uwagi  
 `malloc` Funkcja przydziela blok pamięci, co najmniej `size` bajtów. Blok może być większa niż `size` bajtów z powodu ilości miejsca, która wymaga informacji wyrównanie i konserwacji.  
  
 `malloc` Ustawia `errno` do `ENOMEM` czy alokacja pamięci nie powiedzie się, czy ilość pamięci żądana przekracza `_HEAP_MAXREQ`. Aby uzyskać informacji dotyczących tego i innych kodów błędów, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Kod uruchomienia używa `malloc` Aby przydzielić magazyn `_environ`, `envp`, i `argv` zmiennych. Następujące funkcje i ich odpowiedniki znaków dwubajtowych także wywołać `malloc`.  
  
|||||  
|-|-|-|-|  
|[calloc](../../c-runtime-library/reference/calloc.md)|[fscanf](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)|[_getw](../../c-runtime-library/reference/getw.md)|[setvbuf](../../c-runtime-library/reference/setvbuf.md)|  
|[_exec — funkcje](../../c-runtime-library/exec-wexec-functions.md)|[fseek](../../c-runtime-library/reference/fseek-fseeki64.md)|[_popen —](../../c-runtime-library/reference/popen-wpopen.md)|[_spawn — funkcje](../../c-runtime-library/spawn-wspawn-functions.md)|  
|[fgetc](../../c-runtime-library/reference/fgetc-fgetwc.md)|[fsetpos](../../c-runtime-library/reference/fsetpos.md)|[printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|[_strdup](../../c-runtime-library/reference/strdup-wcsdup-mbsdup.md)|  
|[_fgetchar](../../c-runtime-library/reference/fgetc-fgetwc.md)|[_fullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)|[putc](../../c-runtime-library/reference/putc-putwc.md)|[system](../../c-runtime-library/reference/system-wsystem.md)|  
|[fgets —](../../c-runtime-library/reference/fgets-fgetws.md)|[fwrite](../../c-runtime-library/reference/fwrite.md)|[putchar —](../../c-runtime-library/reference/putc-putwc.md)|[_tempnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|  
|[fprintf](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[getc](../../c-runtime-library/reference/getc-getwc.md)|[_putenv](../../c-runtime-library/reference/putenv-wputenv.md)|[ungetc](../../c-runtime-library/reference/ungetc-ungetwc.md)|  
|[fputc —](../../c-runtime-library/reference/fputc-fputwc.md)|[getchar](../../c-runtime-library/reference/getc-getwc.md)|[umieszcza](../../c-runtime-library/reference/puts-putws.md)|[vfprintf](../../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|  
|[_fputchar](../../c-runtime-library/reference/fputc-fputwc.md)|[_getcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)|[_putw](../../c-runtime-library/reference/putw.md)|[vprintf —](../../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|  
|[fputs —](../../c-runtime-library/reference/fputs-fputws.md)|[_getdcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)|[scanf](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)||  
|[fread](../../c-runtime-library/reference/fread.md)|[Pobiera](../../c-runtime-library/gets-getws.md)|[_searchenv](../../c-runtime-library/reference/searchenv-wsearchenv.md)||  
  
 C++ [_set_new_mode —](../../c-runtime-library/reference/set-new-mode.md) funkcja ustawia tryb obsługi nowych `malloc`. Nowy tryb obsługi wskazuje, czy w przypadku awarii, `malloc` jest wywołanie nowe procedury obsługi zgodnie z ustawieniami [_set_new_handler —](../../c-runtime-library/reference/set-new-handler.md). Domyślnie `malloc` nie wywołuje nowe procedury obsługi nie można przydzielić pamięci. Można zastąpić to zachowanie domyślne, aby, gdy `malloc` nie może przydzielić pamięci, `malloc` wywołuje nowe procedury obsługi tak samo jak robi `new` operator nie w przypadku niepowodzenia tego samego powodu. Aby zastąpić domyślną, należy wywołać `_set_new_mode(1)` wcześniej w program lub Połącz z biblioteką NEWMODE. OBJ (zobacz [opcje łącza](../../c-runtime-library/link-options.md)).  
  
 Gdy aplikacja jest połączony z wersją debugowania biblioteki wykonawcze języka C, `malloc` jest rozpoznawana jako [_malloc_dbg —](../../c-runtime-library/reference/malloc-dbg.md). Aby uzyskać więcej informacji dotyczących sposobu zarządzania infrastrukturą sterty podczas debugowania procesu, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 `malloc` jest oznaczony jako `__declspec(noalias)` i `__declspec(restrict)`; to oznacza, że funkcja jest gwarantowana nie do modyfikowania zmiennych globalnych i że zwracane wskaźnik nie jest używane z aliasem. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczyć](../../cpp/restrict.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`malloc`|\<stdlib.h > i \<malloc.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Przykład  
  
```C  
// crt_malloc.c  
// This program allocates memory with  
// malloc, then frees the memory with free.  
  
#include <stdlib.h>   // For _MAX_PATH definition  
#include <stdio.h>  
#include <malloc.h>  
  
int main( void )  
{  
   char *string;  
  
   // Allocate space for a path name  
   string = malloc( _MAX_PATH );  
  
   // In a C++ file, explicitly cast malloc's return.  For example,   
   // string = (char *)malloc( _MAX_PATH );  
  
   if( string == NULL )  
      printf( "Insufficient memory available\n" );  
   else  
   {  
      printf( "Memory space allocated for path name\n" );  
      free( string );  
      printf( "Memory freed\n" );  
   }  
}  
```  
  
```Output  
Memory space allocated for path name  
Memory freed  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Alokacja pamięci](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [W warstwie bezpłatna](../../c-runtime-library/reference/free.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md)
