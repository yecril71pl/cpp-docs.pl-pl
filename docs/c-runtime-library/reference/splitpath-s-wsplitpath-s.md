---
title: _splitpath_s, _wsplitpath_s
ms.date: 4/2/2020
api_name:
- _wsplitpath_s
- _splitpath_s
- _o__splitpath_s
- _o__wsplitpath_s
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 364544a9423668494747405e801d59b73de4e6c6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355616"
---
# <a name="_splitpath_s-_wsplitpath_s"></a>_splitpath_s, _wsplitpath_s

Dzieli nazwę ścieżki na składniki. Są to wersje [_splitpath, _wsplitpath](splitpath-wsplitpath.md) z ulepszeniami zabezpieczeń, jak opisano w [programie Funkcje zabezpieczeń w programie CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Dysku*<br/>
List dysku, po którym następuje dwukropek (**:**). Można przekazać **null** dla tego parametru, jeśli nie potrzebujesz litery dysku.

*elementy driveNumberOfElements*<br/>
Rozmiar buforu *dysku* w znakach jedno bajtowych lub szerokich. Jeśli *dysk* ma **wartość NULL**, ta wartość musi wynosić 0.

*Dir*<br/>
Ścieżka katalogu, w tym ukośnik na końcu. Można użyć **/** ukośników do **\\** przodu ( ), ukośników odwrotnych ( ) lub obu. Można przekazać **null** dla tego parametru, jeśli nie potrzebujesz ścieżki katalogu.

*dirNumberOfElements*<br/>
Rozmiar buforu *dir* w pojedynczych lub szerokich znakach. Jeśli *dir* ma **wartość NULL**, ta wartość musi wynosić 0.

*Fname*<br/>
Podstawowa nazwa pliku (bez rozszerzenia). Można przekazać **null** dla tego parametru, jeśli nie potrzebujesz nazwy pliku.

*nazwaNumberOfElements*<br/>
Rozmiar buforu *fname* w postaci jedno bajtowej lub szerokiej. Jeśli *wartość fname* ma **wartość NULL**, wartość ta musi wynosić 0.

*Ext*<br/>
Rozszerzenie nazwy pliku, w tym okres wiodący (**.**). Możesz przekazać **wartość NULL** dla tego parametru, jeśli nie jest potrzebne rozszerzenie nazwy pliku.

*extNumberOfElements*<br/>
Rozmiar buforu *ext* w znakach jedno bajtowych lub szerokich. Jeśli *ext* ma **wartość NULL**, ta wartość musi wynosić 0.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli się powiedzie; kod błędu w przypadku awarii.

### <a name="error-conditions"></a>Warunki błędu

|Warunek|Wartość zwracana|
|---------------|------------------|
|*ścieżka* ma **wartość NULL**|**Einval**|
|*dysk* ma **wartość NULL**, *driveNumberOfElements* jest niezerowy|**Einval**|
|*dysk* jest**nie-NULL**, *driveNumberOfElements* wynosi zero|**Einval**|
|*dir* is **NULL**, *dirNumberOfElements* jest niezerowy|**Einval**|
|*dir* jest**nie-NULL**, *dirNumberOfElements* jest zero|**Einval**|
|*fname* jest **NULL**, *nazwaNumberOfElements* jest niezerowa|**Einval**|
|*fname* jest**nie-NULL**, *nazwaNumberOfElements* wynosi zero|**Einval**|
|*ext* ma **wartość NULL**, *extNumberOfElements* jest niezerowy|**Einval**|
|*ext* jest**nie-NULL**, *extNumberOfElements* wynosi zero|**Einval**|

Jeśli wystąpi którykolwiek z powyższych warunków, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [zatwierdzeniu parametru.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, te funkcje **ustawiają errno** na **EINVAL** i zwracają **EINVAL**.

Jeśli którykolwiek z buforów jest zbyt krótki, aby utrzymać wynik, te funkcje wyczyścić wszystkie bufory do pustych ciągów, ustawić **errno** na **ERANGE**i zwrócić **ERANGE**.

## <a name="remarks"></a>Uwagi

Funkcja **_splitpath_s** dzieli ścieżkę na cztery składniki. **_splitpath_s** automatycznie obsługuje argumenty ciągów wielobajtowych, rozpoznając sekwencje znaków wielobajtowych zgodnie z aktualnie używaną stroną kodową wielobajtową. **_wsplitpath_s** jest szerokoznakową wersją **_splitpath_s**; argumenty, które **mają _wsplitpath_s,** to ciągi znaków o szerokich znakach. Funkcje te zachowują się identycznie w przeciwnym razie

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath_s**|**_splitpath_s**|**_splitpath_s**|**_wsplitpath_s**|

Każdy składnik pełnej ścieżki jest przechowywany w oddzielnym buforze; _MAX_DRIVE, **_MAX_DIR,** **_MAX_FNAME**i **_MAX_EXT** (zdefiniowane w STDLIB. **_MAX_DRIVE** H) określić maksymalny dopuszczalny rozmiar dla każdego składnika pliku. Składniki plików większe niż odpowiednie stałe manifestu powodują uszkodzenie sterty.

W poniższej tabeli wymieniono wartości stałych manifestu.

|Nazwa|Wartość|
|----------|-----------|
|_MAX_DRIVE|3|
|_MAX_DIR|256|
|_MAX_FNAME|256|
|_MAX_EXT|256|

Jeśli pełna ścieżka nie zawiera składnika (na przykład nazwa pliku), **_splitpath_s** przypisuje pusty ciąg do odpowiedniego buforu.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonu; przeciążenia można wywnioskować długość buforu automatycznie, eliminując konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Wersje biblioteki debugowania tych funkcji najpierw wypełniają bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_splitpath_s**|\<>|
|**_wsplitpath_s**|\<> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [_makepath_s, _wmakepath_s](makepath-s-wmakepath-s.md).

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
