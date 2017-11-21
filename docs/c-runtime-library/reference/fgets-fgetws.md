---
title: "fgets —, fgetws — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- fgets
- fgetws
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
- _fgetts
- fgetws
- fgets
dev_langs: C++
helpviewer_keywords:
- _fgetts function
- streams, getting strings from
- streams, reading from
- fgets function
- fgetws function
- fgetts function
ms.assetid: ad549bb5-df98-4ccd-a53f-95114e60c4fc
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f1427c830ea861f7b3195c745fff6cde68858666
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fgets-fgetws"></a>fgets, fgetws
Pobierz ciąg ze strumienia.  
  
## <a name="syntax"></a>Składnia  
  
```  
char *fgets(   
   char *str,  
   int n,  
   FILE *stream   
);  
wchar_t *fgetws(   
   wchar_t *str,  
   int n,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `str`  
 Lokalizacja magazynu danych.  
  
 `n`  
 Maksymalna liczba znaków do odczytania.  
  
 `stream`  
 Wskaźnik do `FILE` struktury.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każdy z tych funkcji zwraca `str`. `NULL`zwracany jest błąd lub warunek końca pliku. Użyj `feof` lub `ferror` do określenia, czy wystąpił błąd. Jeśli `str` lub `stream` jest wskaźnika o wartości null, lub `n` jest mniejsza lub równa zero, ta funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `errno` ustawiono `EINVAL` i funkcja zwraca `NULL`.  
  
 Zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat tych i innych kodów błędów.  
  
## <a name="remarks"></a>Uwagi  
 `fgets` Funkcja odczytuje ciągu wejściowego `stream` argumentu i przechowuje ją w `str`. `fgets`odczytuje znaków z bieżącego położenia strumienia, w tym pierwszym znakiem nowego wiersza, w celu strumienia lub dopóki liczba znaków do odczytu jest równa `n` - 1, zależnie od zostanie osiągnięty jako pierwszy. Wynik przechowywany w `str` jest dołączany znakiem null. Znak nowego wiersza, jeśli do odczytu, jest uwzględniona w parametrach.  
  
 `fgetws`jest to wersja znaków dwubajtowych `fgets`.  
  
 `fgetws`odczytuje argument znaków dwubajtowych `str` jako ciąg znaków wielobajtowych lub ciągiem znaków dwubajtowych zgodnie z czy `stream` odpowiednio jest otwarty w trybie tekstu lub w trybie binarnym. Aby uzyskać więcej informacji na temat używania trybach tekstowym i binarnym Unicode i wielobajtowe strumienia I/O zobacz [tekstu i we/wy binarne trybu pliku](../../c-runtime-library/text-and-binary-mode-file-i-o.md) i [we/wy strumienia w Unicode w trybach tekstowym i binarnym](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_fgetts`|`fgets`|`fgets`|`fgetws`|  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`fgets`|\<stdio.h >|  
|`fgetws`|\<stdio.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_fgets.c  
// This program uses fgets to display  
// a line from a file on the screen.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char line[100];  
  
   if( fopen_s( &stream, "crt_fgets.txt", "r" ) == 0 )  
   {  
      if( fgets( line, 100, stream ) == NULL)  
         printf( "fgets error\n" );  
      else  
         printf( "%s", line);  
      fclose( stream );  
   }  
}  
```  
  
## <a name="input-crtfgetstxt"></a>Dane wejściowe: crt_fgets.txt  
  
```  
Line one.  
Line two.  
```  
  
### <a name="output"></a>Dane wyjściowe  
  
```  
Line one.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [fputs —, fputws —](../../c-runtime-library/reference/fputs-fputws.md)   
 [pobiera _getws —](../../c-runtime-library/gets-getws.md)   
 [umieszcza _putws —](../../c-runtime-library/reference/puts-putws.md)