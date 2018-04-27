---
title: tmpfile_s — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- temporary files
- tmpfile_s function
- temporary files, creating
ms.assetid: 50879c69-215e-425a-a2a3-8b5467121eae
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 57c230dedd3415a272e168b586a16ccb03f5d29a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="tmpfiles"></a>tmpfile_s

Tworzy plik tymczasowy. Jest to wersja z [tmpfile —](tmpfile.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

Zwraca wartość 0, jeśli to się powiedzie, kod błędu w przypadku awarii.

### <a name="error-conditions"></a>Warunki błędów

|*pFilePtr*|**Wartość zwracana**|**Zawartość***pFilePtr* |
|----------------|----------------------|---------------------------------|
|**NULL**|**EINVAL —**|nie został zmieniony|

Jeśli wystąpi błąd sprawdzania poprawności parametru powyżej, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **errno** ustawiono **einval —** i jest zwracana wartość **einval —**.

## <a name="remarks"></a>Uwagi

**Tmpfile_s —** funkcja powoduje utworzenie pliku tymczasowego i umieszcza wskaźnik do tego strumienia w *pFilePtr* argumentu. Plik tymczasowy zostanie utworzony w katalogu głównym. Aby utworzyć pliku tymczasowego w katalogu innym niż katalog główny, użyj [tmpnam_s —](tmpnam-s-wtmpnam-s.md) lub [tempnam —](tempnam-wtempnam-tmpnam-wtmpnam.md) w połączeniu z [fopen —](fopen-wfopen.md).

Jeśli nie można otworzyć pliku, **tmpfile_s —** zapisuje **NULL** do *pFilePtr* parametru. Plik tymczasowy jest automatycznie usuwana, gdy plik jest zamknięty, gdy program zakończenie zwykle lub **_rmtmp —** jest wywoływana przy założeniu, że bieżący katalog roboczy nie ulega zmianie. Plik tymczasowy jest otwarty w **w + b** trybu (binarne odczytu/zapisu).

Błąd może wystąpić przy próbie więcej niż **TMP_MAX_S** (zobacz stdio —. H) wywołania z **tmpfile_s —**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**tmpfile_s**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

> [!NOTE]
> W tym przykładzie może wymagać uprawnień administracyjnych dla systemu Windows.

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

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_rmtmp](rmtmp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
