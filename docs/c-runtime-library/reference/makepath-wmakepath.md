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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 19a20de40bb02e49f618e8e617c9659788dc3e25
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914396"
---
# <a name="_makepath-_wmakepath"></a>_makepath, _wmakepath

Utwórz nazwę ścieżki ze składników. Bardziej bezpieczne wersje tych funkcji są dostępne; Zobacz [_makepath_s, _wmakepath_s](makepath-s-wmakepath-s.md).

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

*ścieżka*<br/>
Bufor pełnej ścieżki.

*litera*<br/>
Zawiera literę (A, B i tak dalej) odpowiadającą żądanym dyskowi i opcjonalnym dwukropkiem. **_makepath** automatycznie wstawia dwukropek w ścieżce złożonej, jeśli nie istnieje. Jeśli *dysk* ma **wartość null** lub wskazuje pusty ciąg, w ciągu *ścieżki* złożonej nie zostanie wyświetlona litera dysku.

*katalogów*<br/>
Zawiera ścieżkę katalogów, w tym oznaczenie dysku lub rzeczywistą nazwę pliku. Końcowy ukośnik jest opcjonalny, a ukośnik (/) lub ukośnik odwrotny (\\) mogą być używane w pojedynczym argumencie *dir* . Jeśli nie zostanie określony końcowy ukośnik (/ \\lub), zostanie on wstawiony automatycznie. Jeśli *dir* ma **wartość null** lub wskazuje na pusty ciąg, w ciągu *ścieżki* złożonej nie zostanie wstawiona ścieżka katalogu.

*fname*<br/>
Zawiera podstawową nazwę pliku bez rozszerzeń nazw plików. Jeśli *fname* ma **wartość null** lub wskazuje na pusty ciąg, w ciągu *ścieżki* złożonej nie zostanie wstawiona nazwa pliku.

*EXT*<br/>
Zawiera rzeczywiste rozszerzenie nazwy pliku z lub bez kropki wiodącej (.). **_makepath** wstawia okres automatycznie, jeśli nie jest wyświetlany w *EXT*. Jeśli parametr *EXT* ma **wartość null** lub wskazuje pusty ciąg, w ciągu *ścieżki* złożonej nie zostanie wstawiony żaden rozszerzenie.

## <a name="remarks"></a>Uwagi

Funkcja **_makepath** tworzy ciąg ścieżki złożonej z poszczególnych składników, przechowując wynik w *ścieżce*. *Ścieżka* może zawierać literę dysku, ścieżkę katalogu, nazwę pliku i rozszerzenie nazwy pliku. **_wmakepath** to dwubajtowa wersja **_makepath**; argumenty do **_wmakepath** są ciągami znaków dwubajtowych. **_wmakepath** i **_makepath** zachowują się identycznie w inny sposób.

**Uwaga dotycząca zabezpieczeń** Użyj ciągu zakończenia o wartości null. Aby uniknąć przepełnienia buforu, ciąg zakończony znakiem null nie może przekraczać rozmiaru buforu *ścieżki* . **_makepath** nie gwarantuje, że długość ciągu ścieżki złożonej nie przekracza **_MAX_PATH**. Aby uzyskać więcej informacji, zobacz [unikanie przekroczeń buforu](/windows/win32/SecBP/avoiding-buffer-overruns).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath**|**_makepath**|**_makepath**|**_wmakepath**|

Argument *Path* musi wskazywać na pusty bufor wystarczająco duży, aby pomieścić pełną ścieżkę. *Ścieżka* złożona nie może być większa niż wartość **_MAX_PATH** stała określona w STDLIB. h.

Jeśli ścieżka ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Ponadto **errno** jest ustawiony na **EINVAL**. Wartości **null** są dozwolone dla wszystkich innych parametrów.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_makepath**|\<STDLIB. h>|
|**_wmakepath**|\<STDLIB. h> lub \<WCHAR. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
