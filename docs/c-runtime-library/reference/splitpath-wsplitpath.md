---
title: _splitpath, _wsplitpath
ms.date: 4/2/2020
api_name:
- _wsplitpath
- _splitpath
- _o__splitpath
- _o__wsplitpath
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
ms.openlocfilehash: 6798f93b2d1bc18a190b3b015bf8c882a3fa8a37
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355612"
---
# <a name="_splitpath-_wsplitpath"></a>_splitpath, _wsplitpath

Podziel nazwę ścieżki na składniki. Dostępne są bezpieczniejsze wersje tych funkcji, patrz [_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md).

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

*Dysku*<br/>
List dysku, po którym następuje dwukropek (**:**). Można przekazać **null** dla tego parametru, jeśli nie potrzebujesz litery dysku.

*Dir*<br/>
Ścieżka katalogu, w tym ukośnik na końcu. Można użyć **/** ukośników do **\\** przodu ( ), ukośników odwrotnych ( ) lub obu. Można przekazać **null** dla tego parametru, jeśli nie potrzebujesz ścieżki katalogu.

*Fname*<br/>
Podstawowa nazwa pliku (bez rozszerzenia). Można przekazać **null** dla tego parametru, jeśli nie potrzebujesz nazwy pliku.

*Ext*<br/>
Rozszerzenie nazwy pliku, w tym okres wiodący (**.**). Możesz przekazać **wartość NULL** dla tego parametru, jeśli nie jest potrzebne rozszerzenie nazwy pliku.

## <a name="remarks"></a>Uwagi

Funkcja **_splitpath** dzieli ścieżkę na cztery składniki. **_splitpath** automatycznie obsługuje argumenty ciągów wielobajtowych, rozpoznając sekwencje znaków wielobajtowych zgodnie z aktualnie używaną stroną kodową wielobajtową. **_wsplitpath** jest szerokoznakową wersją **_splitpath**; argumenty, które **mają _wsplitpath,** to ciągi znaków o szerokich znakach. Te funkcje zachowują się identycznie w przeciwnym razie.

**Uwaga dotycząca zabezpieczeń** Te funkcje ponoszą potencjalne zagrożenie spowodowane problemem przepełnienia buforu. Problemy z przepełnieniem buforu są częstą metodą ataku systemu, co powoduje nieuzasadnione podniesienie uprawnień. Aby uzyskać więcej informacji, zobacz [Unikanie przekroczenia buforu](/windows/win32/SecBP/avoiding-buffer-overruns). Dostępne są bezpieczniejsze wersje tych funkcji; patrz [_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath**|**_splitpath**|**_splitpath**|**_wsplitpath**|

Każdy składnik pełnej ścieżki jest przechowywany w oddzielnym buforze; _MAX_DRIVE, **_MAX_DIR,** **_MAX_FNAME**i **_MAX_EXT** (zdefiniowane w STDLIB. **_MAX_DRIVE** H) określić maksymalny rozmiar dla każdego składnika pliku. Składniki plików, które są większe niż odpowiednie stałe manifestu spowodować uszkodzenie sterty.

Każdy bufor musi być tak duży, jak jego odpowiadająca stała manifestu, aby uniknąć potencjalnego przekroczenia buforu.

W poniższej tabeli wymieniono wartości stałych manifestu.

|Nazwa|Wartość|
|----------|-----------|
|**_MAX_DRIVE**|3|
|**_MAX_DIR**|256|
|**_MAX_FNAME**|256|
|**_MAX_EXT**|256|

Jeśli pełna ścieżka nie zawiera składnika (na przykład nazwa pliku), **_splitpath** przypisuje puste ciągi do odpowiednich buforów.

Można przekazać **NULL** do **_splitpath** dla dowolnego parametru innego niż *ścieżka,* która nie jest potrzebna.

Jeśli *ścieżka* ma **wartość NULL**, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [yd.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, **errno** jest ustawiona na **EINVAL** i funkcja zwraca **EINVAL**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_splitpath**|\<>|
|**_wsplitpath**|\<> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [_makepath](makepath-wmakepath.md).

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
