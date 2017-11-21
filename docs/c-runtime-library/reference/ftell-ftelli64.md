---
title: "ftell —, _ftelli64 — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ftelli64
- ftell
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
- _ftelli64
- ftell
dev_langs: C++
helpviewer_keywords:
- ftell function
- ftelli64 function
- _ftelli64 function
- file pointers [C++], getting current position
- file pointers [C++]
ms.assetid: 40149cd8-65f2-42ff-b70c-68e3e918cdd7
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4b37db89ca7d9e3facb7de2fbce2dc819cfa03e8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ftell-ftelli64"></a>ftell, _ftelli64
Pobiera bieżącą pozycję wskaźnika pliku.  
  
## <a name="syntax"></a>Składnia  
  
```  
long ftell(   
   FILE *stream   
);  
__int64 _ftelli64(   
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Docelowy `FILE` struktury.  
  
## <a name="return-value"></a>Wartość zwracana  
 `ftell`i `_ftelli64` Zwraca bieżące położenie pliku. Wartość zwrócona przez `ftell` i `_ftelli64` mogą nie uwzględniać Przesunięcie bajtów fizycznego dla strumieni otwarty w trybie tekstowym, ponieważ tryb tekstu powoduje tłumaczenie wysuwu wiersza powrotu karetki. Użyj `ftell` z `fseek` lub `_ftelli64` z `_fseeki64` aby powrócić do lokalizacji plików poprawnie. W przypadku błędu `ftell` i `_ftelli64` Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, te funkcje zwracane L-1 i zestaw `errno` do jednej z dwóch stałe, zdefiniowane w numer błędu. H. `EBADF` Oznacza stała `stream` argument nie jest wartością wskaźnika prawidłowego pliku lub nie odwołuje się do otwartego pliku. `EINVAL`oznacza nieprawidłową `stream` argument został przekazany do funkcji. Na urządzeniach niezdolne do znalezienia (na przykład terminale i drukarki) lub gdy `stream` nie odwołuje się do otwartego pliku, zwracana wartość jest niezdefiniowana.  
  
 Zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) kody powrotne — Aby uzyskać więcej informacji na temat tych i innych.  
  
## <a name="remarks"></a>Uwagi  
 `ftell` i `_ftelli64` funkcje pobrać bieżącą pozycję wskaźnika pliku (jeśli istnieje) skojarzone z `stream`. Pozycja jest wyrażona jako przesunięcia względem początkiem strumienia.  
  
 Należy pamiętać, że po otwarciu pliku do dołączenia danych bieżącej pozycji w pliku zależy od ostatniej operacji We/Wy przez nie może mieć miejsce kolejnego zapisu. Na przykład jeśli plik jest otwarty w celu dołączania, a ostatnia operacja została odczytu, pozycji w pliku jest punkt, w którym następnej operacji odczytu chce się uruchomić, nie gdzie zaczyna kolejnego zapisu. (Jeśli plik jest otwarty w celu dołączania, pozycji w pliku została przeniesiona do koniec pliku przed żadnej operacji zapisu). Jeśli jeszcze przeprowadzono żadnej operacji We/Wy w pliku otwartym dołączania, pozycji w pliku jest na początku pliku.  
  
 W trybie tekstowym CTRL + Z jest interpretowany jako plik końcowy znak wejściowy. W plikach otwarty do odczytu/zapisu `fopen` i wszystkie powiązane procedury Sprawdź, czy CTRL + Z końcem pliku i usuń go, jeśli to możliwe. Jest to zrobić, ponieważ przy użyciu kombinacji `ftell` i `fseek` lub `_ftelli64` i `_fseeki64`, aby przenieść w pliku, który może spowodować kończy się CTRL + Z `ftell` lub `_ftelli64` będzie działać nieprawidłowo zbliża się koniec pliku.  
  
 Ta funkcja umożliwia zablokowanie wątek wywołujący podczas wykonywania i dlatego wątkowo. Wersja — blokowanie dla `_ftell_nolock`.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|Opcjonalne nagłówki|  
|--------------|---------------------|----------------------|  
|`ftell`|\<stdio.h >|\<errno.h >|  
|`_ftelli64`|\<stdio.h >|\<errno.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_ftell.c  
// This program opens a file named CRT_FTELL.C  
// for reading and tries to read 100 characters. It  
// then uses ftell to determine the position of the  
// file pointer and displays this position.  
  
#include <stdio.h>  
  
FILE *stream;  
  
int main( void )  
{  
   long position;  
   char list[100];  
   if( fopen_s( &stream, "crt_ftell.c", "rb" ) == 0 )  
   {  
      // Move the pointer by reading data:   
      fread( list, sizeof( char ), 100, stream );  
      // Get position after read:   
      position = ftell( stream );  
      printf( "Position after trying to read 100 bytes: %ld\n",  
              position );  
      fclose( stream );  
   }  
}  
```  
  
```Output  
Position after trying to read 100 bytes: 100  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [fopen —, _wfopen —](../../c-runtime-library/reference/fopen-wfopen.md)   
 [fgetpos —](../../c-runtime-library/reference/fgetpos.md)   
 [fseek, _fseeki64 —](../../c-runtime-library/reference/fseek-fseeki64.md)   
 [_lseek —, _lseeki64 —](../../c-runtime-library/reference/lseek-lseeki64.md)