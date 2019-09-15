---
title: tmpfile
ms.date: 11/04/2016
api_name:
- tmpfile
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- tmpfile
helpviewer_keywords:
- temporary files
- tmpfile function
- temporary files, creating
ms.assetid: c4a4dc24-70da-438d-ae4e-98352d88e375
ms.openlocfilehash: f58c23050fe89f84f283c3784a7c0cee72637bf2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957540"
---
# <a name="tmpfile"></a>tmpfile

Tworzy plik tymczasowy. Ta funkcja jest przestarzała, ponieważ jest dostępna bezpieczniejsza wersja; Zobacz [tmpfile_s](tmpfile-s.md).

## <a name="syntax"></a>Składnia

```C
FILE *tmpfile( void );
```

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, **tmpfile** zwraca wskaźnik strumienia. W przeciwnym razie zwraca wskaźnik o **wartości null** .

## <a name="remarks"></a>Uwagi

Funkcja **tmpfile** tworzy plik tymczasowy i zwraca wskaźnik do tego strumienia. Plik tymczasowy zostanie utworzony w katalogu głównym. Aby utworzyć plik tymczasowy w katalogu innym niż główny, użyj [tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md) lub [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md) w połączeniu z [fopen](fopen-wfopen.md).

Jeśli nie można otworzyć pliku, **tmpfile** zwraca wskaźnik o **wartości null** . Ten plik tymczasowy jest automatycznie usuwany po zamknięciu pliku, gdy program kończy się normalnie lub gdy **_rmtmp** jest wywoływana, przy założeniu, że bieżący katalog roboczy nie zmienia się. Plik tymczasowy jest otwierany w trybie w **+ b** (binarny odczyt/zapis).

Błąd może wystąpić, Jeśli podjęto próbę więcej niż TMP_MAX (patrz STDIO. H) wywołania z **tmpfile**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**tmpfile**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

> [!NOTE]
> Ten przykład wymaga uprawnień administracyjnych do uruchomienia w systemie Windows Vista.

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

[We/wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_rmtmp](rmtmp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
