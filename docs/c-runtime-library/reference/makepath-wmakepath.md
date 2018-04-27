---
title: _makepath —, _wmakepath — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _makepath function
- wmakepath function
- makepath function
- _tmakepath function
- paths
- _wmakepath function
- tmakepath function
ms.assetid: 5930b197-a7b8-46eb-8519-2841a58cd026
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0c6ad1331021331e9c9ddc1d1344aae8ed164ce2
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="makepath-wmakepath"></a>_makepath, _wmakepath

Utwórz nazwę ścieżki ze składników. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [_makepath_s —, _wmakepath_s —](makepath-s-wmakepath-s.md).

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

*ścieżka* buforu pełnej ścieżki.

*dysk* zawiera litery (A, B i tak dalej) odpowiadający żądany dysk i opcjonalny dwukropek końcowe. **_makepath —** wstawia dwukropkiem w ścieżce złożonego, jeśli jest on niedostępny. Jeśli *dysku* jest **NULL** lub punktów na pusty ciąg, litera nie występuje w złożone *ścieżki* ciągu.

*dir* zawiera ścieżkę katalogi nie łącznie z określeniem dysku lub rzeczywiste nazwy plików. Wiodący ukośnik jest opcjonalne, a albo ukośnika (/) ani ukośnika odwrotnego (\\) lub może być używany zarówno w jednej *dir* argumentu. Jeśli nie ma ukośników (/ lub \\) jest określona, zostanie on włożony automatycznie. Jeśli *dir* jest **NULL** lub wskazuje na pusty ciąg, nie ma ścieżki katalogu jest wstawiana złożone *ścieżki* ciągu.

*fname* zawiera nazwę pliku podstawowego bez żadnych rozszerzeń nazw plików. Jeśli *fname* jest **NULL** lub wskazuje na pusty ciąg, nazwa pliku nie jest wkładana złożone *ścieżki* ciągu.

*Roz* zawiera rozszerzenie nazwy pliku, z lub bez poprzedzającej go kropki (.). **_makepath —** wstawia okresu automatycznie, jeśli nie ma w *ext*. Jeśli *ext* jest **NULL** lub wskazuje na pusty ciąg, bez rozszerzenia jest wstawiana złożone *ścieżki* ciągu.

## <a name="remarks"></a>Uwagi

**_Makepath —** funkcja tworzy ciąg ścieżki złożone z poszczególnych składników zapisywania wyniku w *ścieżki*. *Ścieżki* może zawierać litery dysku, ścieżki katalogu, nazwę pliku i rozszerzenie nazwy pliku. **_wmakepath —** jest wersja znaków dwubajtowych **_makepath —**; argumenty **_wmakepath —** są ciągami znaków dwubajtowych. **_wmakepath —** i **_makepath —** zachowują się tak samo w przeciwnym razie wartość.

**Uwaga dotycząca zabezpieczeń** użyć ciągu zakończonego wartością null. Aby uniknąć przepełnienia buforu, zerem ciągu nie może przekraczać wielkości *ścieżki* buforu. **_makepath —** zapewnić, że długość ciągu złożony ścieżki przekracza **_max_path —**. Aby uzyskać więcej informacji, zobacz [unikanie Overruns buforu](http://msdn.microsoft.com/library/windows/desktop/ms717795).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath —**|**_makepath**|**_makepath**|**_wmakepath —**|

*Ścieżki* argumentu musi wskazywać na pusty buforu wystarczająco duży, aby pomieścić pełną ścieżkę. Złożone *ścieżki* nie może być większa niż **_max_path —** stałą, zdefiniowane w Stdlib.h.

Jeśli ścieżka jest **NULL**, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Ponadto **errno** ustawiono **einval —**. **Wartość NULL** wartości są dozwolone dla wszystkich innych parametrów.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_makepath**|\<stdlib.h>|
|**_wmakepath —**|\<stdlib.h > lub \<wchar.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
