---
title: tmpfile_s
ms.date: 4/2/2020
api_name:
- tmpfile_s
- _o_tmpfile_s
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- tmpfile_s
helpviewer_keywords:
- temporary files
- tmpfile_s function
- temporary files, creating
ms.assetid: 50879c69-215e-425a-a2a3-8b5467121eae
ms.openlocfilehash: 8f9dd58abdf1d3225341e40661c14ae3a5013257
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362459"
---
# <a name="tmpfile_s"></a>tmpfile_s

Tworzy plik tymczasowy. Jest to wersja [tmpfile](tmpfile.md) z ulepszeniami zabezpieczeń, jak opisano w [funkcji zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t tmpfile_s(
   FILE** pFilePtr
);
```

### <a name="parameters"></a>Parametry

*pFilePtr*<br/>
Adres wskaźnika do przechowywania adresu wygenerowanego wskaźnika do strumienia.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość 0, jeśli się powiedzie, kod błędu w przypadku awarii.

### <a name="error-conditions"></a>Warunki błędu

|*pFilePtr*|**Wartość zwracana**|**Zawartość**  *pFilePtr*|
|----------------|----------------------|---------------------------------|
|**Null**|**Einval**|nie zmieniono|

Jeśli wystąpi powyższy błąd sprawdzania poprawności parametru, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w obszarze [Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, **errno** jest ustawiona na **EINVAL,** a wartość zwracana to **EINVAL**.

## <a name="remarks"></a>Uwagi

Funkcja **tmpfile_s** tworzy plik tymczasowy i umieszcza wskaźnik do tego strumienia w *argumentorapfilu.* Plik tymczasowy jest tworzony w katalogu głównym. Aby utworzyć plik tymczasowy w katalogu innym niż katalog główny, należy użyć [tmpnam_s](tmpnam-s-wtmpnam-s.md) lub [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md) w połączeniu z [fopen](fopen-wfopen.md).

Jeśli nie można otworzyć pliku, **tmpfile_s** zapisuje **wartość NULL** do parametru *pFilePtr.* Ten plik tymczasowy jest automatycznie usuwany po zamknięciu pliku, gdy program kończy się normalnie lub gdy wywoływana jest **_rmtmp,** przy założeniu, że bieżący katalog roboczy nie ulegnie zmianie. Plik tymczasowy jest otwierany w trybie **w+b** (binarny odczyt/zapis).

Błąd może wystąpić, jeśli spróbujesz więcej niż **TMP_MAX_S** (patrz STDIO. H) połączenia z **tmpfile_s**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**tmpfile_s**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

> [!NOTE]
> W tym przykładzie może wymagać uprawnień administracyjnych do uruchomienia w systemie Windows.

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

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_rmtmp](rmtmp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
