---
title: _makepath, _wmakepath
ms.date: 11/04/2016
apiname:
- _makepath
- _wmakepath
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
apitype: DLLExport
f1_keywords:
- _wmakepath
- _tmakepath
- makepath
- tmakepath
- wmakepath
- _makepath
helpviewer_keywords:
- _makepath function
- wmakepath function
- makepath function
- _tmakepath function
- paths
- _wmakepath function
- tmakepath function
ms.assetid: 5930b197-a7b8-46eb-8519-2841a58cd026
ms.openlocfilehash: 073f8aba6936aa33dafcef7ed47f5286802a4948
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62285702"
---
# <a name="makepath-wmakepath"></a>_makepath, _wmakepath

Utwórz nazwę ścieżki ze składników. Bardziej bezpieczne wersje tych funkcji są dostępne; zobacz [_makepath_s —, _wmakepath_s —](makepath-s-wmakepath-s.md).

## <a name="syntax"></a>Składnia

```C
void _makepath(
   char *path,
   const char *drive,
   const char *dir,
   const char *fname,
   const char *ext
);
void _wmakepath(
   wchar_t *path,
   const wchar_t *drive,
   const wchar_t *dir,
   const wchar_t *fname,
   const wchar_t *ext
);
```

### <a name="parameters"></a>Parametry

*Ścieżka*<br/>
Buforu pełnej ścieżki.

*drive*<br/>
Zawiera litery (A, B i tak dalej) odpowiadający żądany dysk i opcjonalny dwukropek końcowe. **_makepath —** wstawia dwukropkiem w ścieżce złożonego przypadku jej braku. Jeśli *dysku* jest **NULL** lub punktów na pusty ciąg, litera nie zostanie wyświetlony w złożonego *ścieżki* ciągu.

*dir*<br/>
Zawiera ścieżkę katalogów, nie wliczając oznaczenie dysku lub rzeczywiste nazwy plików. Końcowy ukośnik jest opcjonalna i ukośnika (/) lub ukośnika odwrotnego (\\) lub obu z nich mogą być używane w ramach pojedynczej *dir* argumentu. Jeśli nie ukośnika (/ lub \\) jest określona, jest wstawiany automatycznie. Jeśli *dir* jest **NULL** lub wskazuje na pusty ciąg, nie ścieżka katalogu jest wstawiana w złożonego *ścieżki* ciągu.

*fname*<br/>
Zawiera nazwę pliku podstawowego bez żadnych rozszerzeń nazw plików. Jeśli *fname* jest **NULL** lub wskazuje na pusty ciąg, a nazwa pliku nie jest wstawiana w złożonego *ścieżki* ciągu.

*ext*<br/>
Zawiera rozszerzenie nazwy pliku, z lub bez poprzedzającej go kropki (.). **_makepath —** wstawia okresu automatycznie, jeżeli nie ma w *ext*. Jeśli *ext* jest **NULL** lub wskazuje na pusty ciąg, bez rozszerzenia jest wstawiana w złożonego *ścieżki* ciągu.

## <a name="remarks"></a>Uwagi

**_Makepath —** funkcja tworzy ciąg ścieżki złożonej z poszczególnych składników, przechowywanie wyników w *ścieżki*. *Ścieżki* może zawierać literę dysku, ścieżka do katalogu, nazwę pliku i rozszerzenie nazwy pliku. **_wmakepath —** to wersja znaku dwubajtowego **_makepath —**; argumenty **_wmakepath —** są ciągami znaków dwubajtowych. **_wmakepath —** i **_makepath —** zachowują się identycznie.

**Uwaga dotycząca zabezpieczeń** Użyj ciąg zakończony znakiem null. Aby uniknąć przepełnienia buforu, ciąg zakończony znakiem null nie może przekraczać rozmiaru *ścieżki* buforu. **_makepath —** zapewnić, że długość ciągu złożonego ścieżki przekracza **_MAX_PATH**. Aby uzyskać więcej informacji, zobacz [unikanie przepełnień bufora](/windows/desktop/SecBP/avoiding-buffer-overruns).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath**|**_makepath**|**_makepath**|**_wmakepath**|

*Ścieżki* argumentu musi wskazywać na pusty bufor wystarczająco duży, aby pomieścić pełną ścieżkę. Złożonego *ścieżki* nie może być większa niż **_MAX_PATH** stałą, zdefiniowane w Stdlib.h.

Jeśli ścieżka jest **NULL**, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Ponadto **errno** ustawiono **EINVAL**. **Wartość NULL** wartości są dozwolone w przypadku wszystkich innych parametrów.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_makepath**|\<stdlib.h>|
|**_wmakepath**|\<stdlib.h> or \<wchar.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_makepath.c
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char path_buffer[_MAX_PATH];
   char drive[_MAX_DRIVE];
   char dir[_MAX_DIR];
   char fname[_MAX_FNAME];
   char ext[_MAX_EXT];

   _makepath( path_buffer, "c", "\\sample\\crt\\", "makepath", "c" ); // C4996
   // Note: _makepath is deprecated; consider using _makepath_s instead
   printf( "Path created with _makepath: %s\n\n", path_buffer );
   _splitpath( path_buffer, drive, dir, fname, ext ); // C4996
   // Note: _splitpath is deprecated; consider using _splitpath_s instead
   printf( "Path extracted with _splitpath:\n" );
   printf( "   Drive: %s\n", drive );
   printf( "   Dir: %s\n", dir );
   printf( "   Filename: %s\n", fname );
   printf( "   Ext: %s\n", ext );
}
```

```Output
Path created with _makepath: c:\sample\crt\makepath.c

Path extracted with _splitpath:
   Drive: c:
   Dir: \sample\crt\
   Filename: makepath
   Ext: .c
```

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
[_makepath_s, _wmakepath_s](makepath-s-wmakepath-s.md)<br/>
