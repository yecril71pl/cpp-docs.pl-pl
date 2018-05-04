---
title: _splitpath —, _wsplitpath — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 220e2befc40dba342a7f8c2aa4c94294bc667ce0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="splitpath-wsplitpath"></a>_splitpath, _wsplitpath

Podziel nazwa ścieżki na składniki. Dostępne są bardziej bezpieczne wersje tych funkcji, zobacz [_splitpath_s —, _wsplitpath_s —](splitpath-s-wsplitpath-s.md).

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

*ścieżka* pełną ścieżkę.

*dysk* litery z dwukropkiem (**:**). Można przekazać **NULL** dla tego parametru, jeśli nie ma potrzeby literę dysku.

*dir* ścieżki katalogu, w tym ukośnika. Przekazuj ukośniki ( **/** ), ukośników odwrotnych ( **\\** ), lub mogą być używane. Można przekazać **NULL** dla tego parametru, jeśli nie ma potrzeby ścieżki katalogu.

*fname* podstawowa nazwa pliku (bez rozszerzenia). Można przekazać **NULL** dla tego parametru, jeśli nazwa pliku nie ma potrzeby.

*Roz* rozszerzenie nazwy pliku, w tym wiodące okres (**.**). Można przekazać **NULL** dla tego parametru, jeśli nie ma potrzeby rozszerzenie nazwy pliku.

## <a name="remarks"></a>Uwagi

**_Splitpath —** funkcja dzieli ścieżki do jego czterech składników. **_splitpath —** automatycznie obsługuje argumentów ciągów znaków wielobajtowych zgodnie z potrzebami, rozpoznawanie wielobajtowych sekwencji znaków zgodnie ze strony kodowe wielobajtowe obecnie w użyciu. **_wsplitpath —** jest wersja znaków dwubajtowych **_splitpath —**; argumenty **_wsplitpath —** są ciągami znaków dwubajtowych. Funkcje te działają tak samo w przeciwnym razie wartość.

**Uwaga dotycząca zabezpieczeń** tych funkcji pociągnąć za sobą potencjalne zagrożenie wynikające z problem przepełnienie buforu. Przepełnienie buforu problemy używanej metody ataku systemu, co powoduje nieuzasadnione podniesienie uprawnień. Aby uzyskać więcej informacji, zobacz [unikanie Overruns buforu](http://msdn.microsoft.com/library/windows/desktop/ms717795). Bezpieczniejsza wersje te funkcje są dostępne; zobacz [_splitpath_s —, _wsplitpath_s —](splitpath-s-wsplitpath-s.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath —**|**_splitpath**|**_splitpath**|**_wsplitpath**|

Każdy składnik pełnej ścieżki są przechowywane w oddzielnych buforu; stałe manifestu **_max_drive —**, **_max_dir —**, **_max_fname —**, i **_max_ext —** (zdefiniowany w STDLIB. H) określić maksymalny rozmiar każdego pliku składnika. Składniki plików, które są większe niż odpowiednie stałe manifestu spowodować uszkodzenie sterty.

Każdy buforu musi być możliwie jak jej odpowiednie stała manifestu w celu uniknięcia potencjalnego przepełnienia buforu.

W poniższej tabeli wymieniono wartości stałe manifestu.

|Nazwa|Wartość|
|----------|-----------|
|**_MAX_DRIVE —**|3|
|**_MAX_DIR —**|256|
|**_MAX_FNAME —**|256|
|**_MAX_EXT —**|256|

Jeśli pełna ścieżka nie zawiera składników (na przykład nazwy pliku), **_splitpath —** przypisuje puste ciągi do odpowiedniego buforów.

Można przekazać **NULL** do **_splitpath —** dla każdego parametru innych niż *ścieżka* nie potrzebne.

Jeśli *ścieżki* jest **NULL**, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **errno** ustawiono **einval —** i funkcja zwraca **einval —**.

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
