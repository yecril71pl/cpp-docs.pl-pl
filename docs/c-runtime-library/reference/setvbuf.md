---
title: "setvbuf — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: setvbuf
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
f1_keywords: setvbuf
dev_langs: C++
helpviewer_keywords:
- controlling stream buffering
- stream buffering
- setvbuf function
ms.assetid: 6aa5aa37-3408-4fa0-992f-87f9f9c4baea
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b5020a0186399ec35fb42a0479f7466318c45c18
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="setvbuf"></a>setvbuf
Buforowanie strumienia formantów i rozmiar buforu.  
  
## <a name="syntax"></a>Składnia  
  
```  
int setvbuf(  
   FILE *stream,  
   char *buffer,  
   int mode,  
   size_t size   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stream`  
 Wskaźnik do `FILE` struktury.  
  
 `buffer`  
 Bufor przydzielone przez użytkownika.  
  
 `mode`  
 Tryb buforowania.  
  
 `size`  
 Rozmiar buforu w bajtach. Dopuszczalny zakres: 2 < = `size` < = int_max — (2147483647). Wewnętrznie, podana wartość `size` jest zaokrąglana do najbliższej wielokrotności 2.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość 0 w przypadku powodzenia.  
  
 Jeśli `stream` jest `NULL`, lub jeśli `mode` lub `size` jest nie prawidłowy zmian, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, ta funkcja zwraca wartość -1 i zestawy `errno` do `EINVAL`.  
  
 Aby uzyskać informacje na temat tych i innych kodów błędów, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 `setvbuf` Funkcja pozwala programowi na sterowanie zarówno buforowanie i rozmiar dla buforu `stream`. `stream`musi odwoływać się do otwartego pliku, która nie została poddana operacji We/Wy, ponieważ zostało otwarte. Tablica wskazywana przez `buffer` pełni rolę bufora, chyba że jest `NULL`, w którym to przypadku `setvbuf` używa automatycznie przydzielonego buforu o długości `size`/2 * 2 bajtów.  
  
 Tryb musi być `_IOFBF`, `_IOLBF`, lub `_IONBF`. Jeśli `mode` jest `_IOFBF` lub `_IOLBF`, następnie `size` jest używany jako rozmiar buforu. Jeśli `mode` jest `_IONBF`, strumień jest Niebuforowane i `size` i `buffer` są ignorowane. Wartości `mode` i ich znaczenie:  
  
 `_IOFBF`  
 Pełne buforowanie; oznacza to `buffer` jest używany jako bufor i `size` jest używany jako rozmiar buforu. Jeśli `buffer` jest `NULL`, automatycznie przydzielonego buforu `size` bajtów jest używany.  
  
 `_IOLBF`  
 W niektórych systemach zapewnia buforowanie wiersza. Jednak systemu Win32, zachowanie jest taka sama jak `_IOFBF` — pełne buforowanie.  
  
 `_IONBF`  
 Bufor nie jest używane, bez względu na to `buffer` lub `size`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`setvbuf`|\<stdio.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_setvbuf.c  
// This program opens two streams: stream1  
// and stream2. It then uses setvbuf to give stream1 a  
// user-defined buffer of 1024 bytes and stream2 no buffer.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   char buf[1024];  
   FILE *stream1, *stream2;  
  
   if( fopen_s( &stream1, "data1", "a" ) == 0 &&  
       fopen_s( &stream2, "data2", "w" ) == 0 )  
   {  
      if( setvbuf( stream1, buf, _IOFBF, sizeof( buf ) ) != 0 )  
         printf( "Incorrect type or size of buffer for stream1\n" );  
      else  
         printf( "'stream1' now has a buffer of 1024 bytes\n" );  
      if( setvbuf( stream2, NULL, _IONBF, 0 ) != 0 )  
         printf( "Incorrect type or size of buffer for stream2\n" );  
      else  
         printf( "'stream2' now has no buffer\n" );  
      _fcloseall();  
   }  
}  
```  
  
```Output  
'stream1' now has a buffer of 1024 bytes  
'stream2' now has no buffer  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [fclose —, _fcloseall —](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [fflush —](../../c-runtime-library/reference/fflush.md)   
 [fopen —, _wfopen —](../../c-runtime-library/reference/fopen-wfopen.md)   
 [setbuf](../../c-runtime-library/reference/setbuf.md)