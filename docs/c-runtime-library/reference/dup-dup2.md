---
title: "_dup —, _dup2 — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- _dup2 function
- dup function
- file handles [C++], duplicating
- file handles [C++], reassigning
- dup2 function
- _dup function
ms.assetid: 4d07e92c-0d76-4832-a770-dfec0e7a0cfa
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f267ebf6526ed46cf3ef5670c6aeeb93a5a075e4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="dup-dup2"></a>_dup, _dup2
Tworzy drugi deskryptorów plików, dla której plik otwarty (`_dup`), lub ponownie przypisuje deskryptorów plików (`_dup2`).  
  
## <a name="syntax"></a>Składnia  
  
```  
int _dup(   
   int fd   
);  
int _dup2(   
   int fd1,  
   int fd2   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fd`, `fd1`  
 Deskryptorów plików odwołujące się do otwarcia pliku.  
  
 `fd2`  
 Wszelkie deskryptorów plików.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_dup`Zwraca nowy deskryptorów plików. `_dup2`Zwraca wartość 0, informując o powodzeniu. Jeśli wystąpi błąd, każda funkcja zwraca wartość -1 i zestawy `errno` do `EBADF` deskryptorów plików jest nieprawidłowy lub do `EMFILE` Jeśli nie więcej deskryptorów plików są dostępne. W przypadku deskryptora nieprawidłowy plik funkcji również wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md).  
  
 Aby uzyskać więcej informacji na temat tych i innych kody powrotu, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 `_dup` i `_dup2` funkcje skojarzyć drugi deskryptorów plików z aktualnie otwarty plik. Funkcje te można można użyć do skojarzenia deskryptor wstępnie zdefiniowanych plików, takim jak dla `stdout`, przy użyciu innego pliku. Przy użyciu albo deskryptorów plików można wykonywać operacji na pliku. Typ dostępu dozwolone dla pliku nie mają wpływu tworzenia nowego deskryptora. `_dup`zwraca deskryptor dalej dostępnych plików dla danego pliku. `_dup2`Wymusza `fd2` do odwoływania się do tego samego pliku jako `fd1`. Jeśli `fd2` jest skojarzony z otwartego pliku w momencie wywołania, czy plik jest zamknięty.  
  
 Zarówno `_dup` i `_dup2` zaakceptować deskryptorów plików jako parametry. Aby przekazać strumienia `(FILE *)` jednej z tych funkcji, należy użyć [_fileno —](../../c-runtime-library/reference/fileno.md). `fileno` Procedury zwraca deskryptorów plików, w obecnie skojarzony z danego strumienia. Poniższy przykład przedstawia sposób skojarzenia `stderr` (zdefiniowany jako `FILE` `*` w Stdio.h) z deskryptorów plików:  
  
```  
int cstderr = _dup( _fileno( stderr ));  
```  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_dup`|\<IO.h >|  
|`_dup2`|\<IO.h >|  
  
 Konsola nie jest obsługiwana w [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji. Uchwyty Standardowy strumień, które są skojarzone z konsoli programu —`stdin`, `stdout`, i `stderr`— muszą być przekierowywane przed funkcje wykonawcze języka C można używać ich w [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji. Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_dup.c  
// This program uses the variable old to save  
// the original stdout. It then opens a new file named  
// DataFile and forces stdout to refer to it. Finally, it  
// restores stdout to its original state.  
//  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)   
 [_zamknij](../../c-runtime-library/reference/close.md)   
 [_creat —, _wcreat —](../../c-runtime-library/reference/creat-wcreat.md)   
 [_otwórz, _wopen —](../../c-runtime-library/reference/open-wopen.md)