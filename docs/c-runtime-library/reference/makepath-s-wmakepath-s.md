---
title: _makepath_s, _wmakepath_s
ms.date: 4/2/2020
api_name:
- _wmakepath_s
- _makepath_s
- _o__makepath_s
- _o__wmakepath_s
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wmakepath_s
- makepath_s
- _makepath_s
- wmakepath_s
helpviewer_keywords:
- _makepath_s function
- wmakepath_s function
- paths
- _wmakepath_s function
- makepath_s function
ms.assetid: 4405e43c-3d63-4697-bb80-9b8dcd21d027
ms.openlocfilehash: 8eb3cf338d7486d7e7893090a1390e5d2d16a438
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914478"
---
# <a name="_makepath_s-_wmakepath_s"></a>_makepath_s, _wmakepath_s

Tworzy nazwę ścieżki ze składników. Są to wersje [_makepath, _wmakepath](makepath-wmakepath.md) z ulepszonymi zabezpieczeniami, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t _makepath_s(
   char *path,
   size_t sizeInBytes,
   const char *drive,
   const char *dir,
   const char *fname,
   const char *ext
);
errno_t _wmakepath_s(
   wchar_t *path,
   size_t sizeInWords,
   const wchar_t *drive,
   const wchar_t *dir,
   const wchar_t *fname,
   const wchar_t *ext
);
template <size_t size>
errno_t _makepath_s(
   char (&path)[size],
   const char *drive,
   const char *dir,
   const char *fname,
   const char *ext
); // C++ only
template <size_t size>
errno_t _wmakepath_s(
   wchar_t (&path)[size],
   const wchar_t *drive,
   const wchar_t *dir,
   const wchar_t *fname,
   const wchar_t *ext
); // C++ only
```

### <a name="parameters"></a>Parametry

*ścieżka*<br/>
Bufor pełnej ścieżki.

*sizeInWords*<br/>
Rozmiar buforu w słowach.

*sizeInBytes*<br/>
Rozmiar buforu w bajtach.

*litera*<br/>
Zawiera literę (A, B i tak dalej) odpowiadającą żądanym dyskowi i opcjonalnym dwukropkiem. **_makepath_s** automatycznie wstawia dwukropek w ścieżce złożonej, jeśli nie istnieje. Jeśli *dysk* ma **wartość null** lub wskazuje pusty ciąg, w ciągu *ścieżki* złożonej nie zostanie wyświetlona litera dysku.

*katalogów*<br/>
Zawiera ścieżkę katalogów, w tym oznaczenie dysku lub rzeczywistą nazwę pliku. Końcowy ukośnik jest opcjonalny, a ukośnik (/) lub ukośnik odwrotny (\\) mogą być używane w pojedynczym argumencie *dir* . Jeśli nie zostanie określony końcowy ukośnik (/ \\lub), zostanie on wstawiony automatycznie. Jeśli *dir* ma **wartość null** lub wskazuje na pusty ciąg, w ciągu *ścieżki* złożonej nie zostanie wstawiona ścieżka katalogu.

*fname*<br/>
Zawiera podstawową nazwę pliku bez rozszerzeń nazw plików. Jeśli *fname* ma **wartość null** lub wskazuje na pusty ciąg, w ciągu *ścieżki* złożonej nie zostanie wstawiona nazwa pliku.

*EXT*<br/>
Zawiera rzeczywiste rozszerzenie nazwy pliku z lub bez kropki wiodącej (.). **_makepath_s** wstawia okres automatycznie, jeśli nie jest wyświetlany w *EXT*. Jeśli parametr *EXT* ma **wartość null** lub wskazuje pusty ciąg, w ciągu *ścieżki* złożonej nie zostanie wstawiony żaden rozszerzenie.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli pomyślne; kod błędu w przypadku niepowodzenia.

### <a name="error-conditions"></a>Warunki błędów

|*ścieżka*|*sizeInWords* / *sizeInBytes*|Przesłać|Zawartość *ścieżki*|
|------------|------------------------------------|------------|------------------------|
|**NULL**|ile|**EINVAL**|nie zmodyfikowano|
|ile|<= 0|**EINVAL**|nie zmodyfikowano|

Jeśli wystąpi którykolwiek z powyższych warunków błędu, te funkcje wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na **EINVAL** , a funkcje zwracają **EINVAL**. Dla parametrów *Drive*, *fname*i *EXT*jest dozwolona **wartość null** . Aby uzyskać informacje o zachowaniu, gdy te parametry mają wskaźniki o wartości null lub puste ciągi, zobacz sekcję Uwagi.

## <a name="remarks"></a>Uwagi

Funkcja **_makepath_s** tworzy ciąg ścieżki złożonej z poszczególnych składników, przechowując wynik w *ścieżce*. *Ścieżka* może zawierać literę dysku, ścieżkę katalogu, nazwę pliku i rozszerzenie nazwy pliku. **_wmakepath_s** to dwubajtowa wersja **_makepath_s**; argumenty do **_wmakepath_s** są ciągami znaków dwubajtowych. **_wmakepath_s** i **_makepath_s** zachowują się identycznie w inny sposób.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath_s**|**_makepath_s**|**_makepath_s**|**_wmakepath_s**|

Argument *Path* musi wskazywać na pusty bufor wystarczająco duży, aby pomieścić pełną ścieżkę. *Ścieżka* złożona nie może być większa niż wartość **_MAX_PATH** stała określona w STDLIB. h.

Jeśli ścieżka ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Ponadto **errno** jest ustawiony na **EINVAL**. Wartości **null** są dozwolone dla wszystkich innych parametrów.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonów; przeciążenia mogą automatycznie wywnioskować długość buforu (eliminując konieczność określenia argumentu rozmiaru) i mogą automatycznie zastąpić starsze, niezabezpieczone funkcje z ich nowszymi, bezpiecznymi odpowiednikami. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

Wersje biblioteki debugowania tych funkcji najpierw wypełniają bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_makepath_s**|\<STDLIB. h>|
|**_wmakepath_s**|\<STDLIB. h> lub \<WCHAR. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_makepath_s.c

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char path_buffer[_MAX_PATH];
   char drive[_MAX_DRIVE];
   char dir[_MAX_DIR];
   char fname[_MAX_FNAME];
   char ext[_MAX_EXT];
   errno_t err;

   err = _makepath_s( path_buffer, _MAX_PATH, "c", "\\sample\\crt\\",
                      "crt_makepath_s", "c" );
   if (err != 0)
   {
      printf("Error creating path. Error code %d.\n", err);
      exit(1);
   }
   printf( "Path created with _makepath_s: %s\n\n", path_buffer );
   err = _splitpath_s( path_buffer, drive, _MAX_DRIVE, dir, _MAX_DIR, fname,
                       _MAX_FNAME, ext, _MAX_EXT );
   if (err != 0)
   {
      printf("Error splitting the path. Error code %d.\n", err);
      exit(1);
   }
   printf( "Path extracted with _splitpath_s:\n" );
   printf( "   Drive: %s\n", drive );
   printf( "   Dir: %s\n", dir );
   printf( "   Filename: %s\n", fname );
   printf( "   Ext: %s\n", ext );
}
```

```Output
Path created with _makepath_s: c:\sample\crt\crt_makepath_s.c

Path extracted with _splitpath_s:
   Drive: c:
   Dir: \sample\crt\
   Filename: crt_makepath_s
   Ext: .c
```

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
