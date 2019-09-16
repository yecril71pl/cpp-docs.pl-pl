---
title: _dup, _dup2
ms.date: 11/04/2016
api_name:
- _dup
- _dup2
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _dup2
- _dup
helpviewer_keywords:
- _dup2 function
- dup function
- file handles [C++], duplicating
- file handles [C++], reassigning
- dup2 function
- _dup function
ms.assetid: 4d07e92c-0d76-4832-a770-dfec0e7a0cfa
ms.openlocfilehash: da47d6f040b62906d30107f9036ffa2a3ea05a1c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70937786"
---
# <a name="_dup-_dup2"></a>_dup, _dup2

Tworzy drugi deskryptor pliku dla otwartego pliku ( **_dup**) lub ponownie przypisuje deskryptor pliku ( **_dup2**).

## <a name="syntax"></a>Składnia

```C
int _dup( int fd );
int _dup2( int fd1, int fd2 );
```

### <a name="parameters"></a>Parametry

*FD*, *FD1*<br/>
Deskryptory plików odwołujące się do otwartego pliku.

*fd2*<br/>
Dowolny deskryptor pliku.

## <a name="return-value"></a>Wartość zwracana

**_dup** zwraca nowy deskryptor pliku. **_dup2** zwraca wartość 0, aby wskazać powodzenie. Jeśli wystąpi błąd, każda funkcja zwraca wartość-1 i ustawia **errno** na **EBADF** , jeśli deskryptor pliku jest nieprawidłowy lub **EMFILE** , jeśli nie ma więcej dostępnych deskryptorów plików. W przypadku nieprawidłowego deskryptora pliku funkcja wywołuje również procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md).

Aby uzyskać więcej informacji na temat tych i innych kodów powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcje **_dup** i **_dup2** kojarzą drugi deskryptor pliku z aktualnie otwartym plikiem. Te funkcje mogą służyć do kojarzenia wstępnie zdefiniowanego deskryptora pliku, takiego jak w przypadku strumienia **stdout**, z innym plikiem. Operacje na pliku można wykonać przy użyciu deskryptora pliku. Nie ma to wpływ na typ dostępu dozwolony dla danego pliku. **_dup** zwraca następny dostępny deskryptor pliku dla danego pliku. **_dup2** zmusza *FD2* do odwoływania się do tego samego pliku jako *FD1*. Jeśli *FD2* jest skojarzony z otwartym plikiem w momencie wywołania, ten plik jest zamknięty.

Zarówno **_dup** , jak i **_dup2** akceptują deskryptory plików jako parametry. Aby przekazać strumień (`FILE *`) do jednej z tych funkcji, użyj [_fileno](fileno.md). Procedura **fileno** zwraca deskryptor pliku aktualnie skojarzony z danym strumieniem. Poniższy przykład pokazuje, jak skojarzyć **stderr** (zdefiniowany jako `FILE *` w stdio. h) z deskryptorem pliku:

```C
int cstderr = _dup( _fileno( stderr ));
```

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_dup**|\<io.h>|
|**_dup2**|\<io.h>|

Konsola nie jest obsługiwana w aplikacjach platforma uniwersalna systemu Windows (platformy UWP). Standardowe uchwyty strumienia, które są skojarzone z konsolą, **stdin**, **stdout**i **stderr**, muszą zostać przekierowane przed użyciem funkcji języka C w aplikacjach platformy UWP. Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_dup.c
// This program uses the variable old to save
// the original stdout. It then opens a new file named
// DataFile and forces stdout to refer to it. Finally, it
// restores stdout to its original state.

#include <io.h>
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int old;
   FILE *DataFile;

   old = _dup( 1 );   // "old" now refers to "stdout"
                      // Note:  file descriptor 1 == "stdout"
   if( old == -1 )
   {
      perror( "_dup( 1 ) failure" );
      exit( 1 );
   }
   _write( old, "This goes to stdout first\n", 26 );
   if( fopen_s( &DataFile, "data", "w" ) != 0 )
   {
      puts( "Can't open file 'data'\n" );
      exit( 1 );
   }

   // stdout now refers to file "data"
   if( -1 == _dup2( _fileno( DataFile ), 1 ) )
   {
      perror( "Can't _dup2 stdout" );
      exit( 1 );
   }
   puts( "This goes to file 'data'\n" );

   // Flush stdout stream buffer so it goes to correct file
   fflush( stdout );
   fclose( DataFile );

   // Restore original stdout
   _dup2( old, 1 );
   puts( "This goes to stdout\n" );
   puts( "The file 'data' contains:" );
   _flushall();
   system( "type data" );
}
```

```Output
This goes to stdout first
This goes to stdout

The file 'data' contains:
This goes to file 'data'
```

## <a name="see-also"></a>Zobacz także

[We/wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
