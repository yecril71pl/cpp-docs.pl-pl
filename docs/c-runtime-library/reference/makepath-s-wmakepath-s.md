---
title: _makepath_s, _wmakepath_s
ms.date: 11/04/2016
apiname:
- _wmakepath_s
- _makepath_s
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
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
ms.openlocfilehash: 3536569fd3e77a353003e1372d5dc4ee6e4ee3fb
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210656"
---
# <a name="makepaths-wmakepaths"></a>_makepath_s, _wmakepath_s

Tworzy nazwę ścieżki ze składników. Są to wersje [_makepath —, _wmakepath —](makepath-wmakepath.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Ścieżka*<br/>
Buforu pełnej ścieżki.

*sizeInWords*<br/>
Rozmiar buforu w słowach.

*sizeInBytes*<br/>
Rozmiar buforu w bajtach.

*drive*<br/>
Zawiera litery (A, B i tak dalej) odpowiadający żądany dysk i opcjonalny dwukropek końcowe. **_makepath_s —** wstawia dwukropkiem w ścieżce złożonego przypadku jej braku. Jeśli *dysku* jest **NULL** lub punktów na pusty ciąg, litera nie zostanie wyświetlony w złożonego *ścieżki* ciągu.

*dir*<br/>
Zawiera ścieżkę katalogów, nie wliczając oznaczenie dysku lub rzeczywiste nazwy plików. Końcowy ukośnik jest opcjonalna i ukośnika (/) lub ukośnika odwrotnego (\\) lub obu z nich mogą być używane w ramach pojedynczej *dir* argumentu. Jeśli nie ukośnika (/ lub \\) jest określona, jest wstawiany automatycznie. Jeśli *dir* jest **NULL** lub wskazuje na pusty ciąg, nie ścieżka katalogu jest wstawiana w złożonego *ścieżki* ciągu.

*fname*<br/>
Zawiera nazwę pliku podstawowego bez żadnych rozszerzeń nazw plików. Jeśli *fname* jest **NULL** lub wskazuje na pusty ciąg, a nazwa pliku nie jest wstawiana w złożonego *ścieżki* ciągu.

*ext*<br/>
Zawiera rozszerzenie nazwy pliku, z lub bez poprzedzającej go kropki (.). **_makepath_s —** wstawia okresu automatycznie, jeżeli nie ma w *ext*. Jeśli *ext* jest **NULL** lub wskazuje na pusty ciąg, bez rozszerzenia jest wstawiana w złożonego *ścieżki* ciągu.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie; Kod błędu.

### <a name="error-conditions"></a>Warunki błędów

|*Ścieżka*|*sizeInWords* / *sizeInBytes*|Wróć|Zawartość *ścieżki*|
|------------|------------------------------------|------------|------------------------|
|**NULL**|Wszystkie|**EINVAL**|Nie zmodyfikowano|
|Wszystkie|<= 0|**EINVAL**|Nie zmodyfikowano|

Jeśli wystąpi dowolne z powyższych warunków błędów, funkcje te wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EINVAL** i funkcji zwraca **EINVAL**. **Wartość NULL** jest dozwolona dla parametrów *dysku*, *fname*, i *ext*. Aby uzyskać informacje o zachowaniu w przypadku wskaźników o wartości null lub puste ciągi tych parametrów, zobacz sekcję Uwagi.

## <a name="remarks"></a>Uwagi

**_Makepath_s —** funkcja tworzy ciąg ścieżki złożonej z poszczególnych składników, przechowywanie wyników w *ścieżki*. *Ścieżki* może zawierać literę dysku, ścieżka do katalogu, nazwę pliku i rozszerzenie nazwy pliku. **_wmakepath_s —** to wersja znaku dwubajtowego **_makepath_s —**; argumenty **_wmakepath_s —** są ciągami znaków dwubajtowych. **_wmakepath_s —** i **_makepath_s —** zachowują się identycznie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath_s**|**_makepath_s**|**_makepath_s**|**_wmakepath_s**|

*Ścieżki* argumentu musi wskazywać na pusty bufor wystarczająco duży, aby pomieścić pełną ścieżkę. Złożonego *ścieżki* nie może być większa niż **_MAX_PATH** stałą, zdefiniowane w Stdlib.h.

Jeśli ścieżka jest **NULL**, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Ponadto **errno** ustawiono **EINVAL**. **Wartość NULL** wartości są dozwolone w przypadku wszystkich innych parametrów.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążania szablonu; przeciążenia mogą automatycznie wywnioskować długość buforu (eliminując potrzebę określenia argumentu rozmiaru) oraz ich mogą automatycznie zastąpić starsze, niezabezpieczone funkcje ich nowsze, bezpieczne odpowiedniki. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Wersje debugowania tych funkcji najpierw wypełniają bufor 0xfd. Aby wyłączyć to zachowanie, użyj [_crtsetdebugfillthreshold —](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_makepath_s**|\<stdlib.h>|
|**_wmakepath_s**|\<stdlib.h> or \<wchar.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
