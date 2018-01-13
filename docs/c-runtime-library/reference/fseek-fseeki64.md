---
title: "fseek, _fseeki64 — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _fseeki64
- fseek
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
apitype: DLLExport
f1_keywords:
- fseek
- _fseeki64
dev_langs: C++
helpviewer_keywords:
- _fseeki64 function
- fseeki64 function
- fseek function
- file pointers [C++], moving
- file pointers [C++]
- seek file pointers
ms.assetid: f6bb1f8b-891c-426e-9e14-0e7e5c62df70
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 90af1581910ceaadf814050be39bc537cfc3881c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fseek-fseeki64"></a>fseek, _fseeki64
Przenosi wskaźnika pliku do określonej lokalizacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
int fseek(   
   FILE *stream,  
   long offset,  
   int origin   
);  
int _fseeki64(   
   FILE *stream,  
   __int64 offset,  
   int origin   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Wskaźnik do `FILE` struktury.  
  
 `offset`  
 Liczba bajtów z `origin`.  
  
 `origin`  
 Pozycja początkowa.  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia `fseek` i `_fseeki64` zwraca wartość 0. W przeciwnym wypadku zwraca wartość różną od zera. Na urządzeniach niezdolne do wyszukiwania wartość zwracana jest niezdefiniowany. Jeśli `stream` jest wskaźnika o wartości null, lub jeśli `origin` nie jest jednym z dozwolonych wartości opisanych poniżej, `fseek` i `_fseeki64` Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji `errno` do `EINVAL` i zwróć -1.  
  
## <a name="remarks"></a>Uwagi  
 `fseek` i `_fseeki64` funkcje przenosi wskaźnika pliku (jeśli istnieje) skojarzone z `stream` do nowej lokalizacji, która jest `offset` bajtów z `origin`. Następnej operacji na strumieniu odbywa się w nowej lokalizacji. W strumieniu otwarty do aktualizacji można następnej operacji odczytu lub zapisu. Początek argumentów musi mieć jedną z następujących stałych, zdefiniowane w stdio —. H:  
  
 `SEEK_CUR`  
 Bieżąca pozycja wskaźnika pliku.  
  
 `SEEK_END`  
 Koniec pliku.  
  
 `SEEK_SET`  
 Początek pliku.  
  
 Można użyć `fseek` i `_fseeki64` Aby przesunąć kursor w dowolnym miejscu w pliku. Wskaźnik również może być umieszczony poza koniec pliku. `fseek`i `_fseeki64` czyści wskaźnik końca pliku i Negacja efekt żadnych przed `ungetc` wywołuje przed `stream`.  
  
 Po otwarciu pliku do dołączenia danych bieżącej pozycji w pliku zależy od ostatniej operacji We/Wy przez nie może mieć miejsce kolejnego zapisu. Jeśli jeszcze przeprowadzono żadnej operacji We/Wy w pliku otwartym dołączania, pozycji w pliku jest początku pliku.  
  
 Dla strumieni otwarty w trybie tekstowym `fseek` i `_fseeki64` ograniczoną użycia, ponieważ może spowodować tłumaczeń wysuwu wiersza powrotu karetki `fseek` i `_fseeki64` powodować nieoczekiwane wyniki. Jedynym `fseek` i `_fseeki64` operacje działać na strumienie otwarty w trybie tekstowym są:  
  
-   Wyszukiwanie z przesunięciem równym 0 względem wartości pochodzenia.  
  
-   Wyszukiwanie od początku pliku wartość przesunięcia zwrócone w wyniku wywołania `ftell` przy użyciu `fseek` lub `_ftelli64` przy użyciu `_fseeki64`.  
  
 Również w trybie tekstowym CTRL + Z jest interpretowany jako plik końcowy znak wejściowy. W plikach otwarty do odczytu/zapisu `fopen` i wszystkie powiązane procedury Sprawdź, czy CTRL + Z końcem pliku i usuń go, jeśli to możliwe. Jest to zrobić, ponieważ przy użyciu kombinacji `fseek` i `ftell` lub `_fseeki64` i `_ftelli64`, aby przenieść w pliku, który może spowodować kończy się CTRL + Z `fseek` lub `_fseeki64` będzie działać nieprawidłowo zbliża się koniec pliku.  
  
 Gdy CRT otwiera plik, który rozpoczyna się z znacznik kolejności bajtów (BOM), wskaźnika pliku znajduje się po BOM (to znaczy na początku pliku rzeczywistej zawartości). Jeśli zajdzie potrzeba `fseek` na początku pliku, użyj `ftell` uzyskać położenie początkowe i `fseek` do niego, a nie na pozycji 0.  
  
 Ta funkcja blokuje innych wątków podczas wykonywania i dlatego wątkowo. Wersja — blokowanie dla [_fseek_nolock —, _fseeki64_nolock —](../../c-runtime-library/reference/fseek-nolock-fseeki64-nolock.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`fseek`|\<stdio.h >|  
|`_fseeki64`|\<stdio.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_fseek.c  
// This program opens the file FSEEK.OUT and  
// moves the pointer to the file's beginning.  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char line[81];  
   int  result;  
  
   if ( fopen_s( &stream, "fseek.out", "w+" ) != 0 )  
   {  
      printf( "The file fseek.out was not opened\n" );  
      return -1;  
   }  
   fprintf( stream, "The fseek begins here: "  
                    "This is the file 'fseek.out'.\n" );  
   result = fseek( stream, 23L, SEEK_SET);  
   if( result )  
      perror( "Fseek failed" );  
   else  
   {  
      printf( "File pointer is set to middle of first line.\n" );  
      fgets( line, 80, stream );  
      printf( "%s", line );  
    }  
   fclose( stream );  
}  
```  
  
```Output  
File pointer is set to middle of first line.  
This is the file 'fseek.out'.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [fopen —, _wfopen —](../../c-runtime-library/reference/fopen-wfopen.md)   
 [ftell —, _ftelli64 —](../../c-runtime-library/reference/ftell-ftelli64.md)   
 [_lseek —, _lseeki64 —](../../c-runtime-library/reference/lseek-lseeki64.md)   
 [rewind](../../c-runtime-library/reference/rewind.md)