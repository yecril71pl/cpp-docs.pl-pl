---
title: malloc
ms.date: 4/2/2020
api_name:
- malloc
- _o_malloc
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
- malloc
helpviewer_keywords:
- malloc function
- memory allocation
ms.assetid: 144fcee2-be34-4a03-bb7e-ed6d4b99eea0
ms.openlocfilehash: afe9264351110bc062d6168ef803fa6fb796538a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341577"
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

**malloc** zwraca wskaźnik void do przydzielonego miejsca lub **NULL,** jeśli nie ma wystarczającej ilości pamięci. Aby przywrócić wskaźnik do typu innego niż **void**, należy użyć typu rzutowego na zwracaną wartość. Miejsce do magazynowania wskazane przez wartość zwracaną jest gwarantowane odpowiednio wyrównane do przechowywania dowolnego typu obiektu, który ma wymóg wyrównania mniejszy lub równy z podstawowym wyrównaniem. (W języku Visual C++ wyrównanie podstawowe jest wyrównanie, które jest wymagane dla **double**, lub 8 bajtów. W kodzie przeznaczonym dla platform 64-bitowych jest to 16 bajtów.) Użyj [_aligned_malloc,](aligned-malloc.md) aby przydzielić magazyn dla obiektów, które mają większe wymagania dotyczące wyrównania — na przykład typy `__declspec(align( n ))` SSE [__m128](../../cpp/m128.md) i **__m256**oraz typy, które są zadeklarowane przy użyciu **n** jest większa niż 8. Jeśli *rozmiar* wynosi 0, **malloc** przydziela element o zerowej długości w stosie i zwraca prawidłowy wskaźnik do tego elementu. Zawsze sprawdzaj zwrot z **malloc**, nawet jeśli ilość żądanej pamięci jest mała.

## <a name="remarks"></a>Uwagi

Funkcja **malloc** przydziela blok pamięci o co najmniej *rozmiarze* bajtów. Blok może być większy niż *bajty rozmiaru* ze względu na miejsce, które jest wymagane do wyrównania i konserwacji informacji.

**malloc** ustawia **errno** na **ENOMEM,** jeśli alokacja pamięci nie powiedzie się lub jeśli ilość żądanej pamięci przekracza **_HEAP_MAXREQ**. Aby uzyskać informacje na temat tego i innych kodów błędów, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Kod startowy używa **malloc** do przydzielania magazynu dla **zmiennych _environ**, *envp*i *argv.* Następujące funkcje i ich odpowiedniki o szerokich znakach również nazywają **malloc**.

|||||
|-|-|-|-|
|[calloc](calloc.md)|[fscanf](fscanf-fscanf-l-fwscanf-fwscanf-l.md)|[_getw](getw.md)|[setvbuf](setvbuf.md)|
|[funkcje _exec](../../c-runtime-library/exec-wexec-functions.md)|[Fseek](fseek-fseeki64.md)|[_popen](popen-wpopen.md)|[funkcje _spawn](../../c-runtime-library/spawn-wspawn-functions.md)|
|[fgetc ( fgetc )](fgetc-fgetwc.md)|[fsetpos](fsetpos.md)|[Printf](printf-printf-l-wprintf-wprintf-l.md)|[_strdup](strdup-wcsdup-mbsdup.md)|
|[_fgetchar](fgetc-fgetwc.md)|[_fullpath](fullpath-wfullpath.md)|[putc ( putc )](putc-putwc.md)|[system](system-wsystem.md)|
|[fgets](fgets-fgetws.md)|[fwrite](fwrite.md)|[putchar ( putchar )](putc-putwc.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[fprintf (druk)](fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[getc ( getc )](getc-getwc.md)|[_putenv](putenv-wputenv.md)|[ungetc (ungetc)](ungetc-ungetwc.md)|
|[fputc ( fputc )](fputc-fputwc.md)|[Getchar](getc-getwc.md)|[Stawia](puts-putws.md)|[vfprintf (właśc.](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|
|[_fputchar](fputc-fputwc.md)|[_getcwd](getcwd-wgetcwd.md)|[_putw](putw.md)|[vprintf (](vprintf-vprintf-l-vwprintf-vwprintf-l.md)|
|[fputs ( fputs )](fputs-fputws.md)|[_getdcwd](getcwd-wgetcwd.md)|[Scanf](scanf-scanf-l-wscanf-wscanf-l.md)||
|[fread](fread.md)|[efekty](../../c-runtime-library/gets-getws.md)|[_searchenv](searchenv-wsearchenv.md)||

Funkcja [_set_new_mode](set-new-mode.md) C++ ustawia nowy tryb obsługi dla **malloc**. Nowy tryb obsługi wskazuje, czy w przypadku awarii **malloc** ma wywołać nową procedurę obsługi zgodnie z [_set_new_handler](set-new-handler.md). Domyślnie **malloc** nie wywołać nową procedurę obsługi na niepowodzenie alokacji pamięci. Można zastąpić to domyślne zachowanie, tak aby, gdy **malloc** nie można przydzielić pamięci, **malloc** wywołuje nową procedurę obsługi w taki sam sposób, jak **nowy** operator robi, gdy nie powiedzie się z tego samego powodu. Aby zastąpić wartość domyślną, zadzwoń `_set_new_mode(1)` na początku programu lub połącz z NEWMODE. OBJ (patrz [Opcje łącza).](../../c-runtime-library/link-options.md)

Gdy aplikacja jest połączona z wersją debugowania bibliotek w czasie wykonywania języka C, **malloc** rozpoznaje [_malloc_dbg](malloc-dbg.md). Aby uzyskać więcej informacji na temat zarządzania stertą podczas procesu debugowania, zobacz [Szczegóły sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

**malloc** jest `__declspec(noalias)` `__declspec(restrict)`oznaczony i ; oznacza to, że funkcja jest gwarantowana, aby nie modyfikować zmiennych globalnych i że wskaźnik zwrócony nie jest aliasem. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczyć](../../cpp/restrict.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**malloc**|\<> i \<malloc.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek wyładowywowych języka C](../../c-runtime-library/crt-library-features.md).

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

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[Wolna](free.md)<br/>
[realloc](realloc.md)<br/>
[_aligned_malloc](aligned-malloc.md)<br/>
