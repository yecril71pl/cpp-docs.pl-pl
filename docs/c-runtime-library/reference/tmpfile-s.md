---
title: tmpfile_s
ms.date: 11/04/2016
apiname:
- tmpfile_s
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
- tmpfile_s
helpviewer_keywords:
- temporary files
- tmpfile_s function
- temporary files, creating
ms.assetid: 50879c69-215e-425a-a2a3-8b5467121eae
ms.openlocfilehash: 341e1c8ed6dd20ec7e6a3d71999fb365e45e614a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488117"
---
# <a name="tmpfiles"></a>tmpfile_s

Tworzy plik tymczasowy. Jest to wersja programu [tmpfile —](tmpfile.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t tmpfile_s(
   FILE** pFilePtr
);
```

### <a name="parameters"></a>Parametry

*pFilePtr*<br/>
Adres wskaźnika do przechowywania adres wygenerowanego wskaźnika do strumienia.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0, jeśli to się powiedzie, kod błędu.

### <a name="error-conditions"></a>Warunki błędów

|*pFilePtr*|**Wartość zwracana**|**Zawartość***pFilePtr* |
|----------------|----------------------|---------------------------------|
|**NULL**|**EINVAL**|nie zmienione|

Jeśli powyższe parametr wystąpienia błędu sprawdzania poprawności, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EINVAL** i wartość zwracana jest **EINVAL**.

## <a name="remarks"></a>Uwagi

**Tmpfile_s —** funkcji utworzy plik tymczasowy i umieszcza wskaźnik do tego strumienia w *pFilePtr* argumentu. Plik tymczasowy zostanie utworzony w katalogu głównym. Aby utworzyć pliku tymczasowego w katalogu innym niż katalog główny, użyj [tmpnam_s —](tmpnam-s-wtmpnam-s.md) lub [tempnam —](tempnam-wtempnam-tmpnam-wtmpnam.md) w połączeniu z [fopen —](fopen-wfopen.md).

Jeśli nie można otworzyć pliku, **tmpfile_s —** zapisuje **NULL** do *pFilePtr* parametru. Plik tymczasowy jest automatycznie usuwany po pliku jest zamykane, gdy program zakończy się normalnie lub **_rmtmp —** jest wywoływana przy założeniu, że nie zmienia bieżącego katalogu roboczego. Plik tymczasowy jest otwarty w **w + b** trybu (binarne odczyt/zapis).

Błąd może wystąpić, jeśli użytkownik podejmie więcej niż **TMP_MAX_S** (zobacz stdio —. H) wywołań w przypadku **tmpfile_s —**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**tmpfile_s**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

> [!NOTE]
> W tym przykładzie może wymagać uprawnień administracyjnych, systemem Windows.

```C
// crt_tmpfile_s.c
// This program uses tmpfile_s to create a
// temporary file, then deletes this file with _rmtmp.
//

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char tempstring[] = "String to be written";
   int  i;
   errno_t err;

   // Create temporary files.
   for( i = 1; i <= 3; i++ )
   {
      err = tmpfile_s(&stream);
      if( err )
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
