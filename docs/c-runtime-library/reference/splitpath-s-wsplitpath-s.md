---
title: _splitpath_s, _wsplitpath_s
ms.date: 11/04/2016
apiname:
- _wsplitpath_s
- _splitpath_s
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
- _wsplitpath_s
- splitpath_s
- _splitpath_s
- wsplitpath_s
helpviewer_keywords:
- splitpath_s function
- pathnames
- _splitpath_s function
- _wsplitpath_s function
- path names
- wsplitpath_s function
ms.assetid: 30fff3e2-cd00-4eb6-b5a2-65db79cb688b
ms.openlocfilehash: 5a6770b7f5f0f8ee82cf86757d14e03b33c1f5d1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602907"
---
# <a name="splitpaths-wsplitpaths"></a>_splitpath_s, _wsplitpath_s

Dzieli ścieżkę na składniki. Są to wersje [_splitpath —, _wsplitpath —](splitpath-wsplitpath.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t _splitpath_s(
   const char * path,
   char * drive,
   size_t driveNumberOfElements,
   char * dir,
   size_t dirNumberOfElements,
   char * fname,
   size_t nameNumberOfElements,
   char * ext,
   size_t extNumberOfElements
);
errno_t _wsplitpath_s(
   const wchar_t * path,
   wchar_t * drive,
   size_t driveNumberOfElements,
   wchar_t *dir,
   size_t dirNumberOfElements,
   wchar_t * fname,
   size_t nameNumberOfElements,
   wchar_t * ext,
   size_t extNumberOfElements
);
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>
errno_t _splitpath_s(
   const char *path,
   char (&drive)[drivesize],
   char (&dir)[dirsize],
   char (&fname)[fnamesize],
   char (&ext)[extsize]
); // C++ only
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>
errno_t _wsplitpath_s(
   const wchar_t *path,
   wchar_t (&drive)[drivesize],
   wchar_t (&dir)[dirsize],
   wchar_t (&fname)[fnamesize],
   wchar_t (&ext)[extsize]
); // C++ only
```

### <a name="parameters"></a>Parametry

*Ścieżka*<br/>
Pełna ścieżka.

*Dysk*<br/>
Litera, następuje dwukropek (**:**). Możesz przekazać **NULL** dla tego parametru, jeśli nie potrzebujesz literę dysku.

*driveNumberOfElements*<br/>
Rozmiar *dysku* buforu znaków jednobajtowych lub szerokiego. Jeśli *dysku* jest **NULL**, ta wartość musi mieć wartość 0.

*dir*<br/>
Ścieżka katalogu, w tym ukośnika. Kreski ułamkowe ( **/** ), ukośniki odwrotne ( **\\** ), lub obie mogą być używane. Możesz przekazać **NULL** dla tego parametru, jeśli nie potrzebujesz ścieżki katalogu.

*dirNumberOfElements*<br/>
Rozmiar *dir* buforu znaków jednobajtowych lub szerokiego. Jeśli *dir* jest **NULL**, ta wartość musi mieć wartość 0.

*fname*<br/>
Nazwa podstawowa pliku (bez rozszerzenia). Możesz przekazać **NULL** dla tego parametru, jeśli nazwa pliku nie jest potrzebna.

*nameNumberOfElements*<br/>
Rozmiar *fname* buforu znaków jednobajtowych lub szerokiego. Jeśli *fname* jest **NULL**, ta wartość musi mieć wartość 0.

*ext*<br/>
Rozszerzenie nazwy pliku, w tym wiodące w okresie (**.**). Możesz przekazać **NULL** dla tego parametru, jeśli nie potrzebujesz rozszerzenie nazwy pliku.

*extNumberOfElements*<br/>
Rozmiar *ext* buforu znaków jednobajtowych lub szerokiego. Jeśli *ext* jest **NULL**, ta wartość musi mieć wartość 0.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie; Kod błędu.

### <a name="error-conditions"></a>Warunki błędów

|Warunek|Wartość zwracana|
|---------------|------------------|
|*ścieżka* jest **o wartości NULL**|**EINVAL**|
|*dysk* jest **NULL**, *driveNumberOfElements* jest różna od zera|**EINVAL**|
|*dysk* ma wartość inną niż**NULL**, *driveNumberOfElements* wynosi zero|**EINVAL**|
|*dir* jest **NULL**, *dirNumberOfElements* jest różna od zera|**EINVAL**|
|*dir* ma wartość inną niż**NULL**, *dirNumberOfElements* wynosi zero|**EINVAL**|
|*fname* jest **NULL**, *nameNumberOfElements* jest różna od zera|**EINVAL**|
|*fname* ma wartość inną niż**NULL**, *nameNumberOfElements* wynosi zero|**EINVAL**|
|*ext* jest **NULL**, *extNumberOfElements* jest różna od zera|**EINVAL**|
|*ext* ma wartość inną niż**NULL**, *extNumberOfElements* wynosi zero|**EINVAL**|

Jeśli wystąpi dowolne z powyższych warunków, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** do **EINVAL** i zwracają **EINVAL**.

Jeśli któryś z buforów, który jest zbyt krótki, aby pomieścić wynik, te funkcje, wyczyść wszystkie bufory puste ciągi, ustaw **errno** do **ERANGE**i zwróć **ERANGE**.

## <a name="remarks"></a>Uwagi

**_Splitpath_s —** funkcja dzieli ścieżkę na jej cztery składniki. **_splitpath_s —** automatycznie obsługuje argumenty ciągu znaków wielobajtowych zgodnie z potrzebami, rozpoznawaniu sekwencje znaków wielobajtowych zgodnie z aktualnie używaną stroną kodową wielobajtowe. **_wsplitpath_s —** to wersja znaku dwubajtowego **_splitpath_s —**; argumenty **_wsplitpath_s —** są ciągami znaków dwubajtowych. Funkcje te zachowują się identycznie

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath_s**|**_splitpath_s**|**_splitpath_s**|**_wsplitpath_s**|

Każdy składnik Pełna ścieżka jest przechowywany w oddzielnych buforu; stałe manifestu **_MAX_DRIVE**, **_MAX_DIR**, **_MAX_FNAME**, i **_MAX_EXT** (zdefiniowany w STDLIB. H) określ maksymalny dozwolony rozmiar dla każdego składnika w pliku. Składniki plików większych niż odpowiednie stałych manifestu spowodować uszkodzenie sterty.

W poniższej tabeli wymieniono wartości stałe manifestu.

|Nazwa|Wartość|
|----------|-----------|
|_MAX_DRIVE|3|
|_MAX_DIR|256|
|_MAX_FNAME|256|
|_MAX_EXT|256|

Jeśli pełna ścieżka nie zawiera składników (na przykład, nazwa_pliku), **_splitpath_s —** przypisuje pusty ciąg znaków do odpowiedniego buforu.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążania szablonu; przeciążenia mogą automatycznie wywnioskować długość buforu, eliminując konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Wersje debugowania tych funkcji najpierw wypełniają bufor 0xfd. Aby wyłączyć to zachowanie, użyj [_crtsetdebugfillthreshold —](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_splitpath_s**|\<stdlib.h>|
|**_wsplitpath_s**|\<stdlib.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [_makepath_s —, _wmakepath_s —](makepath-s-wmakepath-s.md).

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
