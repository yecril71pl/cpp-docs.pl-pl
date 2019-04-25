---
title: tmpfile
ms.date: 11/04/2016
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
helpviewer_keywords:
- temporary files
- tmpfile function
- temporary files, creating
ms.assetid: c4a4dc24-70da-438d-ae4e-98352d88e375
ms.openlocfilehash: 98afcb7a3e04a96a1b08bc1b975634153e550839
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155566"
---
# <a name="tmpfile"></a>tmpfile

Tworzy plik tymczasowy. Ta funkcja jest przestarzały, ponieważ bardziej bezpieczna wersja jest dostępna; zobacz [tmpfile_s —](tmpfile-s.md).

## <a name="syntax"></a>Składnia

```C
FILE *tmpfile( void );
```

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia **tmpfile —** zwraca wskaźnik strumienia. W przeciwnym razie zwraca **NULL** wskaźnika.

## <a name="remarks"></a>Uwagi

**Tmpfile —** funkcji utworzy plik tymczasowy i zwraca wskaźnik do tego strumienia. Plik tymczasowy zostanie utworzony w katalogu głównym. Aby utworzyć pliku tymczasowego w katalogu innym niż katalog główny, użyj [tmpnam —](tempnam-wtempnam-tmpnam-wtmpnam.md) lub [tempnam —](tempnam-wtempnam-tmpnam-wtmpnam.md) w połączeniu z [fopen —](fopen-wfopen.md).

Jeśli nie można otworzyć pliku, **tmpfile —** zwraca **NULL** wskaźnika. Plik tymczasowy jest automatycznie usuwany po pliku jest zamykane, gdy program zakończy się normalnie lub **_rmtmp —** jest wywoływana przy założeniu, że nie zmienia bieżącego katalogu roboczego. Plik tymczasowy jest otwarty w **w + b** trybu (binarne odczyt/zapis).

Błąd może wystąpić, jeśli użytkownik podejmie więcej niż TMP_MAX (zobacz stdio —. H) wywołań w przypadku **tmpfile —**.

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

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[_rmtmp](rmtmp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
