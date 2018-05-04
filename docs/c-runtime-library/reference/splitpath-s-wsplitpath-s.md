---
title: _splitpath_s —, _wsplitpath_s — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- splitpath_s function
- pathnames
- _splitpath_s function
- _wsplitpath_s function
- path names
- wsplitpath_s function
ms.assetid: 30fff3e2-cd00-4eb6-b5a2-65db79cb688b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5fd1407aa6c2b7630e0720eeec179ca27e7d31a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="splitpaths-wsplitpaths"></a>_splitpath_s, _wsplitpath_s

Dzieli nazwa ścieżki na składniki. Są to wersje [_splitpath —, _wsplitpath —](splitpath-wsplitpath.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Dysk litery z dwukropkiem (**:**). Można przekazać **NULL** dla tego parametru, jeśli nie ma potrzeby literę dysku.

*driveNumberOfElements*<br/>
Rozmiar *dysku* buforu w znaki jednobajtowe lub szerokości. Jeśli *dysku* jest **NULL**, ta wartość musi wynosić 0.

*Dir*<br/>
Ścieżka katalogu, w tym ukośnika. Przekazuj ukośniki ( **/** ), ukośników odwrotnych ( **\\** ), lub mogą być używane. Można przekazać **NULL** dla tego parametru, jeśli nie ma potrzeby ścieżki katalogu.

*dirNumberOfElements*<br/>
Rozmiar *dir* buforu w znaki jednobajtowe lub szerokości. Jeśli *dir* jest **NULL**, ta wartość musi wynosić 0.

*fname*<br/>
Nazwa podstawowego pliku (bez rozszerzenia). Można przekazać **NULL** dla tego parametru, jeśli nazwa pliku nie ma potrzeby.

*nameNumberOfElements*<br/>
Rozmiar *fname* buforu w znaki jednobajtowe lub szerokości. Jeśli *fname* jest **NULL**, ta wartość musi wynosić 0.

*numer wewnętrzny*<br/>
Rozszerzenie nazwy pliku, w tym wiodące okres (**.**). Można przekazać **NULL** dla tego parametru, jeśli nie ma potrzeby rozszerzenie nazwy pliku.

*extNumberOfElements*<br/>
Rozmiar *ext* buforu w znaki jednobajtowe lub szerokości. Jeśli *ext* jest **NULL**, ta wartość musi wynosić 0.

## <a name="return-value"></a>Wartość zwracana

Zero w przypadku powodzenia; błąd o kodzie błędu.

### <a name="error-conditions"></a>Warunki błędów

|Warunek|Wartość zwracana|
|---------------|------------------|
|*ścieżka* jest **wartości NULL**|**EINVAL —**|
|*dysk* jest **NULL**, *driveNumberOfElements* jest różna od zera|**EINVAL —**|
|*dysk* ma wartość inną niż**NULL**, *driveNumberOfElements* wynosi zero|**EINVAL —**|
|*dir* jest **NULL**, *dirNumberOfElements* jest różna od zera|**EINVAL —**|
|*dir* ma wartość inną niż**NULL**, *dirNumberOfElements* wynosi zero|**EINVAL —**|
|*fname* jest **NULL**, *nameNumberOfElements* jest różna od zera|**EINVAL —**|
|*fname* ma wartość inną niż**NULL**, *nameNumberOfElements* wynosi zero|**EINVAL —**|
|*Roz* jest **NULL**, *extNumberOfElements* jest różna od zera|**EINVAL —**|
|*Roz* ma wartość inną niż**NULL**, *extNumberOfElements* wynosi zero|**EINVAL —**|

Jeśli występuje którykolwiek z powyższych warunków, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md) . Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji **errno** do **einval —** i zwracać **einval —**.

Jeśli dowolny z bufor jest zbyt krótki, aby pomieścić wynik, te funkcje, wyczyść wszystkie bufory puste ciągi, ustaw **errno** do **erange —**i zwróć **erange —**.

## <a name="remarks"></a>Uwagi

**_Splitpath_s —** funkcja dzieli ścieżki do jego czterech składników. **_splitpath_s —** automatycznie obsługuje argumentów ciągów znaków wielobajtowych zgodnie z potrzebami, rozpoznawanie wielobajtowych sekwencji znaków zgodnie ze strony kodowe wielobajtowe obecnie w użyciu. **_wsplitpath_s —** jest wersja znaków dwubajtowych **_splitpath_s —**; argumenty **_wsplitpath_s —** są ciągami znaków dwubajtowych. Funkcje te działają tak samo w przeciwnym razie

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath_s**|**_splitpath_s**|**_splitpath_s**|**_wsplitpath_s**|

Każdy składnik pełnej ścieżki są przechowywane w oddzielnych buforu; stałe manifestu **_max_drive —**, **_max_dir —**, **_max_fname —**, i **_max_ext —** (zdefiniowany w STDLIB. H) określić maksymalny dozwolony rozmiar dla każdego składnika pliku. Składniki plików większych niż odpowiedni stałe manifestu spowodować uszkodzenie sterty.

W poniższej tabeli wymieniono wartości stałe manifestu.

|Nazwa|Wartość|
|----------|-----------|
|_MAX_DRIVE|3|
|_MAX_DIR|256|
|_MAX_FNAME|256|
|_MAX_EXT|256|

Jeśli pełna ścieżka nie zawiera składników (na przykład nazwy pliku), **_splitpath_s —** przypisuje pustego ciągu do odpowiedniego buforu.

W języku C++ za pomocą tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można wnioskować o długości buforu automatycznie, co eliminuje konieczność określić argument rozmiar. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).

Wersje tych funkcji do debugowania najpierw wprowadzić bufor 0xFD. Aby wyłączyć to zachowanie, użyj [_crtsetdebugfillthreshold —](crtsetdebugfillthreshold.md).

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
