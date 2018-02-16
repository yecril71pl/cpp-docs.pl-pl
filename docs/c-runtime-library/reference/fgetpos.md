---
title: "fgetpos — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- fgetpos
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
- fgetpos
dev_langs:
- C++
helpviewer_keywords:
- fgetpos function
- streams, file position indicator
ms.assetid: bfa05c38-1135-418c-bda1-d41be51acb62
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3740fdc7924e12fc9eeb2de4ab108ad376c764da
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="fgetpos"></a>fgetpos
Pobiera strumienia wskaźnika położenia pliku.  
  
## <a name="syntax"></a>Składnia  
  
```  
int fgetpos(   
   FILE *stream,  
   fpos_t *pos   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Strumień docelowy.  
  
 `pos`  
 Wskaźnik położenia magazynu.  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia `fgetpos` zwraca wartość 0. W przypadku awarii, zwraca wartość różną od zera i ustawia `errno` do jednej z następujących manifestu — stałe (zdefiniowany w stdio —. H): `EBADF`, co oznacza, że określonego obiektu stream nie jest prawidłowym plikiem wskaźnikiem lub nie jest dostępny, lub `EINVAL`, co oznacza, że `stream` wartość lub wartość `pos` jest nieprawidłowy, np. Jeśli to jest wskaźnika o wartości null. Jeśli `stream` lub `pos` jest `NULL` wskaźnika, funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md).  
  
## <a name="remarks"></a>Uwagi  
 `fgetpos` Funkcja pobiera bieżącą wartość `stream` wskaźnika położenia pliku i magazyny go w obiekcie wskazywana przez argumentu `pos`. `fsetpos` Funkcja mógł później użyć informacji przechowywanych w `pos` zresetować `stream` argumentu wskaźnik do położenia w czasie `fgetpos` została wywołana. `pos` Wartości są przechowywane w wewnętrznym formacie i jest przeznaczona do użycia tylko poprzez `fgetpos` i `fsetpos`.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`fgetpos`|\<stdio.h>|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_fgetpos.c  
// This program uses fgetpos and fsetpos to  
// return to a location in a file.  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE   *stream;  
   fpos_t pos;  
   char   buffer[20];  
  
   if( fopen_s( &stream, "crt_fgetpos.txt", "rb" ) ) {  
      perror( "Trouble opening file" );  
      return -1;  
   }  
  
   // Read some data and then save the position.   
   fread( buffer, sizeof( char ), 8, stream );  
   if( fgetpos( stream, &pos ) != 0 ) {  
      perror( "fgetpos error" );  
      return -1;  
   }  
  
   fread( buffer, sizeof( char ), 13, stream );  
   printf( "after fgetpos: %.13s\n", buffer );  
  
   // Restore to old position and read data   
   if( fsetpos( stream, &pos ) != 0 ) {  
      perror( "fsetpos error" );  
      return -1;  
   }  
  
   fread( buffer, sizeof( char ), 13, stream );  
   printf( "after fsetpos: %.13s\n", buffer );  
   fclose( stream );  
}  
```  
  
## <a name="input-crtfgetpostxt"></a>Dane wejściowe: crt_fgetpos.txt  
  
```  
fgetpos gets a stream's file-position indicator.  
```  
  
### <a name="output-crtfgetpostxt"></a>Crt_fgetpos.txt danych wyjściowych  
  
```  
after fgetpos: gets a stream  
after fsetpos: gets a stream  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [fsetpos](../../c-runtime-library/reference/fsetpos.md)