---
title: _mktemp —, _wmktemp — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wmktemp
- _mktemp
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
- _tmktemp
- wmktemp
- tmktemp
- _wmktemp
- _mktemp
dev_langs:
- C++
helpviewer_keywords:
- _wmktemp function
- _mktemp function
- files [C++], temporary
- tmktemp function
- _tmktemp function
- wmktemp function
- mktemp function
- temporary files [C++]
ms.assetid: 055eb539-a8c2-4a7d-be54-f5b6d1eb5c85
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 087348b3cc59fb1b47699fc0e64f533c22d992b4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="mktemp-wmktemp"></a>_mktemp, _wmktemp

Tworzy unikatową nazwę pliku. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [_mktemp_s —, _wmktemp_s —](mktemp-s-wmktemp-s.md).

## <a name="syntax"></a>Składnia

```C
char *_mktemp(
   char *nameTemplate
);
wchar_t *_wmktemp(
   wchar_t *nameTemplate
);
template <size_t size>
char *_mktemp(
   char (&nameTemplate)[size]
); // C++ only
template <size_t size>
wchar_t *_wmktemp(
   wchar_t (&nameTemplate)[size]
); // C++ only
```

### <a name="parameters"></a>Parametry

*nametemplate innej*<br/>
Wzorzec nazwy pliku.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wskaźnik do modyfikacji nametemplate innej. Funkcja zwraca **NULL** Jeśli *nametemplate innej* jest nieprawidłowo sformatowany lub unikatowych nazw nie mogą być tworzone z danym nametemplate innej.

## <a name="remarks"></a>Uwagi

**_Mktemp —** funkcja tworzy unikatową nazwę pliku, modyfikując *nametemplate innej* argumentu. **_mktemp —** automatycznie obsługuje argumentów ciągów znaków wielobajtowych zgodnie z potrzebami, rozpoznawanie wielobajtowych sekwencji znaków zgodnie z aktualnie używanej strony kodowe wielobajtowe przez system czasu wykonywania. **_wmktemp —** jest wersja znaków dwubajtowych **_mktemp —**; argumentów i wartości **_wmktemp —** są ciągami znaków dwubajtowych. **_wmktemp —** i **_mktemp —** zachowują się tak samo w przeciwnym razie wartość, z wyjątkiem **_wmktemp —** nie obsługuje ciągów znaków wielobajtowych.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp —**|**_mktemp**|**_mktemp**|**_wmktemp**|

*Nametemplate innej* argument ma postać *podstawowej ** XXXXXX*, gdzie *podstawowej* jest częścią nową nazwę pliku, który znasz i każdego X jest symbolem zastępczym dla znaku dostarczone przez **_mktemp —**. Dla każdego znaku zastępczego *nametemplate innej* musi być X. wielkie litery **_mktemp —** zachowuje *podstawowej* i zamienia pierwszy X końcowe znakiem alfabetycznym. **_mktemp —** zastępuje następujące kończyć znakiem x o wartości 5 cyfrowy; ta wartość jest unikatowy numer identyfikujący wywołania proces, lub w programów wielowątkowych wątek wywołujący.

Każde wywołanie pomyślnie **_mktemp —** modyfikuje *nametemplate innej*. W każdym wywołaniu kolejne z tej samej proces lub wątek o takim samym *nametemplate innej* argumentu, **_mktemp —** sprawdza, czy nazwy plików, które odpowiadają nazwom zwrócony przez **_mktemp —** w poprzednich wywołań. Jeśli plik nie istnieje dla podanej nazwy, **_mktemp —** zwraca tę nazwę. Jeśli pliki znajdują się na wcześniej zostały zwrócone wszystkie nazwy, **_mktemp —** tworzy nową nazwę, zastępując alfabetu on w nazwie poprzednio zwróconych z na kolejne dostępne małe litery, w kolejności od "" do "z". Na przykład jeśli *podstawowej* jest:

> **FN**

i wartości 5 cyfrowy dostarczonych przez **_mktemp —** 12345, imię, zwracana jest:

> **fna12345**

Jeśli ta nazwa jest używana do utworzenia pliku FNA12345 i ten plik nadal istnieje, następnej nazwy zwrócił na połączenie z tym samym proces lub wątek o tej samej *podstawowej* dla *nametemplate innej* jest:

> **fnb12345**

Jeśli FNA12345 nie istnieje, zwracana nazwa dalej jest ponownie:

> **fna12345**

**_mktemp —** można utworzyć maksymalnie 26 unikatowe nazwy plików w dowolnej kombinacji danego *podstawowej* i *nametemplate innej* wartości. W związku z tym FNZ12345 jest unikatowy plik nazwisko **_mktemp —** można tworzyć dla *podstawowej* i *nametemplate innej* wartości używane w tym przykładzie.

W przypadku awarii **errno** jest ustawiona. Jeśli *nametemplate innej* ma nieprawidłowy format (na przykład mniej niż 6 x), **errno** ustawiono **einval —**. Jeśli **_mktemp —** nie może utworzyć unikatową nazwę, ponieważ istnieją już wszystkie 26 nazwy pliku to możliwe, **_mktemp —** ustawia nametemplate innej pustym ciągiem i zwraca **eexist —**.

W języku C++ te funkcje mają przeciążenia szablonu, które wywołują odpowiedników nowsza, bezpieczne tych funkcji. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mktemp**|\<io.h>|
|**_wmktemp**|\<IO.h > lub \<wchar.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_mktemp.c
// compile with: /W3
/* The program uses _mktemp to create
* unique filenames. It opens each filename
* to ensure that the next name is unique.
*/

#include <io.h>
#include <string.h>
#include <stdio.h>
#include <errno.h>

char *template = "fnXXXXXX";
char *result;
char names[27][9];

int main( void )
{
   int i;
   FILE *fp;

   for( i = 0; i < 27; i++ )
   {
      strcpy_s( names[i], sizeof( names[i] ), template );
      /* Attempt to find a unique filename: */
      result = _mktemp( names[i] );  // C4996
      // Note: _mktemp is deprecated; consider using _mktemp_s instead
      if( result == NULL )
      {
         printf( "Problem creating the template\n" );
         if (errno == EINVAL)
         {
             printf( "Bad parameter\n");
         }
         else if (errno == EEXIST)
         {
             printf( "Out of unique filenames\n");
         }
      }
      else
      {
         fopen_s( &fp, result, "w" );
         if( fp != NULL )
            printf( "Unique filename is %s\n", result );
         else
            printf( "Cannot open %s\n", result );
         fclose( fp );
      }
   }
}
```

```Output
Unique filename is fna03912
Unique filename is fnb03912
Unique filename is fnc03912
Unique filename is fnd03912
Unique filename is fne03912
Unique filename is fnf03912
Unique filename is fng03912
Unique filename is fnh03912
Unique filename is fni03912
Unique filename is fnj03912
Unique filename is fnk03912
Unique filename is fnl03912
Unique filename is fnm03912
Unique filename is fnn03912
Unique filename is fno03912
Unique filename is fnp03912
Unique filename is fnq03912
Unique filename is fnr03912
Unique filename is fns03912
Unique filename is fnt03912
Unique filename is fnu03912
Unique filename is fnv03912
Unique filename is fnw03912
Unique filename is fnx03912
Unique filename is fny03912
Unique filename is fnz03912
Problem creating the template.
Out of unique filenames.
```

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_getpid](getpid.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[tmpfile](tmpfile.md)<br/>
