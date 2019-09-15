---
title: tmpnam_s, _wtmpnam_s
ms.date: 11/04/2016
api_name:
- tmpnam_s
- _wtmpnam_s
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
- tmpnam_s
- _wtmpnam_s
- L_tmpnam_s
helpviewer_keywords:
- tmpnam_s function
- file names [C++], creating temporary
- _wtmpnam_s function
- L_tmpnam_s constant
- temporary files, creating
- file names [C++], temporary
- wtmpnam_s function
ms.assetid: e70d76dc-49f5-4aee-bfa2-f1baa2bcd29f
ms.openlocfilehash: 847df0d2369857d009c39b4dd61adce45094899c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946045"
---
# <a name="tmpnam_s-_wtmpnam_s"></a>tmpnam_s, _wtmpnam_s

Generuj nazwy, których można użyć do tworzenia plików tymczasowych. Są to wersje systemów [tmpnam i _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md) z ulepszeniami zabezpieczeń opisanymi w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t tmpnam_s(
   char * str,
   size_t sizeInChars
);
errno_t _wtmpnam_s(
   wchar_t *str,
   size_t sizeInChars
);
template <size_t size>
errno_t tmpnam_s(
   char (&str)[size]
); // C++ only
template <size_t size>
errno_t _wtmpnam_s(
   wchar_t (&str)[size]
); // C++ only
```

### <a name="parameters"></a>Parametry

*str*<br/>
Wskaźnik, który będzie przechowywać wygenerowaną nazwę.

*sizeInChars*<br/>
Rozmiar buforu w znakach.

## <a name="return-value"></a>Wartość zwracana

Obie te funkcje zwracają wartość 0, jeśli powodzenie lub wystąpił błąd w przypadku niepowodzenia.

### <a name="error-conditions"></a>Warunki błędów

|||||
|-|-|-|-|
|*str*|*sizeInChars*|**Wartość zwracana**|**Zawartość** *str*|
|**NULL**|Ile|**EINVAL**|nie zmodyfikowano|
|Nie **ma wartości null** (wskazuje na prawidłową pamięć)|zbyt krótki|**ERANGE**|nie zmodyfikowano|

Jeśli *str* ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** na **EINVAL** i zwracają **EINVAL**.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji zwraca nazwę pliku, który obecnie nie istnieje. **tmpnam_s** zwraca nazwę unikatową w wydzielonym katalogu tymczasowym systemu Windows zwróconym przez [GetTempPathW](/windows/win32/api/fileapi/nf-fileapi-gettemppathw). Zwróć uwagę, że nazwa pliku jest wstępnie zainstalowana z ukośnikiem odwrotnym i bez informacji o ścieżce, takich jak \fname21, oznacza to, że nazwa jest prawidłowa dla bieżącego katalogu roboczego.

W przypadku **tmpnam_s**można zapisać tę wygenerowaną nazwę pliku w *str*. Maksymalna długość ciągu zwracanego przez **tmpnam_s** to **L_tmpnam_s**, zdefiniowany w stdio. C. Jeśli *str* ma **wartość null**, **tmpnam_s** pozostawia wynik w wewnętrznym buforze statycznym. W ten sposób wszystkie kolejne wywołania powodują zniszczenie tej wartości. Nazwa wygenerowana przez **tmpnam_s** składa się z nazwy pliku generowanej przez program i, po pierwszym wywołaniu do **tmpnam_s**, rozszerzenie pliku numerów sekwencyjnych w podstawowej 32 (. 1-. 1vvvvvu, gdy **TMP_MAX_S** w stdio. H to **INT_MAX**).

**tmpnam_s** automatycznie obsługuje argumenty ciągu znaków wielobajtowych, aby rozpoznawać sekwencje znaków wielobajtowych zgodnie ze stroną kodową OEM uzyskaną od systemu operacyjnego. **_wtmpnam_s** to dwubajtowa wersja **tmpnam_s**; argument i wartość zwracana przez **_wtmpnam_s** są ciągami znaków dwubajtowych. **_wtmpnam_s** i **tmpnam_s** zachowują się identycznie, z tą różnicą, że **_wtmpnam_s** nie obsługują ciągów znaków wielobajtowych.

W C++programie korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonów; przeciążenia mogą automatycznie wywnioskować długość buforu, eliminując konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam_s**|**tmpnam_s**|**tmpnam_s**|**_wtmpnam_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**tmpnam_s**|\<stdio.h>|
|**_wtmpnam_s**|\<stdio. h > lub \<WCHAR. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_tmpnam_s.c
// This program uses tmpnam_s to create a unique filename in the
// current working directory.
//

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char name1[L_tmpnam_s];
   errno_t err;
   int i;

   for (i = 0; i < 15; i++)
   {
      err = tmpnam_s( name1, L_tmpnam_s );
      if (err)
      {
         printf("Error occurred creating unique filename.\n");
         exit(1);
      }
      else
      {
         printf( "%s is safe to use as a temporary file.\n", name1 );
      }
   }
}
```

```Output
C:\Users\LocalUser\AppData\Local\Temp\u19q8.0 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.1 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.2 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.3 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.4 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.5 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.6 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.7 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.8 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.9 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.a is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.b is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.c is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.d is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.e is safe to use as a temporary file.
```

## <a name="see-also"></a>Zobacz także

[We/wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[malloc](malloc.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
