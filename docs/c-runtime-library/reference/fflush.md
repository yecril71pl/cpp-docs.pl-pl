---
title: "fflush — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: fflush
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
f1_keywords: fflush
dev_langs: C++
helpviewer_keywords:
- streams, flushing
- flushing
- fflush function
ms.assetid: 8bbc753f-dc74-4e77-b563-74da2835e92b
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a5cca12799dfd44fdc0aaf67389cdd35e4cc6cc0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fflush"></a>fflush
Opróżnienia strumienia.  
  
## <a name="syntax"></a>Składnia  
  
```  
int fflush(   
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Wskaźnik do `FILE` struktury.  
  
## <a name="return-value"></a>Wartość zwracana  
 `fflush`Zwraca wartość 0, jeśli bufor został pomyślnie opróżniany. Wartość 0 jest także zwracany w przypadkach, w których określonego strumienia ma bufor nie jest otwarty do odczytu tylko. Zwracana wartość `EOF` wskazuje błąd.  
  
> [!NOTE]
>  Jeśli `fflush` zwraca `EOF`, dane mogą zostać utracone z powodu błędu zapisu. Podczas konfigurowania obsługi błąd krytyczny, jest najbezpieczniejszy wyłączyć buforowanie z `setvbuf` funkcji lub używać procedury we/wy niskiego poziomu, takich jak `_open`, `_close`, i `_write` zamiast funkcje We/Wy strumienia.  
  
## <a name="remarks"></a>Uwagi  
 `fflush` Funkcja opróżnienia strumienia `stream`. Jeśli strumień został otwarty na skutek zapisu trybu, lub został otwarty w trybie aktualizacji i zapis został ostatniej operacji, zawartości buforu strumienia są zapisywane do pliku źródłowego lub urządzenia i buforu zostaną odrzucone. Jeśli strumień został otwarty w trybie do odczytu albo strumienia nie ma żadnych buforu wywołanie `fflush` nie obowiązuje i są przechowywane wszystkie buforu. Wywołanie `fflush` Negacja efekt wszelkie wcześniejsze wywołanie elementu `ungetc` dla tego strumienia. Strumień pozostaje otwarty po wywołaniu.  
  
 Jeśli `stream` jest `NULL`, zachowanie jest taka sama jak wywołanie `fflush` na temat każdego strumienia otwarte. Wszystkie strumienie otwartym w trybie zapisu i wszystkich strumieni otwartym w trybie aktualizacji których ostatnia operacja zakończyła zapisu są opróżniane. Wywołanie nie ma wpływu na innych strumieni.  
  
 Bufory są zazwyczaj obsługiwane przez system operacyjny, który określa czas optymalnego automatycznie zapisać danych na dysku: gdy bufor jest pełny, gdy strumień jest zamknięty lub gdy program kończy się zwykle bez zamykania strumienia. Funkcja commit-to-disk biblioteki wykonawczej umożliwia upewnij się, że krytyczne dane są zapisywane bezpośrednio na dysku, a nie do buforów systemu operacyjnego. Bez ponowne zapisywanie istniejący program, łącząc plików obiektów programu z COMMODE.OBJ można włączyć tę funkcję. W wynikowym pliku wykonywalnego, wywołań `_flushall` zapisać zawartość buforów wszystkich na dysku. Tylko `_flushall` i `fflush` dotyczy COMMODE.OBJ.  
  
 Aby uzyskać informacje na temat funkcji commit-to-disk, zobacz [strumień we/wy](../../c-runtime-library/stream-i-o.md), [fopen —](../../c-runtime-library/reference/fopen-wfopen.md), i [_fdopen —](../../c-runtime-library/reference/fdopen-wfdopen.md).  
  
 Ta funkcja umożliwia zablokowanie wątek wywołujący i dlatego wątkowo. Wersja — blokowanie dla `_fflush_nolock`.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`fflush`|\<stdio.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_fflush.c  
#include <stdio.h>  
#include <conio.h>  
  
int main( void )  
{  
   int integer;  
   char string[81];  
  
   // Read each word as a string.  
   printf( "Enter a sentence of four words with scanf: " );  
   for( integer = 0; integer < 4; integer++ )  
   {  
      scanf_s( "%s", string, sizeof(string) );        
      printf( "%s\n", string );  
   }  
  
   // You must flush the input buffer before using gets.   
   // fflush on input stream is an extension to the C standard   
   fflush( stdin );     
   printf( "Enter the same sentence with gets: " );  
   gets_s( string, sizeof(string) );  
   printf( "%s\n", string );  
}  
```  
  
```Output  
  
      This is a test  
This is a test  
  
```  
  
```Output  
  
      This is a test  
This is a testEnter a sentence of four words with scanf: This is a test  
This  
is  
a  
test  
Enter the same sentence with gets: This is a test  
This is a test  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [fclose —, _fcloseall —](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [_flushall —](../../c-runtime-library/reference/flushall.md)   
 [setvbuf —](../../c-runtime-library/reference/setvbuf.md)