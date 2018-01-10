---
title: "fread — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: fread
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
f1_keywords: fread
dev_langs: C++
helpviewer_keywords:
- reading data [C++], from input streams
- fread function
- data [C++], reading from input stream
- streams [C++], reading data from
ms.assetid: 9a3c1538-93dd-455e-ae48-77c1e23c53f0
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e1230c3a309fc4fbbf382df4bb07ca2bebf0d5a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fread"></a>fread
Odczytuje dane ze strumienia.  
  
## <a name="syntax"></a>Składnia  
  
```  
size_t fread(   
   void *buffer,  
   size_t size,  
   size_t count,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 Lokalizacja magazynu danych.  
  
 `size`  
 Rozmiar elementu w bajtach.  
  
 `count`  
 Maksymalna liczba elementów do odczytu.  
  
 `stream`  
 Wskaźnik do `FILE` struktury.  
  
## <a name="return-value"></a>Wartość zwracana  
 `fread`Zwraca liczbę elementów pełne faktycznie odczytu, które może być mniejsza niż `count` Jeśli wystąpi błąd lub napotkano koniec pliku przed osiągnięciem `count`. Użyj `feof` lub `ferror` funkcja odróżnienia błąd odczytu warunek końca pliku. Jeśli `size` lub `count` ma wartość 0, `fread` zwraca 0 i zawartości buforu nie uległy zmianie. Jeśli `stream` lub `buffer` wskaźnika o wartości null, jest `fread` wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, ta funkcja ustawia `errno` do `EINVAL` i zwraca wartość 0.  
  
 Zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat tych i innych kodów błędów.  
  
## <a name="remarks"></a>Uwagi  
 `fread` Funkcja odczytuje do `count` elementów `size` bajtów z danych wejściowych `stream` i zapisuje je w `buffer`. Wskaźnika pliku skojarzone z `stream` (jeśli istnieje) jest zwiększana o liczba bajtów odczytanych w rzeczywistości. Jeśli dany strumień jest otwarty w trybie tekstowym, pary wysuwu wiersza powrotu karetki są zastępowane wysuwu wiersza pojedynczy znaki. Zastąpienie nie ma wpływu na wskaźnika pliku lub wartości zwracanej. Położenie pliku wskaźnika jest nieokreślony, jeśli wystąpi błąd. Nie można określić wartość elementu częściowo odczytu.  
  
 Ta funkcja blokuje inne wątki. Wersja — blokowanie, należy użyć `_fread_nolock`.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`fread`|\<stdio.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_fread.c  
// This program opens a file named FREAD.OUT and  
// writes 25 characters to the file. It then tries to open  
// FREAD.OUT and read in 25 characters. If the attempt succeeds,  
// the program displays the number of actual items read.  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char list[30];  
   int  i, numread, numwritten;  
  
   // Open file in text mode:  
   if( fopen_s( &stream, "fread.out", "w+t" ) == 0 )  
   {  
      for ( i = 0; i < 25; i++ )  
         list[i] = (char)('z' - i);  
      // Write 25 characters to stream   
      numwritten = fwrite( list, sizeof( char ), 25, stream );  
      printf( "Wrote %d items\n", numwritten );  
      fclose( stream );  
  
   }  
   else  
      printf( "Problem opening the file\n" );  
  
   if( fopen_s( &stream, "fread.out", "r+t" ) == 0 )  
   {  
      // Attempt to read in 25 characters   
      numread = fread( list, sizeof( char ), 25, stream );  
      printf( "Number of items read = %d\n", numread );  
      printf( "Contents of buffer = %.25s\n", list );  
      fclose( stream );  
   }  
   else  
      printf( "File could not be opened\n" );  
}  
```  
  
```Output  
Wrote 25 items  
Number of items read = 25  
Contents of buffer = zyxwvutsrqponmlkjihgfedcb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [fwrite —](../../c-runtime-library/reference/fwrite.md)   
 [_read](../../c-runtime-library/reference/read.md)