---
title: _splitpath, _wsplitpath
ms.date: 11/04/2016
apiname:
- _wsplitpath
- _splitpath
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
- wsplitpath
- _splitpath
- splitpath
- _wsplitpath
- _tsplitpath
helpviewer_keywords:
- _splitpath function
- pathnames
- wsplitpath function
- splitpath function
- _wsplitpath function
- tsplitpath function
- path names
- _tsplitpath function
ms.assetid: 32bd76b5-1385-4ee8-a64c-abcb541cd2e4
ms.openlocfilehash: d079bd17912c0711a4e1fbadadf12430520f2c96
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465185"
---
# <a name="splitpath-wsplitpath"></a>_splitpath, _wsplitpath

Nazwa ścieżki przerwać działanie składników. Dostępne są bardziej bezpieczne wersje tych funkcji, zobacz [_splitpath_s —, _wsplitpath_s —](splitpath-s-wsplitpath-s.md).

## <a name="syntax"></a>Składnia

```C
void _splitpath(
   const char *path,
   char *drive,
   char *dir,
   char *fname,
   char *ext
);
void _wsplitpath(
   const wchar_t *path,
   wchar_t *drive,
   wchar_t *dir,
   wchar_t *fname,
   wchar_t *ext
);
```

### <a name="parameters"></a>Parametry

*Ścieżka*<br/>
Pełna ścieżka.

*Dysk*<br/>
Litera, następuje dwukropek (**:**). Możesz przekazać **NULL** dla tego parametru, jeśli nie potrzebujesz literę dysku.

*dir*<br/>
Ścieżka katalogu, w tym ukośnika. Kreski ułamkowe ( **/** ), ukośniki odwrotne ( **\\** ), lub obie mogą być używane. Możesz przekazać **NULL** dla tego parametru, jeśli nie potrzebujesz ścieżki katalogu.

*fname*<br/>
Podstawowa nazwa pliku (bez rozszerzenia). Możesz przekazać **NULL** dla tego parametru, jeśli nazwa pliku nie jest potrzebna.

*ext*<br/>
Rozszerzenie nazwy pliku, w tym wiodące w okresie (**.**). Możesz przekazać **NULL** dla tego parametru, jeśli nie potrzebujesz rozszerzenie nazwy pliku.

## <a name="remarks"></a>Uwagi

**_Splitpath —** funkcja dzieli ścieżkę na jej cztery składniki. **_splitpath —** automatycznie obsługuje argumenty ciągu znaków wielobajtowych zgodnie z potrzebami, rozpoznawaniu sekwencje znaków wielobajtowych zgodnie z aktualnie używaną stroną kodową wielobajtowe. **_wsplitpath —** to wersja znaku dwubajtowego **_splitpath —**; argumenty **_wsplitpath —** są ciągami znaków dwubajtowych. Funkcje te zachowują się identycznie.

**Uwaga dotycząca zabezpieczeń** te funkcje pociągnąć za sobą potencjalnym zagrożeniem spowodowanym ulepszonym problem przepełnienia buforu. Problemy z przepełnieniem buforu są częstą metodą ataku systemu, co nieuzasadnione podniesienie poziomu uprawnień. Aby uzyskać więcej informacji, zobacz [unikanie przepełnień bufora](/windows/desktop/SecBP/avoiding-buffer-overruns). Bardziej bezpieczne wersje tych funkcji są dostępne; zobacz [_splitpath_s —, _wsplitpath_s —](splitpath-s-wsplitpath-s.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath —**|**_splitpath**|**_splitpath**|**_wsplitpath**|

Każdy składnik Pełna ścieżka jest przechowywany w oddzielnych buforu; stałe manifestu **_MAX_DRIVE**, **_MAX_DIR**, **_MAX_FNAME**, i **_MAX_EXT** (zdefiniowany w STDLIB. H) określ maksymalny rozmiar każdego pliku składnika. Składniki pliku, które są większe niż odpowiednie stałych manifestu doprowadzić do uszkodzenia sterty.

Każdy bufor musi być tak duże jak jego odpowiedniego stała manifestu, aby uniknąć potencjalnych przepełnienia buforu.

W poniższej tabeli wymieniono wartości stałe manifestu.

|Nazwa|Wartość|
|----------|-----------|
|**_MAX_DRIVE**|3|
|**_MAX_DIR**|256|
|**_MAX_FNAME**|256|
|**_MAX_EXT**|256|

Jeśli pełna ścieżka nie zawiera składników (na przykład, nazwa_pliku), **_splitpath —** przypisuje puste ciągi znaków do odpowiedniego buforów.

Można przekazać **NULL** do **_splitpath —** dla każdego parametru, inne niż *ścieżki* , nie potrzebujesz.

Jeśli *ścieżki* jest **NULL**, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EINVAL** a funkcja zwraca **EINVAL**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_splitpath**|\<stdlib.h>|
|**_wsplitpath**|\<stdlib.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [_makepath —](makepath-wmakepath.md).

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
