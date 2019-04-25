---
title: malloc
ms.date: 11/04/2016
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
helpviewer_keywords:
- malloc function
- memory allocation
ms.assetid: 144fcee2-be34-4a03-bb7e-ed6d4b99eea0
ms.openlocfilehash: e6a007fb6f089ebf1c9f5fc9ce59cbcbf0b13888
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157181"
---
# <a name="malloc"></a>malloc

Przydziela bloki pamięci.

## <a name="syntax"></a>Składnia

```C
void *malloc(
   size_t size
);
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Bajty do przydzielenia.

## <a name="return-value"></a>Wartość zwracana

**malloc** zwraca pusty wskaźnik do przydzielonego miejsca lub **NULL** Jeśli dostępnych jest za mało pamięci. Aby zwrócić wskaźnik do typu innego niż **void**, użyj typu rzutowanego na wartość zwracaną. Miejsca do magazynowania wskazywany przez wartość zwracana jest gwarantowane do bycia odpowiednio wyrównaną do przechowywania dowolnego typu obiektu, którego wymóg wyrównania jest mniejsza niż lub równe, wyrównanie podstawowe. (W programie Visual C++ podstawowe jest wyrównanie, które jest wymagane dla **double**, lub 8 bajtów. W kodzie, który jest przeznaczony dla platform 64-bitowy to 16 bajtów.) Użyj [_aligned_malloc](aligned-malloc.md) do przydzielania pamięci dla obiektów, które mają większe wymagania dotyczące wyrównania — na przykład typy SSE [__m128](../../cpp/m128.md) i **__m256**oraz typy, które są zadeklarowane za pomocą `__declspec(align( n ))` gdzie **n** jest większa niż 8. Jeśli *rozmiar* ma wartość 0, **— funkcja malloc** przydziela element o zerowej długości w stosie i zwraca prawidłowy wskaźnik do tego elementu. Zawsze sprawdzaj zwrot z **— funkcja malloc**, nawet jeśli żądana ilość pamięci jest mała.

## <a name="remarks"></a>Uwagi

**— Funkcja malloc** funkcja przydziela blok pamięci wielkości co najmniej *rozmiar* bajtów. Blok może być większa niż *rozmiar* bajtów ze względu na miejsce, które są wymagane do wyrównania i konserwacji informacji.

**malloc** ustawia **errno** do **ENOMEM** Jeśli alokacja pamięci nie powiedzie się lub Jeśli żądana ilość pamięci, przekracza **_heap_maxreq —**. Aby uzyskać informacji na temat tego i innych kodów błędu, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Kod startowy używa **— funkcja malloc** do przydzielania pamięci dla **_environ**, *envp*, i *argv* zmiennych. Następujące funkcje i ich odpowiedniki o znakach szerokich również wywołują **— funkcja malloc**.

|||||
|-|-|-|-|
|[calloc](calloc.md)|[fscanf —](fscanf-fscanf-l-fwscanf-fwscanf-l.md)|[_getw](getw.md)|[setvbuf](setvbuf.md)|
|[Funkcje _exec](../../c-runtime-library/exec-wexec-functions.md)|[fseek](fseek-fseeki64.md)|[_popen](popen-wpopen.md)|[_spawn — funkcje](../../c-runtime-library/spawn-wspawn-functions.md)|
|[fgetc](fgetc-fgetwc.md)|[fsetpos](fsetpos.md)|[printf](printf-printf-l-wprintf-wprintf-l.md)|[_strdup](strdup-wcsdup-mbsdup.md)|
|[_fgetchar](fgetc-fgetwc.md)|[_fullpath](fullpath-wfullpath.md)|[putc](putc-putwc.md)|[system](system-wsystem.md)|
|[fgets](fgets-fgetws.md)|[fwrite](fwrite.md)|[putchar](putc-putwc.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[fprintf —](fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[getc](getc-getwc.md)|[_putenv](putenv-wputenv.md)|[ungetc](ungetc-ungetwc.md)|
|[fputc](fputc-fputwc.md)|[getchar](getc-getwc.md)|[umieszcza](puts-putws.md)|[vfprintf](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|
|[_fputchar](fputc-fputwc.md)|[_getcwd](getcwd-wgetcwd.md)|[_putw](putw.md)|[vprintf](vprintf-vprintf-l-vwprintf-vwprintf-l.md)|
|[fputs —](fputs-fputws.md)|[_getdcwd](getcwd-wgetcwd.md)|[scanf](scanf-scanf-l-wscanf-wscanf-l.md)||
|[fread](fread.md)|[Pobiera](../../c-runtime-library/gets-getws.md)|[_searchenv](searchenv-wsearchenv.md)||

C++ [_Set_new_mode](set-new-mode.md) funkcja Ustawia nowy tryb obsługi dla **— funkcja malloc**. Nowy tryb obsługi wskazuje, czy w przypadku awarii, **— funkcja malloc** ma wywoływać nową procedurę obsługi zgodnie z ustawieniem [_set_new_handler](set-new-handler.md). Domyślnie **— funkcja malloc** nie wywołuje nowej procedury obsługi awarii w celu przydzielenia pamięci. Można zastąpić to zachowanie domyślne tak, aby, gdy **— funkcja malloc** nie może przydzielić pamięci, **— funkcja malloc** wywoła nową procedurę obsługi w taki sam sposób **nowe** jest operator Jeśli jej nie powiedzie się z tego samego powodu. Aby zastąpić domyślne, wywołaj `_set_new_mode(1)` wcześniej program, lub Połącz z biblioteką NEWMODE. OBJ (zobacz [opcje łącza](../../c-runtime-library/link-options.md)).

Gdy aplikacja jest połączona z wersji debugowania bibliotek uruchomieniowych C, **— funkcja malloc** jest rozpoznawana jako [_malloc_dbg](malloc-dbg.md). Aby uzyskać więcej informacji na temat sposobu zarządzania stosem podczas debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

**malloc** jest oznaczony jako `__declspec(noalias)` i `__declspec(restrict)`; oznacza to, że funkcja daje gwarancję niemodyfikowania zmiennych globalnych i że zwrócony wskaźnik nie jest aliasem. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczyć](../../cpp/restrict.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**malloc**|\<stdlib.h> and \<malloc.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
[_aligned_malloc](aligned-malloc.md)<br/>
