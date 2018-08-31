---
title: _dup, _dup2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _dup
- _dup2
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _dup2
- _dup
dev_langs:
- C++
helpviewer_keywords:
- _dup2 function
- dup function
- file handles [C++], duplicating
- file handles [C++], reassigning
- dup2 function
- _dup function
ms.assetid: 4d07e92c-0d76-4832-a770-dfec0e7a0cfa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 820172e1e6ab4ad007c89b2b40f03512134f0f0d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215956"
---
# <a name="dup-dup2"></a>_dup, _dup2

Tworzy deskryptor drugiego pliku dla otwartego pliku (**_dup —**), lub ponownie przypisuje deskryptor pliku (**_dup2 —**).

## <a name="syntax"></a>Składnia

```C
int _dup( int fd );
int _dup2( int fd1, int fd2 );
```

### <a name="parameters"></a>Parametry

*FD*, *fd1*<br/>
Deskryptory pliku odnoszące się do otwarcia pliku.

*FD2*<br/>
Każdy deskryptor pliku.

## <a name="return-value"></a>Wartość zwracana

**_dup —** zwraca nowy deskryptor pliku. **_dup2 —** zwraca wartość 0, informując o powodzeniu. Jeśli wystąpi błąd, każda funkcja zwraca wartość -1 i ustawia **errno** do **EBADF** Jeżeli deskryptor pliku jest nieprawidłowa lub aby **EMFILE** Jeśli więcej deskryptorów plików nie są dostępne. W przypadku nieprawidłowego deskryptora pliku, funkcja również wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md).

Aby uzyskać więcej informacji na temat tych i innych kodach powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Dup —** i **_dup2 —** funkcje kojarzą deskryptor drugiego pliku z aktualnie otwartym plikiem. Te funkcje można skojarzyć deskryptor pliku wstępnie zdefiniowanych w takim **stdout**, z innego pliku. Operacje na pliku mogą odbywać się przy użyciu pliku albo deskryptora pliku. Typ dostępu przyznany dla pliku jest zależny od utworzenia nowego deskryptora. **_dup —** zwraca następny dostępny deskryptor pliku dla danego pliku. **_dup2 —** wymusza *fd2* do odwoływania się do tego samego pliku jako *fd1*. Jeśli *fd2* jest skojarzony z plikiem otwartym w momencie wywołania, ten plik jest zamknięty.

Zarówno **_dup —** i **_dup2 —** akceptują deskryptory jako parametry. Aby przekazać strumień (`FILE *`) do jednej z tych funkcji, należy użyć [_fileno](fileno.md). **Fileno —** rutynowe zwroty deskryptora pliku aktualnie skojarzone z danym strumieniem. Poniższy przykład pokazuje, jak skojarzyć **stderr** (zdefiniowany jako `FILE *` w Stdio.h) z deskryptorem pliku:

```C
int cstderr = _dup( _fileno( stderr ));
```

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_dup**|\<io.h>|
|**_dup2**|\<io.h>|

Konsola nie jest obsługiwana w aplikacjach platformy uniwersalnej Windows (UWP). Standardowe uchwyty strumienia, które są powiązane z konsolą, **stdin**, **stdout**, i **stderr**, muszą zostać przekierowane zanim funkcje środowiska wykonawczego języka C można ich używać w aplikacjach platformy UWP . Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

[Niskiego poziomu operacji We/Wy](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
