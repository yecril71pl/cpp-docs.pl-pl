---
title: _makepath, _wmakepath
ms.date: 4/2/2020
api_name:
- _makepath
- _wmakepath
- _o__makepath
- _o__wmakepath
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: b92e056816183b4bbb07edb3efec4415655d655e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341591"
---
# <a name="_makepath-_wmakepath"></a>_makepath, _wmakepath

Utwórz nazwę ścieżki ze składników. Dostępne są bezpieczniejsze wersje tych funkcji; patrz [_makepath_s, _wmakepath_s](makepath-s-wmakepath-s.md).

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
Pełny bufor ścieżki.

*Dysku*<br/>
Zawiera literę (A, B itd.) odpowiadającą żądanemu dyskowi i opcjonalnie końcowemu dwukropkiem. **_makepath** automatycznie wstawia dwukropek do ścieżki złożonej, jeśli jej brakuje. Jeśli *dysk* ma **wartość NULL** lub wskazuje pusty ciąg, w ciągu *ścieżki* złożonej nie jest wyświetlana żadna litera dysku.

*Dir*<br/>
Zawiera ścieżkę katalogów, z wyłączeniem projektora dysku lub rzeczywistej nazwy pliku. Ukośnik końcowy jest opcjonalny i w pojedynczym argumie\\ *dir* można użyć ukośnika do przodu (/) lub ukośnika odwrotnego ( ) lub oba. Jeśli nie określono przecięciowego (/ lub), \\zostanie on wstawiony automatycznie. Jeśli *dir* ma **wartość NULL** lub wskazuje pusty ciąg, w ciągu *ścieżki* złożonej nie jest wstawiana żadna ścieżka katalogu.

*Fname*<br/>
Zawiera podstawową nazwę pliku bez rozszerzeń nazw plików. Jeśli *nazwa fname* ma **wartość NULL** lub wskazuje pusty ciąg, w ciągu *ścieżki* złożonej nie jest wstawiana żadna nazwa pliku.

*Ext*<br/>
Zawiera rzeczywiste rozszerzenie nazwy pliku z kropką wiodącą lub bez niego (.). **_makepath** wstawia okres automatycznie, jeśli nie pojawia się *wew*. Jeśli *ext* jest **NULL** lub wskazuje na pusty ciąg, żadne rozszerzenie nie jest wstawiany w ciągu *ścieżki* złożonej.

## <a name="remarks"></a>Uwagi

Funkcja **_makepath** tworzy ciąg ścieżki złożonej z poszczególnych komponentów, przechowując wynik w *ścieżce*. *Ścieżka* może zawierać literę dysku, ścieżkę katalogu, nazwę pliku i rozszerzenie nazwy pliku. **_wmakepath** jest szerokoznakową wersją **_makepath**; argumenty, które **mają _wmakepath,** to ciągi znaków o szerokich znakach. **_wmakepath** i **_makepath** zachowują się identycznie w przeciwnym razie.

**Uwaga dotycząca zabezpieczeń** Użyj ciągu zakończonego wartością null. Aby uniknąć przekroczenia buforu, ciąg zakończony z wartością null nie może przekraczać rozmiaru buforu *ścieżki.* **_makepath** nie zapewnia, że długość ciągu ścieżki złożonej nie przekracza **_MAX_PATH**. Aby uzyskać więcej informacji, zobacz [Unikanie przekroczenia buforu](/windows/win32/SecBP/avoiding-buffer-overruns).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath**|**_makepath**|**_makepath**|**_wmakepath**|

Argument *ścieżki* musi wskazywać pusty bufor wystarczająco duży, aby pomieścić pełną ścieżkę. *Ścieżka* złożona nie może być większa niż stała **_MAX_PATH,** zdefiniowana w stdlib.h.

Jeśli ścieżka ma **wartość NULL**, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [yd.](../../c-runtime-library/parameter-validation.md) Ponadto, **errno** jest ustawiony na **EINVAL**. **Wartości NULL** są dozwolone dla wszystkich innych parametrów.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_makepath**|\<>|
|**_wmakepath**|\<> lub \<wchar.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
[_makepath_s, _wmakepath_s](makepath-s-wmakepath-s.md)<br/>
