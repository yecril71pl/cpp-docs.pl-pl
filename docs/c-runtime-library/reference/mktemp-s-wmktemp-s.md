---
title: _mktemp_s, _wmktemp_s
ms.date: 11/04/2016
api_name:
- _mktemp_s
- _wmktemp_s
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
ms.openlocfilehash: 464f0dfbdb0b84e1fd29ec650e53f5c2543c4403
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624209"
---
# <a name="_mktemp_s-_wmktemp_s"></a>_mktemp_s, _wmktemp_s

Tworzy unikatową nazwę pliku. Są to wersje [_mktemp, _wmktemp](mktemp-wmktemp.md) z ulepszeniami zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Rozmiar buforu w znakach jednobajtowych w **_mktemp_s**; znaki dwubajtowe w **_wmktemp_s**, w tym terminator o wartości null.

## <a name="return-value"></a>Wartość zwracana

Obie te funkcje zwracają zero po sukcesie; kod błędu w przypadku niepowodzenia.

### <a name="error-conditions"></a>Warunki błędów

|*nameTemplate*|*sizeInChars*|Wartość zwracana|Nowa wartość w *nameTemplate*|
|----------------|-------------------|----------------------|-------------------------------|
|**NULL**|Ile|**EINVAL**|**NULL**|
|Niepoprawny format (patrz sekcja uwagi w poszukiwaniu poprawnego formatu)|Ile|**EINVAL**|Pusty ciąg|
|Ile|< = liczba elementów X|**EINVAL**|Pusty ciąg|

Jeśli wystąpi którykolwiek z powyższych warunków błędu, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na **EINVAL** , a funkcje zwracają **EINVAL**.

## <a name="remarks"></a>Uwagi

Funkcja **_mktemp_s** tworzy unikatową nazwę pliku, modyfikując argument *nameTemplate* , tak że po wywołaniu, wskaźnik *nameTemplate* wskazuje ciąg zawierający nową nazwę pliku. **_mktemp_s** automatycznie obsługuje argumenty ciągu znaków wielobajtowych, aby rozpoznawać sekwencje znaków wielobajtowych zgodnie ze stroną kodową wielobajtowego aktualnie używaną przez system czasu wykonywania. **_wmktemp_s** to dwubajtowa wersja **_mktemp_s**; argument **_wmktemp_s** jest ciągiem znaków dwubajtowych. **_wmktemp_s** i **_mktemp_s** zachowują się identycznie, z tą różnicą, że **_wmktemp_s** nie obsługują ciągów znaków wielobajtowych.

Wersje biblioteki debugowania tych funkcji najpierw wypełniają bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp_s**|**_mktemp_s**|**_mktemp_s**|**_wmktemp_s**|

Argument *nameTemplate* ma postać **baseXXXXXX**, gdzie *Base* jest częścią nowej nazwy pliku, która jest dostarczana, a każdy X jest symbolem zastępczym dla znaku dostarczonego przez **_mktemp_s**. Każdy znak zastępczy w *nameTemplate* musi być wielką literą x. **_mktemp_s** zachowuje *podstawową* i zastępuje pierwsze końcowe X znakiem alfabetycznym. **_mktemp_s** zastępuje następujące znaki końcowe X wartością z pięciu cyfr; Ta wartość jest unikatowym numerem identyfikującym proces wywołujący lub w programach wielowątkowych, wątek wywołujący.

Każde pomyślne wywołanie **_mktemp_s** modyfikuje *nameTemplate*. W każdym kolejnym wywołaniu z tego samego procesu lub wątku z tym samym argumentem nameTemplate **_mktemp_s** sprawdza nazwy plików, które są zgodne z nazwami zwracanymi przez **_mktemp_s** w poprzednich wywołaniach. Jeśli plik nie istnieje dla danej nazwy, **_mktemp_s** zwraca tę nazwę. Jeśli istnieją pliki dla wszystkich poprzednio zwróconych nazw, **_mktemp_s** tworzy nową nazwę przez zastąpienie znaku alfabetycznego, który został użyty w wcześniej zwróconej nazwie z następną dostępną małą literą, w kolejności od "a" do "z". Na przykład jeśli *podstawowa* :

> **Fn**

i pięć cyfr dostarczonych przez **_mktemp_s** to 12345, pierwsza zwrócona nazwa:

> **fna12345**

Jeśli ta nazwa jest używana do tworzenia pliku FNA12345, a ten plik nadal istnieje, następna nazwa zwrócona przez wywołanie z tego samego procesu lub wątku z tą samą *podstawą* dla *nameTemplate* jest:

> **fnb12345**

Jeśli FNA12345 nie istnieje, zwracana jest kolejna Nazwa:

> **fna12345**

**_mktemp_s** może utworzyć maksymalnie 26 unikatowych nazw plików dla każdej kombinacji wartości *podstawowych* i *nameTemplate* . W związku z tym FNZ12345 jest ostatnią unikatową nazwą pliku **_mktemp_s** można utworzyć dla wartości *podstawowych* i *nameTemplate* użytych w tym przykładzie.

W C++programie korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonów; przeciążenia mogą automatycznie wywnioskować długość buforu (eliminując konieczność określenia argumentu rozmiaru) i mogą automatycznie zastąpić starsze, niezabezpieczone funkcje z ich nowszymi, bezpiecznymi odpowiednikami. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mktemp_s**|\<we/wy >|
|**_wmktemp_s**|\<we/wy > lub \<WCHAR. h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
