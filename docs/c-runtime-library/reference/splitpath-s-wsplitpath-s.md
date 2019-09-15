---
title: _splitpath_s, _wsplitpath_s
ms.date: 11/04/2016
api_name:
- _wsplitpath_s
- _splitpath_s
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: f97c07ed01ae629fe3eb61346c6c0fcd8fa803f0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958052"
---
# <a name="_splitpath_s-_wsplitpath_s"></a>_splitpath_s, _wsplitpath_s

Dzieli nazwę ścieżki na składniki. Są to wersje [_splitpath, _wsplitpath](splitpath-wsplitpath.md) z ulepszeniami zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*litera*<br/>
Litera dysku, po którym następuje dwukropek ( **:** ). Jeśli nie potrzebujesz litery dysku, możesz przekazać **wartość null** dla tego parametru.

*driveNumberOfElements*<br/>
Rozmiar buforu *dysku* w znakach jednobajtowych lub szerokich. Jeśli *dysk* ma wartość **null**, ta wartość musi być równa 0.

*katalogów*<br/>
Ścieżka katalogu, włącznie z końcowym ukośnikiem. Można używać ukośników **/** (), ukośników odwrotnych ( **\\** ) lub obu tych wartości. Jeśli ścieżka katalogu nie jest potrzebna, można przekazać **wartość null** dla tego parametru.

*dirNumberOfElements*<br/>
Rozmiar buforu *dir* w znakach jednobajtowych lub szerokich. Jeśli *dir* ma wartość **null**, ta wartość musi być równa 0.

*fname*<br/>
Podstawowa nazwa pliku (bez rozszerzenia). Jeśli nazwa pliku nie jest potrzebna, można przekazać **wartość null** dla tego parametru.

*nameNumberOfElements*<br/>
Rozmiar buforu *fname* w znakach jednobajtowych lub szerokich. Jeśli *fname* ma wartość **null**, ta wartość musi być równa 0.

*EXT*<br/>
Rozszerzenie nazwy pliku, włącznie z kropką wiodącą ( **.** ). Jeśli rozszerzenie nazwy pliku nie jest potrzebne, można przekazać **wartość null** dla tego parametru.

*extNumberOfElements*<br/>
Rozmiar buforu *EXT* w znakach jednobajtowych lub szerokich. Jeśli *EXT* ma wartość **null**, ta wartość musi być równa 0.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli pomyślne; kod błędu w przypadku niepowodzenia.

### <a name="error-conditions"></a>Warunki błędów

|Warunek|Wartość zwracana|
|---------------|------------------|
|*ścieżka* ma **wartość null**|**EINVAL**|
|*dysk* ma **wartość null**, *driveNumberOfElements* jest różny od zera.|**EINVAL**|
|*dysk* ma wartość różną od**null**, *driveNumberOfElements* ma wartość zero|**EINVAL**|
|*dir* ma **wartość null**, *dirNumberOfElements* jest różna od zera.|**EINVAL**|
|*dir* ma wartość różną od**null**, *dirNumberOfElements* ma wartość zero|**EINVAL**|
|*fname* ma **wartość null**, *nameNumberOfElements* jest różna od zera|**EINVAL**|
|*fname* jest różna od**null**, *nameNumberOfElements* jest zerem|**EINVAL**|
|*EXT* ma **wartość null**, *extNumberOfElements* jest różna od zera.|**EINVAL**|
|*EXT* ma wartość różną od**null**, *extNumberOfElements* jest zerem|**EINVAL**|

Jeśli wystąpi którykolwiek z powyższych warunków, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** na **EINVAL** i zwracają **EINVAL**.

Jeśli którykolwiek z buforów jest zbyt krótki, aby pomieścić wynik, te funkcje Wyczyść wszystkie bufory do pustych ciągów, ustaw **errno** na **ERANGE**i zwróć **ERANGE**.

## <a name="remarks"></a>Uwagi

Funkcja **_splitpath_s** dzieli ścieżkę na cztery składniki. **_splitpath_s** automatycznie obsługuje argumenty ciągu znaków wielobajtowych, aby rozpoznać sekwencje znaków wielobajtowych zgodnie z aktualnie używaną stroną kodową. **_wsplitpath_s** to dwubajtowa wersja **_splitpath_s**; argumenty **_wsplitpath_s** są ciągami znaków dwubajtowych. Funkcje te zachowują się identycznie w inny sposób

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath_s**|**_splitpath_s**|**_splitpath_s**|**_wsplitpath_s**|

Każdy składnik pełnej ścieżki jest przechowywany w osobnym buforze; stałe manifestu **_MAX_DRIVE**, **_MAX_DIR**, **_MAX_FNAME**i **_MAX_EXT** (zdefiniowane w STDLIB. H) Określ maksymalny dozwolony rozmiar każdego składnika plików. Składniki plików większe niż odpowiednie stałe manifestu powodują uszkodzenie sterty.

Poniższa tabela zawiera listę wartości stałych manifestu.

|Nazwa|Wartość|
|----------|-----------|
|_MAX_DRIVE|3|
|_MAX_DIR|256|
|_MAX_FNAME|256|
|_MAX_EXT|256|

Jeśli pełna ścieżka nie zawiera składnika (na przykład filename), **_splitpath_s** przypisze pusty ciąg do odpowiedniego buforu.

W C++programie korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonów; przeciążenia mogą automatycznie wywnioskować długość buforu, eliminując konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

Wersje debugowania tych funkcji najpierw wypełniają bufor 0xFD. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_splitpath_s**|\<stdlib.h>|
|**_wsplitpath_s**|\<STDLIB. h > lub \<WCHAR. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład dla [_makepath_s, _wmakepath_s](makepath-s-wmakepath-s.md).

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
