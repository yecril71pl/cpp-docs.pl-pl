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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 4e699920f37139be40542ba91b3740cd9edef148
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917512"
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

*size*<br/>
Bajty do przydzielenia.

## <a name="return-value"></a>Wartość zwracana

Funkcja **malloc** zwraca wskaźnik void do przydzieloną miejsce lub **wartość null** , jeśli jest za mało dostępnej pamięci. Aby zwrócić wskaźnik do typu innego niż **void**, należy użyć rzutowania typu dla zwracanej wartości. Miejsce do magazynowania wskazywane przez wartość zwracaną jest gwarantowane odpowiednio wyrównane do przechowywania dowolnego typu obiektu, który ma wymaganie wyrównania mniejsze niż lub równe podstawowemu wyrównaniu. (W Visual C++ podstawowe wyrównanie jest wyrównaniem wymaganym przez **podwójny**lub 8 bajtów. W kodzie, który jest przeznaczony dla platform 64-bitowych, wynosi 16 bajtów. Użyj [_aligned_malloc](aligned-malloc.md) , aby przydzielić magazyn dla obiektów, które mają większe wymagania dotyczące wyrównania — na przykład typy SSE [__m128](../../cpp/m128.md) i **__m256**oraz typy, które są zadeklarowane za pomocą `__declspec(align( n ))` gdzie **n** jest większy niż 8. Jeśli *rozmiar* wynosi 0, **malloc** przypisuje element o zerowej długości w stercie i zwraca prawidłowy wskaźnik do tego elementu. Zawsze sprawdzaj poprawność funkcji **malloc**, nawet jeśli żądana ilość pamięci jest mała.

## <a name="remarks"></a>Uwagi

Funkcja **malloc** przypisuje blok pamięci o *rozmiarze* co najmniej bajtów. Blok może być większy niż *rozmiar* bajtów ze względu na miejsce, które jest wymagane do wyrównania i konserwacji.

Funkcja **malloc** ustawia **errno** do **ENOMEM** , jeśli alokacja pamięci nie powiedzie się lub jeśli żądana ilość pamięci przekroczy **_HEAP_MAXREQ**. Aby uzyskać informacje o tym i innych kodach błędów, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Kod uruchamiania używa usługi **malloc** do przydzielania pamięci dla zmiennych **_environ**, *envp*i *argv* . Następujące funkcje i ich odpowiedniki znakowe są również wywołaniem **malloc**.

|||||
|-|-|-|-|
|[calloc](calloc.md)|[fscanf](fscanf-fscanf-l-fwscanf-fwscanf-l.md)|[_getw](getw.md)|[setvbuf](setvbuf.md)|
|[funkcje _exec](../../c-runtime-library/exec-wexec-functions.md)|[fseek](fseek-fseeki64.md)|[_popen](popen-wpopen.md)|[funkcje _spawn](../../c-runtime-library/spawn-wspawn-functions.md)|
|[fgetc](fgetc-fgetwc.md)|[fsetpos](fsetpos.md)|[printf](printf-printf-l-wprintf-wprintf-l.md)|[_strdup](strdup-wcsdup-mbsdup.md)|
|[_fgetchar](fgetc-fgetwc.md)|[_fullpath](fullpath-wfullpath.md)|[putc](putc-putwc.md)|[system](system-wsystem.md)|
|[fgets](fgets-fgetws.md)|[fwrite](fwrite.md)|[putchar](putc-putwc.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[fprintf —](fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[getc —](getc-getwc.md)|[_putenv](putenv-wputenv.md)|[ungetc —](ungetc-ungetwc.md)|
|[fputc](fputc-fputwc.md)|[GetChar](getc-getwc.md)|[sumaryczn](puts-putws.md)|[vfprintf](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|
|[_fputchar](fputc-fputwc.md)|[_getcwd](getcwd-wgetcwd.md)|[_putw](putw.md)|[vprintf —](vprintf-vprintf-l-vwprintf-vwprintf-l.md)|
|[fputs](fputs-fputws.md)|[_getdcwd](getcwd-wgetcwd.md)|[scanf](scanf-scanf-l-wscanf-wscanf-l.md)||
|[fread](fread.md)|[kto](../../c-runtime-library/gets-getws.md)|[_searchenv](searchenv-wsearchenv.md)||

Funkcja C++ [_set_new_mode](set-new-mode.md) ustawia nowy tryb obsługi dla opcji **malloc**. Nowy tryb obsługi wskazuje, czy w przypadku niepowodzenia, **malloc** ma wywołać nową procedurę obsługi jako ustawioną przez [_set_new_handler](set-new-handler.md). Domyślnie funkcja **malloc** nie wywołuje nowej procedury obsługi w przypadku niepowodzenia przydzielenia pamięci. Można zastąpić to zachowanie domyślne, tak aby w przypadku niepowodzenia przydzielenia pamięci przez funkcję **malloc** wywołuje nową procedurę obsługi w taki sam **sposób, w** jaki operator **New** wykonuje, gdy nie powiedzie się z tego samego powodu. Aby zastąpić wartość domyślną, wywołaj `_set_new_mode(1)` wczesne w programie lub Połącz z NEWMODE. OBJ (zobacz [Opcje linku](../../c-runtime-library/link-options.md)).

Gdy aplikacja jest połączona z wersją debugową bibliotek uruchomieniowych C, funkcja **malloc** rozwiązuje [_malloc_dbg](malloc-dbg.md). Aby uzyskać więcej informacji na temat sposobu zarządzania stertą w procesie debugowania, zobacz [szczegóły sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

Funkcja **malloc** jest `__declspec(noalias)` oznaczona `__declspec(restrict)`i; oznacza to, że funkcja nie modyfikuje zmiennych globalnych i że zwrócony wskaźnik nie jest aliasem. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczaj](../../cpp/restrict.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**malloc**|\<STDLIB. h> i \<malloc. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

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
[zwolniony](free.md)<br/>
[realloc](realloc.md)<br/>
[_aligned_malloc](aligned-malloc.md)<br/>
