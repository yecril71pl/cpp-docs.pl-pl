---
title: tmpnam_s, _wtmpnam_s
ms.date: 11/04/2016
apiname:
- tmpnam_s
- _wtmpnam_s
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
ms.openlocfilehash: 9bf994d16362ef461d8d25d72466721ba9a5890f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497490"
---
# <a name="tmpnams-wtmpnams"></a>tmpnam_s, _wtmpnam_s

Generowanie nazwy, których można użyć, aby utworzyć pliki tymczasowe. Są to wersje [tmpnam — i _wtmpnam —](tempnam-wtempnam-tmpnam-wtmpnam.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

Obie te funkcje zwracają 0, jeśli kończy się pomyślnie lub numer błędu w przypadku niepowodzenia.

### <a name="error-conditions"></a>Warunki błędów

|||||
|-|-|-|-|
|*str*|*sizeInChars*|**Wartość zwracana**|**Zawartość***str*|
|**NULL**|Wszystkie|**EINVAL**|Nie zmodyfikowano|
|Nie **NULL** (wskazuje prawidłowy pamięci)|zbyt krótki|**ERANGE**|Nie zmodyfikowano|

Jeśli *str* jest **NULL**, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** do **EINVAL** i zwracają **EINVAL**.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji zwraca nazwę pliku, który obecnie nie istnieje. **tmpnam_s —** zwraca nazwę na unikatowy w wyznaczonym katalogu tymczasowym Windows zwracane przez [GetTempPathW](/windows/desktop/api/fileapi/nf-fileapi-gettemppathw). Należy zauważyć, że jeśli nazwa pliku jest pre oczekującego ukośnik odwrotny i żadnych informacji o ścieżce, takie jak \fname21, oznacza to, że nazwa jest nieprawidłowa dla bieżącego katalogu roboczego.

Aby uzyskać **tmpnam_s —**, możesz zapisać tę nazwę wygenerowanego pliku w *str*. Maksymalna długość ciągu zwróconego przez **tmpnam_s —** jest **L_tmpnam_s**zdefiniowaną w stdio —. H. Jeśli *str* jest **NULL**, następnie **tmpnam_s —** pozostawia wynik w statycznych buforu wewnętrznego. Ten sposób kolejnych wywołań zniszczyć tę wartość. Nazwa wygenerowana przez **tmpnam_s —** zawiera nazwę pliku wygenerowanego przez program, a po pierwszym wywołaniu **tmpnam_s —**, rozszerzenie pliku numerów sekwencyjnych w podstawowej 32 (.1 .1vvvvvu, gdy **TMP _MAX_S** w stdio —. H jest **INT_MAX**).

**tmpnam_s —** obsługi znaków wielobajtowych argumenty typu string zgodnie z potrzebami, rozpoznawaniu sekwencje znaków wielobajtowych według stronę kodową OEM uzyskiwane automatycznie z systemu operacyjnego. **_wtmpnam_s —** to wersja znaku dwubajtowego **tmpnam_s —**; argument i wartość zwracana przez **_wtmpnam_s —** są ciągami znaków dwubajtowych. **_wtmpnam_s —** i **tmpnam_s —** zachowują się identycznie, chyba że **_wtmpnam_s —** nie obsługuje ciągi znaków wielobajtowych.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążania szablonu; przeciążenia mogą automatycznie wywnioskować długość buforu, eliminując konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam_s**|**tmpnam_s**|**tmpnam_s**|**_wtmpnam_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**tmpnam_s**|\<stdio.h>|
|**_wtmpnam_s**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[malloc](malloc.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
