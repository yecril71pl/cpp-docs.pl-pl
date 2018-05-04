---
title: _mktemp_s —, _wmktemp_s — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
apitype: DLLExport
f1_keywords:
- wmktemp_s
- mktemp_s
- _mktemp_s
- _wmktemp_s
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0ed525f44150943496cddde57699035d8b62b6d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="mktemps-wmktemps"></a>_mktemp_s, _wmktemp_s

Tworzy unikatową nazwę pliku. Są to wersje [_mktemp —, _wmktemp —](mktemp-wmktemp.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*nametemplate innej*<br/>
Wzorzec nazwy pliku.

*sizeInChars*<br/>
Rozmiar buforu w znaki jednobajtowe w **_mktemp_s —**; szerokości znaków **_wmktemp_s —**, włącznie z terminatorem null.

## <a name="return-value"></a>Wartość zwracana

Obie te funkcje zwracać zera w przypadku powodzenia; błąd o kodzie błędu.

### <a name="error-conditions"></a>Warunki błędów

|*nametemplate innej*|*sizeInChars*|Wartość zwracana|Nowa wartość w *nametemplate innej*|
|----------------|-------------------|----------------------|-------------------------------|
|**NULL**|wszystkie|**EINVAL —**|**NULL**|
|Niepoprawny format (zobacz uwagi sekcji poprawny format)|wszystkie|**EINVAL —**|Pusty ciąg|
|wszystkie|< = liczba x|**EINVAL —**|Pusty ciąg|

Jeśli dowolne z powyższych warunków błąd wystąpi, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **errno** ustawiono **einval —** i funkcji zwraca **einval —**.

## <a name="remarks"></a>Uwagi

**_Mktemp_s —** funkcja tworzy unikatową nazwę pliku, modyfikując *nametemplate innej* argumentu, tak aby po wywołaniu metody, *nametemplate innej* wskazuje wskaźnik do ciągu zawierający nową nazwę pliku. **_mktemp_s —** automatycznie obsługuje argumentów ciągów znaków wielobajtowych zgodnie z potrzebami, rozpoznawanie wielobajtowych sekwencji znaków zgodnie z aktualnie używanej strony kodowe wielobajtowe przez system czasu wykonywania. **_wmktemp_s —** jest wersja znaków dwubajtowych **_mktemp_s —**; argument **_wmktemp_s —** jest ciągiem znaków dwubajtowych. **_wmktemp_s —** i **_mktemp_s —** zachowują się tak samo w przeciwnym razie wartość, z wyjątkiem **_wmktemp_s —** nie obsługuje ciągów znaków wielobajtowych.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp_s —**|**_mktemp_s**|**_mktemp_s**|**_wmktemp_s**|

*Nametemplate innej* argument ma postać **baseXXXXXX**, gdzie *podstawowej* jest częścią nową nazwę pliku, który znasz i każdego X jest symbolem zastępczym dla znaku dostarczone przez **_mktemp_s —**. Dla każdego znaku zastępczego *nametemplate innej* musi być X. wielkie litery **_mktemp_s —** zachowuje *podstawowej* i zamienia pierwszy X końcowe znakiem alfabetycznym. **_mktemp_s —** zastępuje następujące kończyć znakiem x o wartości 5 cyfrowy; ta wartość jest unikatowy numer identyfikujący wywołania proces, lub w programów wielowątkowych wątek wywołujący.

Każde wywołanie pomyślnie **_mktemp_s —** modyfikuje *nametemplate innej*. W każdym wywołaniu kolejne z tej samej proces lub wątek o takim samym *nametemplate innej* argumentu, **_mktemp_s —** sprawdza, czy nazwy plików, które odpowiadają nazwom zwrócony przez **_mktemp_s —** w poprzednich wywołań. Jeśli plik nie istnieje dla podanej nazwy, **_mktemp_s —** zwraca tę nazwę. Jeśli pliki znajdują się na wcześniej zostały zwrócone wszystkie nazwy, **_mktemp_s —** tworzy nową nazwę, zastępując alfabetu on w nazwie poprzednio zwróconych z na kolejne dostępne małe litery, w kolejności od "" do "z". Na przykład jeśli *podstawowej* jest:

> **FN**

i wartości 5 cyfrowy dostarczonych przez **_mktemp_s —** 12345, imię, zwracana jest:

> **fna12345**

Jeśli ta nazwa jest używana do utworzenia pliku FNA12345 i ten plik nadal istnieje, następnej nazwy zwrócił na połączenie z tym samym proces lub wątek o tej samej *podstawowej* dla *nametemplate innej* jest:

> **fnb12345**

Jeśli FNA12345 nie istnieje, zwracana nazwa dalej jest ponownie:

> **fna12345**

**_mktemp_s —** można utworzyć maksymalnie 26 unikatowe nazwy plików w dowolnej kombinacji danego *podstawowej* i *nametemplate innej* wartości. W związku z tym FNZ12345 jest unikatowy plik nazwisko **_mktemp_s —** można tworzyć dla *podstawowej* i *nametemplate innej* wartości używane w tym przykładzie.

W języku C++ za pomocą tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można automatycznie rozpoznać długość buforu (wyeliminowanie konieczności określania argumentem rozmiaru) i automatycznie można zastąpić starszą, które nie są bezpieczne funkcje z ich odpowiedniki nowsza, bezpieczne. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mktemp_s**|\<io.h>|
|**_wmktemp_s**|\<IO.h > lub \<wchar.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
