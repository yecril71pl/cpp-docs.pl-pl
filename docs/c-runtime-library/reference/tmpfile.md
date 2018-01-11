---
title: "tmpfile — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: tmpfile
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
f1_keywords: tmpfile
dev_langs: C++
helpviewer_keywords:
- temporary files
- tmpfile function
- temporary files, creating
ms.assetid: c4a4dc24-70da-438d-ae4e-98352d88e375
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b4e6600eda1bae67edaa531d5af05033d1448d8a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="tmpfile"></a>tmpfile
Tworzy plik tymczasowy. Ta funkcja jest przestarzały, ponieważ bezpieczniejsza wersja jest dostępna; zobacz [tmpfile_s —](../../c-runtime-library/reference/tmpfile-s.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
FILE *tmpfile( void );  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia `tmpfile` zwraca wskaźnik strumienia. W przeciwnym razie zwraca `NULL` wskaźnika.  
  
## <a name="remarks"></a>Uwagi  
 `tmpfile` Funkcji powoduje utworzenie pliku tymczasowego i zwraca wskaźnik do tego strumienia. Plik tymczasowy zostanie utworzony w katalogu głównym. Aby utworzyć pliku tymczasowego w katalogu innym niż katalog główny, użyj [tmpnam —](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) lub [tempnam —](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) w połączeniu z [fopen —](../../c-runtime-library/reference/fopen-wfopen.md).  
  
 Jeśli nie można otworzyć pliku, `tmpfile` zwraca `NULL` wskaźnika. Plik tymczasowy jest automatycznie usuwana, gdy plik jest zamknięty, gdy program zakończenie zwykle lub `_rmtmp` jest wywoływana przy założeniu, że bieżący katalog roboczy nie ulega zmianie. Plik tymczasowy jest otwarty w `w+b` trybu (binarne odczytu/zapisu).  
  
 Błąd może wystąpić przy próbie więcej niż tmp_max — (zobacz stdio —. H) wywołania z `tmpfile`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`tmpfile`|\<stdio.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
> [!NOTE]
>  W tym przykładzie wymaga uprawnień administracyjnych do uruchamiania w systemie Windows Vista.  
  
```  
// crt_tmpfile.c  
// compile with: /W3  
// This program uses tmpfile to create a  
// temporary file, then deletes this file with _rmtmp.  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   int  i;  
  
   // Create temporary files.  
   for( i = 1; i <= 3; i++ )  
   {  
      if( (stream = tmpfile()) == NULL ) // C4996  
      // Note: tmpfile is deprecated; consider using tmpfile_s instead  
         perror( "Could not open new temporary file\n" );  
      else  
         printf( "Temporary file %d was created\n", i );  
   }  
  
   // Remove temporary files.  
   printf( "%d temporary files deleted\n", _rmtmp() );  
}  
```  
  
```Output  
Temporary file 1 was created  
Temporary file 2 was created  
Temporary file 3 was created  
3 temporary files deleted  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [_rmtmp —](../../c-runtime-library/reference/rmtmp.md)   
 [_tempnam, _wtempnam, tmpnam, _wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)