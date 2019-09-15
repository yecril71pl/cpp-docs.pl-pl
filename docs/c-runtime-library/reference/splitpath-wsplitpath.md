---
title: _splitpath, _wsplitpath
ms.date: 11/04/2016
api_name:
- _wsplitpath
- _splitpath
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: a502977faf91d744868c4aef79b3a40ca240a90f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958037"
---
# <a name="_splitpath-_wsplitpath"></a>_splitpath, _wsplitpath

Przerwij nazwę ścieżki w składnikach. Bardziej bezpieczne wersje tych funkcji są dostępne, zobacz [_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md).

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

*litera*<br/>
Litera dysku, po którym następuje dwukropek ( **:** ). Jeśli nie potrzebujesz litery dysku, możesz przekazać **wartość null** dla tego parametru.

*katalogów*<br/>
Ścieżka katalogu, włącznie z końcowym ukośnikiem. Można używać ukośników **/** (), ukośników odwrotnych ( **\\** ) lub obu tych wartości. Jeśli ścieżka katalogu nie jest potrzebna, można przekazać **wartość null** dla tego parametru.

*fname*<br/>
Podstawowa nazwa pliku (bez rozszerzenia). Jeśli nazwa pliku nie jest potrzebna, można przekazać **wartość null** dla tego parametru.

*EXT*<br/>
Rozszerzenie nazwy pliku, włącznie z kropką wiodącą ( **.** ). Jeśli rozszerzenie nazwy pliku nie jest potrzebne, można przekazać **wartość null** dla tego parametru.

## <a name="remarks"></a>Uwagi

Funkcja **_splitpath** dzieli ścieżkę na cztery składniki. **_splitpath** automatycznie obsługuje argumenty ciągu znaków wielobajtowych, aby rozpoznać sekwencje znaków wielobajtowych zgodnie z aktualnie używaną stroną kodową. **_wsplitpath** to dwubajtowa wersja **_splitpath**; argumenty **_wsplitpath** są ciągami znaków dwubajtowych. Funkcje te zachowują się identycznie w inny sposób.

**Uwaga dotycząca zabezpieczeń** Te funkcje powodują potencjalne zagrożenie spowodowane przez problem z przepełnieniem buforu. Problemy związane z przepełnieniem buforu są częstą metodą ataku systemu, powodując nieuzasadnione podniesienie uprawnień. Aby uzyskać więcej informacji, zobacz [unikanie przekroczeń buforu](/windows/win32/SecBP/avoiding-buffer-overruns). Bardziej bezpieczne wersje tych funkcji są dostępne; Zobacz [_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath**|**_splitpath**|**_splitpath**|**_wsplitpath**|

Każdy składnik pełnej ścieżki jest przechowywany w osobnym buforze; stałe manifestu **_MAX_DRIVE**, **_MAX_DIR**, **_MAX_FNAME**i **_MAX_EXT** (zdefiniowane w STDLIB. H) Określ maksymalny rozmiar każdego składnika plików. Składniki plików, które są większe niż odpowiednie stałe manifestu powodują uszkodzenie sterty.

Każdy bufor musi być tak duży, jak odpowiadający mu stała manifestu, aby uniknąć potencjalnego przepełnienia buforu.

Poniższa tabela zawiera listę wartości stałych manifestu.

|Nazwa|Wartość|
|----------|-----------|
|**_MAX_DRIVE**|3|
|**_MAX_DIR**|256|
|**_MAX_FNAME**|256|
|**_MAX_EXT**|256|

Jeśli pełna ścieżka nie zawiera składnika (na przykład filename), **_splitpath** przypisze puste ciągi do odpowiednich buforów.

Można przekazać **wartość null** do **_splitpath** dla dowolnego parametru innego niż niepotrzebna *ścieżka* .

Jeśli *ścieżka* ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na **EINVAL** , a funkcja zwraca **EINVAL**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_splitpath**|\<stdlib.h>|
|**_wsplitpath**|\<STDLIB. h > lub \<WCHAR. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład dla [_makepath](makepath-wmakepath.md).

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
