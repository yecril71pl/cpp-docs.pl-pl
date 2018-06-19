---
title: tmpfile — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- tmpfile
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
- tmpfile
dev_langs:
- C++
helpviewer_keywords:
- temporary files
- tmpfile function
- temporary files, creating
ms.assetid: c4a4dc24-70da-438d-ae4e-98352d88e375
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ebcad2a25af2f2acb0056d882c4191f1a51293d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409072"
---
# <a name="tmpfile"></a>tmpfile

Tworzy plik tymczasowy. Ta funkcja jest przestarzały, ponieważ bezpieczniejsza wersja jest dostępna; zobacz [tmpfile_s —](tmpfile-s.md).

## <a name="syntax"></a>Składnia

```C
FILE *tmpfile( void );
```

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia **tmpfile —** zwraca wskaźnik strumienia. W przeciwnym razie zwraca **NULL** wskaźnika.

## <a name="remarks"></a>Uwagi

**Tmpfile —** funkcji powoduje utworzenie pliku tymczasowego i zwraca wskaźnik do tego strumienia. Plik tymczasowy zostanie utworzony w katalogu głównym. Aby utworzyć pliku tymczasowego w katalogu innym niż katalog główny, użyj [tmpnam —](tempnam-wtempnam-tmpnam-wtmpnam.md) lub [tempnam —](tempnam-wtempnam-tmpnam-wtmpnam.md) w połączeniu z [fopen —](fopen-wfopen.md).

Jeśli nie można otworzyć pliku, **tmpfile —** zwraca **NULL** wskaźnika. Plik tymczasowy jest automatycznie usuwana, gdy plik jest zamknięty, gdy program zakończenie zwykle lub **_rmtmp —** jest wywoływana przy założeniu, że bieżący katalog roboczy nie ulega zmianie. Plik tymczasowy jest otwarty w **w + b** trybu (binarne odczytu/zapisu).

Błąd może wystąpić przy próbie więcej niż tmp_max — (zobacz stdio —. H) wywołania z **tmpfile —**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**tmpfile**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

> [!NOTE]
> W tym przykładzie wymaga uprawnień administracyjnych do uruchamiania w systemie Windows Vista.

```C
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

## <a name="see-also"></a>Zobacz także

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_rmtmp](rmtmp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
