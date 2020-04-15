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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 3a44651cb9ff8be806c45c6b6c5f41f810319a85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341601"
---
# <a name="_makepath_s-_wmakepath_s"></a>_makepath_s, _wmakepath_s

Tworzy nazwę ścieżki ze składników. Są to wersje [_makepath, _wmakepath](makepath-wmakepath.md) z ulepszeniami zabezpieczeń, jak opisano w [programie Funkcje zabezpieczeń w programie CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Pełny bufor ścieżki.

*rozmiarWłasna*<br/>
Rozmiar buforu w słowach.

*rozmiarWzdjęty*<br/>
Rozmiar buforu w bajtach.

*Dysku*<br/>
Zawiera literę (A, B itd.) odpowiadającą żądanemu dyskowi i opcjonalnie końcowemu dwukropkiem. **_makepath_s** automatycznie wstawia dwukropek do ścieżki złożonej, jeśli jej brakuje. Jeśli *dysk* ma **wartość NULL** lub wskazuje pusty ciąg, w ciągu *ścieżki* złożonej nie jest wyświetlana żadna litera dysku.

*Dir*<br/>
Zawiera ścieżkę katalogów, z wyłączeniem projektora dysku lub rzeczywistej nazwy pliku. Ukośnik końcowy jest opcjonalny i w pojedynczym argumie\\ *dir* można użyć ukośnika do przodu (/) lub ukośnika odwrotnego ( ) lub oba. Jeśli nie określono przecięciowego (/ lub), \\zostanie on wstawiony automatycznie. Jeśli *dir* ma **wartość NULL** lub wskazuje pusty ciąg, w ciągu *ścieżki* złożonej nie jest wstawiana żadna ścieżka katalogu.

*Fname*<br/>
Zawiera podstawową nazwę pliku bez rozszerzeń nazw plików. Jeśli *nazwa fname* ma **wartość NULL** lub wskazuje pusty ciąg, w ciągu *ścieżki* złożonej nie jest wstawiana żadna nazwa pliku.

*Ext*<br/>
Zawiera rzeczywiste rozszerzenie nazwy pliku z kropką wiodącą lub bez niego (.). **_makepath_s** wstawia okres automatycznie, jeśli nie pojawia się *wew*. Jeśli *ext* jest **NULL** lub wskazuje na pusty ciąg, żadne rozszerzenie nie jest wstawiany w ciągu *ścieżki* złożonej.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli się powiedzie; kod błędu w przypadku awarii.

### <a name="error-conditions"></a>Warunki błędu

|*Ścieżka*|*rozmiarInWords* / *rozmiarWzszty*|Zwraca|Zawartość *ścieżki*|
|------------|------------------------------------|------------|------------------------|
|**Null**|Wszelki|**Einval**|nie zmodyfikowano|
|Wszelki|<= 0|**Einval**|nie zmodyfikowano|

Jeśli wystąpi którykolwiek z powyższych warunków błędu, te funkcje wywołają nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, **errno** jest ustawiona na **EINVAL** i funkcje zwraca **EINVAL**. **Null** jest dozwolony dla parametrów *drive*, *fname*i *ext*. Aby uzyskać informacje na temat zachowania, gdy te parametry są wskaźniki null lub puste ciągi, zobacz uwagi sekcji.

## <a name="remarks"></a>Uwagi

Funkcja **_makepath_s** tworzy ciąg ścieżki złożonej z poszczególnych komponentów, przechowując wynik w *ścieżce*. *Ścieżka* może zawierać literę dysku, ścieżkę katalogu, nazwę pliku i rozszerzenie nazwy pliku. **_wmakepath_s** jest szerokoznakową wersją **_makepath_s**; argumenty, które **mają _wmakepath_s,** to ciągi znaków o szerokich znakach. **_wmakepath_s** i **_makepath_s** zachowują się identycznie w przeciwnym razie.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath_s**|**_makepath_s**|**_makepath_s**|**_wmakepath_s**|

Argument *ścieżki* musi wskazywać pusty bufor wystarczająco duży, aby pomieścić pełną ścieżkę. *Ścieżka* złożona nie może być większa niż stała **_MAX_PATH,** zdefiniowana w stdlib.h.

Jeśli ścieżka ma **wartość NULL**, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [yd.](../../c-runtime-library/parameter-validation.md) Ponadto, **errno** jest ustawiony na **EINVAL**. **Wartości NULL** są dozwolone dla wszystkich innych parametrów.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonu; przeciążenia można wywnioskować długość buforu automatycznie (eliminując konieczność określenia argumentu rozmiaru) i mogą automatycznie zastąpić starsze, niezabezpieczone funkcje z ich nowszych, bezpiecznych odpowiedników. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Wersje biblioteki debugowania tych funkcji najpierw wypełniają bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_makepath_s**|\<>|
|**_wmakepath_s**|\<> lub \<wchar.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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
