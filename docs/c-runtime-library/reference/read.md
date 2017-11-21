---
title: _przeczytaj | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _read
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
f1_keywords: _read
dev_langs: C++
helpviewer_keywords:
- data [CRT]
- _read function
- read function
- data [C++], reading
- reading data [C++]
- files [C++], reading
ms.assetid: 2ce9c433-57ad-47fe-9ac1-4a7d4c883d30
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2473dcac2d737d8419a90f4f8e7a47939065f3be
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="read"></a>_read

Odczytuje dane z pliku.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _read(  
   int fd,  
   void *buffer,  
   unsigned int count   
);  
```  
  
### <a name="parameters"></a>Parametry  

*FD*  
Plik deskryptora odwołujących się do otwartego pliku.  
  
*Bufor*  
Lokalizacja magazynu danych.  
  
*Liczba*  
Maksymalna liczba bajtów.  
  
## <a name="return-value"></a>Wartość zwracana  

`_read`Zwraca liczbę bajtów odczytanych, który może być mniejsza niż *liczba* Jeśli jest dostępnych mniej niż *liczba* pozostałych bajtów w pliku lub jeśli plik został otwarty w trybie tekstowym, w którym to przypadku wierszami powrotu karetki źródła pary `\r\n` jest zastępowany znak pojedynczego wysuwu wiersza `\n`. Tylko znak pojedynczego wysuwu wiersza jest liczony w wartości zwracanej. Zastąpienie nie ma wpływu na wskaźnika pliku.  
  
Jeśli funkcja próbuje odczytać na końcu pliku, zwraca wartość 0. Jeśli *fd* jest nieprawidłowy, plik nie jest otwarty do odczytu, lub plik jest zablokowany, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, funkcja zwraca wartość -1 i zestawy `errno` do `EBADF`.  
  
Jeśli *buforu* jest **NULL**, program obsługi nieprawidłowych parametrów jest wywoływany. Jeśli wykonanie może kontynuować, funkcja zwraca wartość -1 i `errno` ma ustawioną wartość `EINVAL`.  
  
Aby uzyskać więcej informacji dotyczących tego i innych kody powrotu, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  

`_read` Funkcja odczytuje maksymalnie *liczba* bajtów do *buforu* z pliku skojarzone z *fd*. Operacja odczytu rozpoczyna się w bieżącym położeniu wskaźnika pliku skojarzone z danym pliku. Po wykonaniu operacji odczytu wskaźnika pliku wskazuje na następny znak nieprzeczytana.  
  
Jeśli plik został otwarty w trybie tekstowym, Odczyt kończy kiedy `_read` napotka CTRL + Z znak, który jest traktowany jako plik końcowy wskaźnika. Użyj [_lseek —](../../c-runtime-library/reference/lseek-lseeki64.md) wyczyść wskaźnik końca pliku.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_read`|\<IO.h >|  
  
Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Biblioteki  

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Przykład  
  
```C  
// crt_read.c  
/* This program opens a file named crt_read.txt  
 * and tries to read 60,000 bytes from  
 * that file using _read. It then displays the  
 * actual number of bytes read.  
 */  
  
#include <fcntl.h>      /* Needed only for _O_RDWR definition */  
#include <io.h>  
#include <stdlib.h>  
#include <stdio.h>  
#include <share.h>  
  
char buffer[60000];  
  
int main( void )  
{  
   int fh;  
   unsigned int nbytes = 60000, bytesread;  
  
   /* Open file for input: */  
   if( _sopen_s( &fh, "crt_read.txt", _O_RDONLY, _SH_DENYNO, 0 ) )  
   {  
      perror( "open failed on input file" );  
      exit( 1 );  
   }  
  
   /* Read in input: */  
   if( ( bytesread = _read( fh, buffer, nbytes ) ) <= 0 )  
      perror( "Problem reading file" );  
   else  
      printf( "Read %u bytes from file\n", bytesread );  
  
   _close( fh );  
}  
```  
  
### <a name="input-crtreadtxt"></a>Dane wejściowe: crt_read.txt  
  
```  
Line one.  
Line two.  
```  
  
### <a name="output"></a>Dane wyjściowe  
  
```  
Read 19 bytes from file  
```  
  
## <a name="see-also"></a>Zobacz też  

[We/Wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)   
[_creat —, _wcreat —](../../c-runtime-library/reference/creat-wcreat.md)   
[fread —](../../c-runtime-library/reference/fread.md)   
[_otwórz, _wopen —](../../c-runtime-library/reference/open-wopen.md)   
[_Write](../../c-runtime-library/reference/write.md)
