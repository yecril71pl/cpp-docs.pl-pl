---
title: malloc | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f600deb7bfa9b65ed9bdf784f2a16bd037729a51
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405526"
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
Liczba bajtów do przydzielenia.

## <a name="return-value"></a>Wartość zwracana

**malloc** zwraca typ void wskaźnik do przydzielone miejsce, lub **NULL** Jeśli dostępnych jest za mało pamięci. Aby zwraca wskaźnik do typu innego niż **void**, użyj typu rzutowania wartości zwracanej. Miejsca do magazynowania wskazywanej przez wartość zwracana jest gwarantowana odpowiednio dopasowany do przechowywania dowolnego typu obiektu, który ma wyrównanie wymaganie mniej niż lub równa niż podstawowych wyrównania. (W programie Visual C++, podstawowe wyrównania jest wyrównania, która jest wymagana dla **podwójne**, lub 8 bajtów. W kodzie, przeznaczonego dla platformy 64-bitowych jest 16 bajtów). Użyj [_aligned_malloc —](aligned-malloc.md) Aby przydzielić magazyn dla obiektów, które mają większe wymagania wyrównania — na przykład typy SSE [__m128](../../cpp/m128.md) i **__m256**oraz typy, które są zadeklarowana przy użyciu `__declspec(align( n ))` gdzie **n** jest większa niż 8. Jeśli *rozmiar* ma wartość 0, **— funkcja malloc** przydziela elementu o zerowej długości w stercie i zwraca prawidłowego wskaźnika do elementu. Zawsze sprawdzaj powrót z **— funkcja malloc**nawet wtedy, gdy jest mała ilość pamięci żądana.

## <a name="remarks"></a>Uwagi

**— Funkcja malloc** funkcja przydziela blok pamięci, co najmniej *rozmiar* bajtów. Blok może być większy niż *rozmiar* bajtów z powodu ilości miejsca, która wymaga informacji wyrównanie i konserwacji.

**malloc** ustawia **errno** do **enomem —** czy alokacja pamięci nie powiedzie się, czy ilość pamięci żądana przekracza **_heap_maxreq —**. Aby uzyskać informacji dotyczących tego i innych kodów błędów, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Kod uruchomienia używa **— funkcja malloc** Aby przydzielić magazyn **_environ —**, *envp —*, i *ARGV —* zmiennych. Następujące funkcje i ich odpowiedniki znaków dwubajtowych także wywołać **— funkcja malloc**.

|||||
|-|-|-|-|
|[calloc](calloc.md)|[fscanf —](fscanf-fscanf-l-fwscanf-fwscanf-l.md)|[_getw](getw.md)|[setvbuf](setvbuf.md)|
|[_exec — funkcje](../../c-runtime-library/exec-wexec-functions.md)|[fseek](fseek-fseeki64.md)|[_popen —](popen-wpopen.md)|[_spawn — funkcje](../../c-runtime-library/spawn-wspawn-functions.md)|
|[fgetc](fgetc-fgetwc.md)|[fsetpos](fsetpos.md)|[printf](printf-printf-l-wprintf-wprintf-l.md)|[_strdup](strdup-wcsdup-mbsdup.md)|
|[_fgetchar](fgetc-fgetwc.md)|[_fullpath](fullpath-wfullpath.md)|[putc —](putc-putwc.md)|[system](system-wsystem.md)|
|[fgets —](fgets-fgetws.md)|[fwrite](fwrite.md)|[putchar —](putc-putwc.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[fprintf —](fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[getc](getc-getwc.md)|[_putenv](putenv-wputenv.md)|[ungetc](ungetc-ungetwc.md)|
|[fputc —](fputc-fputwc.md)|[getchar](getc-getwc.md)|[umieszcza](puts-putws.md)|[vfprintf —](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|
|[_fputchar —](fputc-fputwc.md)|[_getcwd](getcwd-wgetcwd.md)|[_putw](putw.md)|[vprintf —](vprintf-vprintf-l-vwprintf-vwprintf-l.md)|
|[fputs —](fputs-fputws.md)|[_getdcwd](getcwd-wgetcwd.md)|[scanf](scanf-scanf-l-wscanf-wscanf-l.md)||
|[fread](fread.md)|[Pobiera](../../c-runtime-library/gets-getws.md)|[_searchenv](searchenv-wsearchenv.md)||

C++ [_set_new_mode —](set-new-mode.md) funkcja ustawia tryb obsługi nowych **— funkcja malloc**. Nowy tryb obsługi wskazuje, czy w przypadku awarii, **— funkcja malloc** jest wywołanie nowe procedury obsługi zgodnie z ustawieniami [_set_new_handler —](set-new-handler.md). Domyślnie **— funkcja malloc** nie wywołuje nowe procedury obsługi nie można przydzielić pamięci. Można zastąpić to zachowanie domyślne, aby, gdy **— funkcja malloc** nie może przydzielić pamięci, **— funkcja malloc** wywołuje nowe procedury obsługi w taki sam jak robi **nowe** operator jest Jeśli go nie powiodło się z tego samego powodu. Aby zastąpić domyślną, należy wywołać `_set_new_mode(1)` wcześniej w program lub Połącz z biblioteką NEWMODE. OBJ (zobacz [opcje łącza](../../c-runtime-library/link-options.md)).

Gdy aplikacja jest połączony z wersją debugowania biblioteki wykonawcze języka C, **— funkcja malloc** jest rozpoznawana jako [_malloc_dbg —](malloc-dbg.md). Aby uzyskać więcej informacji dotyczących sposobu zarządzania infrastrukturą sterty podczas debugowania procesu, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

**malloc** jest oznaczony jako `__declspec(noalias)` i `__declspec(restrict)`; to oznacza, że funkcja jest gwarantowana nie do modyfikowania zmiennych globalnych i że zwracane wskaźnik nie jest używane z aliasem. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md) i [ograniczyć](../../cpp/restrict.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**malloc**|\<stdlib.h > i \<malloc.h >|

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

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
[_aligned_malloc](aligned-malloc.md)<br/>
