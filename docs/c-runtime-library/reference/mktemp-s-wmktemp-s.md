---
title: _mktemp_s, _wmktemp_s
ms.date: 11/04/2016
apiname:
- _mktemp_s
- _wmktemp_s
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
- wmktemp_s
- mktemp_s
- _mktemp_s
- _wmktemp_s
helpviewer_keywords:
- _tmktemp_s function
- mktemp_s function
- _wmktemp_s function
- _mktemp_s function
- files [C++], temporary
- tmktemp_s function
- wmktemp_s function
- temporary files [C++]
ms.assetid: 92a7e269-7f3d-4c71-bad6-14bc827a451d
ms.openlocfilehash: fef10f2cfbcc0332741d560a41a782b70ed14798
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156541"
---
# <a name="mktemps-wmktemps"></a>_mktemp_s, _wmktemp_s

Tworzy unikatową nazwę pliku. Są to wersje [_mktemp —, _wmktemp —](mktemp-wmktemp.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t _mktemp_s(
   char *nameTemplate,
   size_t sizeInChars
);
errno_t _wmktemp_s(
   wchar_t *nameTemplate,
   size_t sizeInChars
);
template <size_t size>
errno_t _mktemp_s(
   char (&nameTemplate)[size]
); // C++ only
template <size_t size>
errno_t _wmktemp_s(
   wchar_t (&nameTemplate)[size]
); // C++ only
```

### <a name="parameters"></a>Parametry

*nameTemplate*<br/>
Wzorzec nazwy pliku.

*sizeInChars*<br/>
Rozmiar buforu w znaki jednobajtowe w **_mktemp_s —**; szerokie znaki w **_wmktemp_s —**, łącznie z terminatorem null.

## <a name="return-value"></a>Wartość zwracana

Obie te funkcje zwracają zero w przypadku powodzenia; Kod błędu.

### <a name="error-conditions"></a>Warunki błędów

|*nameTemplate*|*sizeInChars*|Wartość zwracana|Nowa wartość w *nametemplate innej*|
|----------------|-------------------|----------------------|-------------------------------|
|**NULL**|Wszystkie|**EINVAL**|**NULL**|
|Niepoprawny format (zobacz uwagi dotyczącej poprawny format)|Wszystkie|**EINVAL**|Pusty ciąg|
|Wszystkie|< = liczba x|**EINVAL**|Pusty ciąg|

Jeśli wystąpi dowolne z powyższych warunków błędu, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EINVAL** i funkcji zwraca **EINVAL**.

## <a name="remarks"></a>Uwagi

**_Mktemp_s —** funkcja tworzy unikatową nazwę pliku, modyfikując *nametemplate innej* argument, tak aby po wywołaniu metody, *nametemplate innej* wskaźnik wskazuje na ciąg zawierający nową nazwę pliku. **_mktemp_s —** automatycznie obsługuje argumenty ciągu znaków wielobajtowych zgodnie z potrzebami, rozpoznawaniu sekwencje znaków wielobajtowych zgodnie z aktualnie używaną stroną kodową wielobajtowych przez system w czasie wykonywania. **_wmktemp_s —** to wersja znaku dwubajtowego **_mktemp_s —**; argument **_wmktemp_s —** jest ciągiem znaku dwubajtowego. **_wmktemp_s —** i **_mktemp_s —** zachowują się identycznie, chyba że **_wmktemp_s —** nie obsługuje ciągi znaków wielobajtowych.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp_s**|**_mktemp_s**|**_mktemp_s**|**_wmktemp_s**|

*Nametemplate innej* argument ma postać **baseXXXXXX**, gdzie *podstawowy* jest częścią nową nazwę pliku, który podasz, a każda X jest symbolem zastępczym dla znak, który został dostarczony przez **_mktemp_s —**. Dla każdego znaku zastępczego *nametemplate innej* musi być wielkie X. **_mktemp_s —** zachowuje *podstawowy* i zamienia pierwszą X końcowe litery alfabetu. **_mktemp_s —** zastępuje następujące końcowe x o wartości 5 cyfrowy; ta wartość jest unikatowy numer identyfikujący wywołania procesu, lub w przypadku programów wielowątkowych wątku wywołującego.

Każde wywołanie pomyślne **_mktemp_s —** modyfikuje *nametemplate innej*. W każdym wywołaniu kolejnych ten sam proces lub wątek z takimi samymi *nametemplate innej* argument **_mktemp_s —** sprawdza, czy nazw plików, które odpowiadają nazwom zwrócony przez **_mktemp_s —** w poprzednich wywołań. Jeśli plik nie istnieje dla danej nazwy **_mktemp_s —** zwraca tę nazwę. Pliki, jeśli istnieją dla nazwy, wszystkie wcześniej zwrócony **_mktemp_s —** tworzy nową nazwę, zastępując znaku alfabetycznego go użyć w nazwie wcześniej zwrócony z na kolejne dostępne małe litery, w kolejności, od "" do "z". Na przykład jeśli *podstawowy* jest:

> **FN**

i wartość 5 cyfrowy dostarczonych przez **_mktemp_s —** 12345, imię, zwracany jest:

> **fna12345**

Jeśli ta nazwa jest używana w celu utworzenia pliku FNA12345 i ten plik nadal istnieje, następnej nazwy zwróciło w wywołaniu ten sam proces lub wątek z takimi samymi *podstawowy* dla *nametemplate innej* jest:

> **fnb12345**

Jeśli FNA12345 nie istnieje, następnej nazwy, zwracany jest ponownie:

> **fna12345**

**_mktemp_s —** może utworzyć maksymalnie 26 unikatowych nazw plików dla dowolnej podanej kombinacji *podstawowy* i *nametemplate innej* wartości. W związku z tym, FNZ12345 miał na nazwisko unikatowego pliku **_mktemp_s —** można utworzyć dla *podstawowy* i *nametemplate innej* wartości używanych w tym przykładzie.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążania szablonu; przeciążenia mogą automatycznie wywnioskować długość buforu (eliminując potrzebę określenia argumentu rozmiaru) oraz ich mogą automatycznie zastąpić starsze, niezabezpieczone funkcje ich nowsze, bezpieczne odpowiedniki. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mktemp_s**|\<io.h>|
|**_wmktemp_s**|\<IO.h > lub \<wchar.h >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```cpp
// crt_mktemp_s.cpp
/* The program uses _mktemp to create
* five unique filenames. It opens each filename
* to ensure that the next name is unique.
*/

#include <io.h>
#include <string.h>
#include <stdio.h>

char *fnTemplate = "fnXXXXXX";
char names[5][9];

int main()
{
   int i, err, sizeInChars;
   FILE *fp;

   for( i = 0; i < 5; i++ )
   {
      strcpy_s( names[i], sizeof(names[i]), fnTemplate );
      /* Get the size of the string and add one for the null terminator.*/
      sizeInChars = strnlen(names[i], 9) + 1;
      /* Attempt to find a unique filename: */
      err = _mktemp_s( names[i], sizeInChars );
      if( err != 0 )
         printf( "Problem creating the template" );
      else
      {
         if( fopen_s( &fp, names[i], "w" ) == 0 )
            printf( "Unique filename is %s\n", names[i] );
         else
            printf( "Cannot open %s\n", names[i] );
         fclose( fp );
      }
   }

   return 0;
}
```

### <a name="sample-output"></a>Przykładowe dane wyjściowe

```Output
Unique filename is fna03188
Unique filename is fnb03188
Unique filename is fnc03188
Unique filename is fnd03188
Unique filename is fne03188
```

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_getpid](getpid.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
