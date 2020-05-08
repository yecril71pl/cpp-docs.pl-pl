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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 48c599887a8a903d52c7dcd46b98046119c9d3ad
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919935"
---
# <a name="tmpfile_s"></a>tmpfile_s

Tworzy plik tymczasowy. Jest to wersja [tmpfile](tmpfile.md) z ulepszeniami zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

Zwraca wartość 0, jeśli to się powiedzie, kod błędu w przypadku niepowodzenia.

### <a name="error-conditions"></a>Warunki błędów

|*pFilePtr*|**Wartość zwracana**|**Zawartość**  *pFilePtr*|
|----------------|----------------------|---------------------------------|
|**NULL**|**EINVAL**|nie zmieniono|

Jeśli wystąpi błąd walidacji powyższego parametru, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na **EINVAL** , a zwracana wartość to **EINVAL**.

## <a name="remarks"></a>Uwagi

Funkcja **tmpfile_s** tworzy plik tymczasowy i umieszcza wskaźnik do tego strumienia w argumencie *pFilePtr* . Plik tymczasowy zostanie utworzony w katalogu głównym. Aby utworzyć plik tymczasowy w katalogu innym niż główny, użyj [tmpnam_s](tmpnam-s-wtmpnam-s.md) lub [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md) w połączeniu z [fopen](fopen-wfopen.md).

Jeśli nie można otworzyć pliku, **tmpfile_s** zapisuje **wartości null** w parametrze *pFilePtr* . Ten plik tymczasowy jest automatycznie usuwany po zamknięciu pliku, gdy program kończy się normalnie lub gdy **_rmtmp** jest wywoływana, przy założeniu, że bieżący katalog roboczy nie zmienia się. Plik tymczasowy jest otwierany w trybie w **+ b** (binarny odczyt/zapis).

Błąd może wystąpić, Jeśli podjęto próbę więcej niż **TMP_MAX_S** (zobacz stdio. H) wywołuje **tmpfile_s**.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**tmpfile_s**|\<stdio. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

> [!NOTE]
> Ten przykład może wymagać uprawnień administracyjnych do uruchamiania w systemie Windows.

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
