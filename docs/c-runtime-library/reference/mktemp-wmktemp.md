---
title: _mktemp, _wmktemp
ms.date: 11/04/2016
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
ms.openlocfilehash: 9dbaba9e4a68523c0d79762c6a7ff54c238e397d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554179"
---
# <a name="mktemp-wmktemp"></a>_mktemp, _wmktemp

Tworzy unikatową nazwę pliku. Bardziej bezpieczne wersje tych funkcji są dostępne; zobacz [_mktemp_s —, _wmktemp_s —](mktemp-s-wmktemp-s.md).

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

Każda z tych funkcji zwraca wskaźnik do modyfikacji nametemplate innej. Funkcja zwraca **NULL** Jeśli *nametemplate innej* jest nieprawidłowo sformułowana lub nie ma więcej unikatowych nazw mogą być tworzone z danym nametemplate innej.

## <a name="remarks"></a>Uwagi

**_Mktemp —** funkcja tworzy unikatową nazwę pliku, modyfikując *nametemplate innej* argumentu. **_mktemp —** automatycznie obsługuje argumenty ciągu znaków wielobajtowych zgodnie z potrzebami, rozpoznawaniu sekwencje znaków wielobajtowych zgodnie z aktualnie używaną stroną kodową wielobajtowych przez system w czasie wykonywania. **_wmktemp —** to wersja znaku dwubajtowego **_mktemp —**; argument i wartość zwracana przez **_wmktemp —** są ciągami znaków dwubajtowych. **_wmktemp —** i **_mktemp —** zachowują się identycznie, chyba że **_wmktemp —** nie obsługuje ciągi znaków wielobajtowych.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp —**|**_mktemp**|**_mktemp**|**_wmktemp**|

*Nametemplate innej* argument ma postać *podstawowy ** XXXXXX*, gdzie *podstawowy* jest częścią nową nazwę pliku, który podasz, a każda X jest symbolem zastępczym dla znak, który został dostarczony przez **_mktemp —**. Dla każdego znaku zastępczego *nametemplate innej* musi być wielkie X. **_mktemp —** zachowuje *podstawowy* i zamienia pierwszą X końcowe litery alfabetu. **_mktemp —** zastępuje następujące końcowe x o wartości 5 cyfrowy; ta wartość jest unikatowy numer identyfikujący wywołania procesu, lub w przypadku programów wielowątkowych wątku wywołującego.

Każde wywołanie pomyślne **_mktemp —** modyfikuje *nametemplate innej*. W każdym wywołaniu kolejnych ten sam proces lub wątek z takimi samymi *nametemplate innej* argument **_mktemp —** sprawdza, czy nazw plików, które odpowiadają nazwom zwrócony przez **_mktemp —** w poprzednie wywołania. Jeśli plik nie istnieje dla danej nazwy **_mktemp —** zwraca tę nazwę. Pliki, jeśli istnieją dla nazwy, wszystkie wcześniej zwrócony **_mktemp —** tworzy nową nazwę, zastępując znaku alfabetycznego go użyć w nazwie wcześniej zwrócony z na kolejne dostępne małe litery, w kolejności, od "" do "z". Na przykład jeśli *podstawowy* jest:

> **FN**

i wartość 5 cyfrowy dostarczonych przez **_mktemp —** 12345, imię, zwracany jest:

> **fna12345**

Jeśli ta nazwa jest używana w celu utworzenia pliku FNA12345 i ten plik nadal istnieje, następnej nazwy zwróciło w wywołaniu ten sam proces lub wątek z takimi samymi *podstawowy* dla *nametemplate innej* jest:

> **fnb12345**

Jeśli FNA12345 nie istnieje, następnej nazwy, zwracany jest ponownie:

> **fna12345**

**_mktemp —** może utworzyć maksymalnie 26 unikatowych nazw plików dla dowolnej podanej kombinacji *podstawowy* i *nametemplate innej* wartości. W związku z tym, FNZ12345 miał na nazwisko unikatowego pliku **_mktemp —** można utworzyć dla *podstawowy* i *nametemplate innej* wartości używanych w tym przykładzie.

W przypadku awarii **errno** jest ustawiona. Jeśli *nametemplate innej* ma nieprawidłowy format (na przykład, mniej niż 6 x), **errno** ustawiono **EINVAL**. Jeśli **_mktemp —** nie można utworzyć unikatowej nazwy, ponieważ wszystkie 26 nazwy pliku możliwe już istnieje, **_mktemp —** ustawia nametemplate innej pusty ciąg i zwraca **EEXIST**.

W języku C++ funkcje te mają przeciążenia szablonu, które wywołują nowsze, bezpieczne odpowiedniki tych funkcji. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mktemp**|\<io.h>|
|**_wmktemp**|\<IO.h > lub \<wchar.h >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
