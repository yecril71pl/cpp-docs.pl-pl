---
title: strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l
ms.date: 11/04/2016
api_name:
- strxfrm
- _wcsxfrm_l
- _strxfrm_l
- wcsxfrm
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
ms.openlocfilehash: 411fe3a5a6f66614f0a22e0f623b73685a6e0844
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957608"
---
# <a name="strxfrm-wcsxfrm-_strxfrm_l-_wcsxfrm_l"></a>strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l

Przekształć ciąg w oparciu o informacje specyficzne dla ustawień regionalnych.

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

*strDest*<br/>
Ciąg docelowy.

*strSource*<br/>
Ciąg źródłowy.

*liczbą*<br/>
Maksymalna liczba znaków do umieszczenia w *strDest*.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwraca długość przekształconego ciągu, który nie zlicza kończącego znaku null. Jeśli wartość zwracana jest większa lub równa *liczbie*, zawartość *strDest* jest nieprzewidywalne. W przypadku błędu każda funkcja ustawia **errno** i zwraca **INT_MAX**. Dla nieprawidłowego znaku **errno** jest ustawiony na **EILSEQ**.

## <a name="remarks"></a>Uwagi

Funkcja **strxfrm** przekształca ciąg wskazany przez *strSource* do nowego, posortowanego formularza, który jest przechowywany w *strDest*. Nie więcej niż *Liczba* znaków, w tym znak null, są przekształcane i umieszczane w ciągu wynikowym. Przekształcenie jest realizowane przy użyciu ustawienia kategorii **LC_COLLATE** ustawień regionalnych. Aby uzyskać więcej informacji na temat **LC_COLLATE**, zobacz [setlocale](setlocale-wsetlocale.md). **strxfrm** używa bieżących ustawień regionalnych dla zachowań zależnych od ustawień regionalnych; **_strxfrm_l** jest identyczny, z tą różnicą, że używa ustawień regionalnych przekazaną zamiast bieżących ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Po przekształceniu wywołanie **strcmp** z dwoma przekształconymi ciągami daje wyniki identyczne z wywołaniami **strcoll —** zastosowanymi do oryginalnych dwóch ciągów. Podobnie jak w przypadku **strcoll —** i **stricoll**, **strxfrm** automatycznie obsługuje ciągi znaków wielobajtowych.

**wcsxfrm** to dwubajtowa wersja **strxfrm**; argumenty ciągu **wcsxfrm** są wskaźnikami znaków dwubajtowych. Dla **wcsxfrm**, po przekształceniu ciągu, wywołanie **wcscmp** z dwoma przekształconymi ciągami daje wyniki identyczne z wywołaniami **wcscoll** zastosowanymi do oryginalnych dwóch ciągów. **wcsxfrm** i **strxfrm** zachowują się identycznie w inny sposób. **wcsxfrm** używa bieżących ustawień regionalnych dla zachowań zależnych od ustawień regionalnych; **_wcsxfrm_l** używa ustawień regionalnych przekazaną zamiast bieżących ustawień regionalnych.

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli *strSource* jest wskaźnikiem typu null, lub *strDest* jest wskaźnikiem **null** (chyba że licznik ma wartość zero) lub jeśli *licznik* jest większy niż **INT_MAX**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** na **EINVAL** i zwracają **INT_MAX**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsxfrm**|**strxfrm**|**strxfrm**|**wcsxfrm**|
|**_tcsxfrm_l**|**_strxfrm_l**|**_strxfrm_l**|**_wcsxfrm_l**|

W ustawieniach regionalnych "C" kolejność znaków w zestawie znaków (zestaw znaków ASCII) jest taka sama jak kolejność leksykograficznych znaków. Jednak w innych ustawieniach regionalnych kolejność znaków w zestawie znaków może różnić się od kolejności znaków leksykograficznych. Na przykład w niektórych europejskich ustawieniach regionalnych znak "a" (wartość 0x61) poprzedza znak "&\#x00E4;". (Value 0xE4) w zestawie znaków, ale znak "ä" poprzedza znak "a" lexicographically.

W ustawieniach regionalnych, dla których zestaw znaków i kolejność znaków leksykograficznych są różne, użyj **strxfrm** dla oryginalnych ciągów, a następnie **strcmp** na wynikowych ciągach, aby utworzyć porównanie ciągów leksykograficznych zgodnie z bieżącymi ustawieniami regionalnymi. Ustawienie kategorii **LC_COLLATE** . W tym celu należy porównać dwa ciągi lexicographically w powyższych ustawieniach regionalnych, użyć **strxfrm** dla oryginalnych ciągów, a następnie **strcmp** na wynikowych ciągach. Alternatywnie możesz użyć **strcoll —** zamiast **strcmp** w oryginalnych ciągach.

**strxfrm** jest w zasadzie otoką wokół [LCMapString](/windows/win32/api/winnls/nf-winnls-lcmapstringw) z **LCMAP_SORTKEY**.

Wartość następującego wyrażenia jest rozmiar tablicy wymaganej do przeprowadzenia transformacji **strxfrm** ciągu źródłowego:

`1 + strxfrm( NULL, string, 0 )`

Tylko w ustawieniach regionalnych "C" **strxfrm** jest równoważne z następującymi:

```C
strncpy( _string1, _string2, _count );
return( strlen( _string1 ) );
```

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strxfrm**|\<string.h>|
|**wcsxfrm**|\<ciąg. h > lub \<WCHAR. h >|
|**_strxfrm_l**|\<string.h>|
|**_wcsxfrm_l**|\<ciąg. h > lub \<WCHAR. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll, funkcje](../../c-runtime-library/strcoll-functions.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
