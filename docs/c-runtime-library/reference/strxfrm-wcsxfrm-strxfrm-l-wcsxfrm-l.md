---
title: strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l
ms.date: 4/2/2020
api_name:
- strxfrm
- _wcsxfrm_l
- _strxfrm_l
- wcsxfrm
- _o__strxfrm_l
- _o__wcsxfrm_l
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strxfrm
- _tcsxfrm
- wcsxfrm
helpviewer_keywords:
- strxfrm_l function
- _tcsxfrm function
- _strxfrm_l function
- strxfrm function
- wcsxfrm_l function
- wcsxfrm function
- string comparison [C++], transforming strings
- tcsxfrm function
- strings [C++], comparing locale
- _wcsxfrm_l function
ms.assetid: 6ba8e1f6-4484-49aa-83b8-bc2373187d9e
ms.openlocfilehash: aabe7e7c2e44f558b936e0fd4c6fa4a85dc582f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362969"
---
# <a name="strxfrm-wcsxfrm-_strxfrm_l-_wcsxfrm_l"></a>strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l

Przekształcanie ciągu na podstawie informacji specyficznych dla ustawień regionalnych.

## <a name="syntax"></a>Składnia

```C
size_t strxfrm(
   char *strDest,
   const char *strSource,
   size_t count
);
size_t wcsxfrm(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count
);
size_t _strxfrm_l(
   char *strDest,
   const char *strSource,
   size_t count,
   _locale_t locale
);
size_t wcsxfrm_l(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*strDest (strDest)*<br/>
Ciąg docelowy.

*strSource (źródło usług strSource)*<br/>
Ciąg źródłowy.

*Liczba*<br/>
Maksymalna liczba znaków do umieszczenia w *strDest*.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwraca długość przekształconego ciągu, nie licząc kończącego się znaku null. Jeśli zwracana wartość jest większa lub równa *zliczeniu,* zawartość *strDest* jest nieprzewidywalna. W razie błędu każda funkcja ustawia **errno** i zwraca **INT_MAX**. W przypadku nieprawidłowego znaku **errno** jest ustawione na **EILSEQ**.

## <a name="remarks"></a>Uwagi

Funkcja **strxfrm** przekształca ciąg wskazany przez *strSource* w nową formę posortowaną, która jest przechowywana w *strDest*. Nie więcej niż *zliczanie* znaków, w tym znaku null, są przekształcane i umieszczane w wynikowym ciągu. Transformacja jest **dokonywana** przy użyciu ustawienia ustawień LC_COLLATE ustawień kategorii ustawień ustawień regionalnych. Aby uzyskać więcej informacji na temat **LC_COLLATE**, zobacz [setlocale](setlocale-wsetlocale.md). **strxfrm** używa bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych; **_strxfrm_l** jest identyczna, z tą różnicą, że używa ustawień regionalnych przekazanych zamiast bieżących ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Po transformacji wywołanie **strcmp** z dwóch przekształconych ciągów daje wyniki identyczne z wywołaniem **strcoll** stosowane do oryginalnych dwóch ciągów. Podobnie jak **w przypadku strcoll** i **stricoll,** **strxfrm** automatycznie obsługuje ciągi znaków wielobajtowych, stosownie do przypadku.

**wcsxfrm** jest szerokoznakową wersją **strxfrm;** argumenty ciągu **wcsxfrm** są wskaźnikami o szerokich znakach. Dla **wcsxfrm**, po transformacji ciągu, wywołanie **wcscmp** z dwóch przekształconych ciągów daje wyniki identyczne z tymi wywołania **wcscoll** stosowane do oryginalnych dwóch ciągów. **wcsxfrm** i **strxfrm** zachowują się identycznie inaczej. **wcsxfrm** używa bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych; **_wcsxfrm_l** używa ustawień regionalnych przekazanych zamiast bieżących ustawień regionalnych.

Te funkcje sprawdzają ich parametry. Jeśli *strSource* jest wskaźnikiem zerowym lub *strDest* jest wskaźnikiem **NULL** (chyba że liczba wynosi zero) lub jeśli *liczba* jest większa niż **INT_MAX,** wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [zatwierdzeniu parametru.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, te funkcje **ustawiają errno** na **EINVAL** i zwracają **INT_MAX**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsxfrm**|**strxfrm**|**strxfrm**|**wcsxfrm**|
|**_tcsxfrm_l**|**_strxfrm_l**|**_strxfrm_l**|**_wcsxfrm_l**|

W ustawieniach regionalnych "C" kolejność znaków w zestawie znaków (zestaw znaków ASCII) jest taka sama jak kolejność leksykograficzna znaków. Jednak w innych ustawieniach regionalnych kolejność znaków w zestawie znaków może różnić się od kolejności znaków leksykograficznych. Na przykład w niektórych europejskich ustawieniach regionalnych znak "a" (wartość 0x61) poprzedza znak "&\#x00E4;" (wartość 0xE4) w zestawie znaków, ale znak "ä" poprzedza znak "a" leksykograficznie.

W ustawieniach regionalnych, dla których zestaw znaków i kolejność znaków leksykograficznych różnią się, użyj **strxfrm** na oryginalnych ciągów, a następnie **strcmp** na wynikowych ciągów do produkcji porównania ciągów leksykograficznych zgodnie z bieżącą ustawieńą LC_COLLATE **kategorii** ustawień ustawień regionalnych. W ten sposób, aby porównać dwa ciągi leksykograficzne w powyższych ustawieniach regionalnych, użyj **strxfrm** na oryginalnych ciągach, a następnie **strcmp** na wynikowych ciągów. Alternatywnie można użyć **strcoll** zamiast **strcmp** na oryginalnych ciągów.

**strxfrm** jest w zasadzie opakowanie wokół [LCMapString](/windows/win32/api/winnls/nf-winnls-lcmapstringw) z **LCMAP_SORTKEY**.

Wartość następującego wyrażenia jest rozmiar tablicy potrzebne do przechowywania **transformacji strxfrm** ciągu źródłowego:

`1 + strxfrm( NULL, string, 0 )`

Tylko w ustawieniach regionalnych "C" **strxfrm** jest odpowiednikiem następujących:

```C
strncpy( _string1, _string2, _count );
return( strlen( _string1 ) );
```

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strxfrm**|\<string.h>|
|**wcsxfrm**|\<string.h> lub \<wchar.h>|
|**_strxfrm_l**|\<string.h>|
|**_wcsxfrm_l**|\<string.h> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll — Funkcje](../../c-runtime-library/strcoll-functions.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
