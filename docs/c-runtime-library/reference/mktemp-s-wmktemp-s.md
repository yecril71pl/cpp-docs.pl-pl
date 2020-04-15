---
title: _mktemp_s, _wmktemp_s
ms.date: 4/2/2020
api_name:
- _mktemp_s
- _wmktemp_s
- _o__mktemp_s
- _o__wmktemp_s
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
ms.openlocfilehash: 061c5647b2c5a5e79b017cf93989f62ad19cfc0a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338754"
---
# <a name="_mktemp_s-_wmktemp_s"></a>_mktemp_s, _wmktemp_s

Tworzy unikatową nazwę pliku. Są to wersje [_mktemp, _wmktemp](mktemp-wmktemp.md) z ulepszeniami zabezpieczeń, jak opisano w [programie Funkcje zabezpieczeń w programie CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Rozmiar buforu w postaci jedno bajtowej **w _mktemp_s**; szerokich znaków **w _wmktemp_s**, w tym zerowego terminatora.

## <a name="return-value"></a>Wartość zwracana

Obie te funkcje zwracają zero na sukces; kod błędu w przypadku awarii.

### <a name="error-conditions"></a>Warunki błędu

|*nameTemplate*|*sizeInChars*|Wartość zwracana|Nowa wartość w *nazwieTemplate*|
|----------------|-------------------|----------------------|-------------------------------|
|**Null**|Wszelki|**Einval**|**Null**|
|Nieprawidłowy format (zobacz sekcję Uwagi, aby uzyskać poprawny format)|Wszelki|**Einval**|pusty ciąg znaków|
|Wszelki|<= liczba X|**Einval**|pusty ciąg znaków|

Jeśli wystąpi którykolwiek z powyższych warunków błędu, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [obszarze Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, **errno** jest ustawiona na **EINVAL** i funkcje zwraca **EINVAL**.

## <a name="remarks"></a>Uwagi

Funkcja **_mktemp_s** tworzy unikatową nazwę pliku, modyfikując argument *nameTemplate,* tak aby po wywołaniu wskaźnik *nameTemplate* wskazuje na ciąg zawierający nową nazwę pliku. **_mktemp_s** automatycznie obsługuje argumenty ciągów wielobajtowych, rozpoznając sekwencje znaków wielobajtowych zgodnie ze stroną kodową wielobajtową aktualnie używaną przez system czasu wykonywania. **_wmktemp_s** jest szerokoznakową wersją **_mktemp_s**; argumentem **_wmktemp_s** jest ciąg znaków o szerokim charakterze. **_wmktemp_s** i **_mktemp_s** zachowywać się identycznie inaczej, z tą różnicą, że **_wmktemp_s** nie obsługuje ciągów znaków wielobajtowych.

Wersje biblioteki debugowania tych funkcji najpierw wypełniają bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp_s**|**_mktemp_s**|**_mktemp_s**|**_wmktemp_s**|

Argument *nameTemplate* ma formę **baseXXXXXX**, gdzie *podstawa* jest częścią nowej nazwy pliku, którą podajesz, a każdy X jest symbolem zastępczym dla znaku dostarczonego przez **_mktemp_s**. Każdy znak zastępczy w *nazwieTemplate* musi być wielką literą X. **_mktemp_s** zachowuje *bazę* i zastępuje pierwszy znak x spływającym znakiem alfabetycznym. **_mktemp_s** zastępuje następujące końcowe X wartością pięciocyfrową; ta wartość jest unikatowy numer identyfikujący proces wywołujący lub w programach wielowątkowych, wątek wywołujący.

Każde udane wywołanie **_mktemp_s** modyfikuje *nazwęTemplate*. W każdym kolejnym wywołaniu z tego samego procesu lub wątku o tej samej *nazwieTemplate* **argument, _mktemp_s** sprawdza nazwy plików, które pasują do nazw zwracanych przez **_mktemp_s** w poprzednich wywołaniach. Jeśli dla danej nazwy nie istnieje żaden plik, **_mktemp_s** zwraca tę nazwę. Jeśli pliki istnieją dla wszystkich wcześniej zwróconych nazw, **_mktemp_s** tworzy nową nazwę, zastępując znak alfabetyczny używany we wcześniej zwróconej nazwie następną dostępną literą, w kolejności od "a" do "z". Na przykład, jeśli *podstawą* jest:

> **Fn**

a pięciocyfrowa wartość podana przez **_mktemp_s** wynosi 12345, imię zwrócone jest:

> **fna12345**

Jeśli ta nazwa jest używana do tworzenia pliku FNA12345 i ten plik nadal istnieje, następna nazwa zwrócona na wywołanie z tego samego procesu lub wątku o tej samej *podstawie* dla *nameTemplate* jest:

> **fnb12345**

Jeśli FNA12345 nie istnieje, następna zwrócona nazwa jest ponownie:

> **fna12345**

**_mktemp_s** może utworzyć maksymalnie 26 unikatowych nazw plików dla dowolnej kombinacji wartości *podstawowej* i *nameTemplate.* W związku z tym FNZ12345 jest ostatnią unikatową nazwą **pliku, _mktemp_s** można utworzyć dla *wartości podstawowej* i *nameTemplate* używane w tym przykładzie.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonu; przeciążenia można wywnioskować długość buforu automatycznie (eliminując konieczność określenia argumentu rozmiaru) i mogą automatycznie zastąpić starsze, niezabezpieczone funkcje z ich nowszych, bezpiecznych odpowiedników. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mktemp_s**|\<> io.h|
|**_wmktemp_s**|\<io.h> lub \<wchar.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_getpid](getpid.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
