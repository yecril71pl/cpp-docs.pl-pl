---
title: strxfrm —, wcsxfrm —, _strxfrm_l —, _wcsxfrm_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- strxfrm
- _wcsxfrm_l
- _strxfrm_l
- wcsxfrm
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- strxfrm
- _tcsxfrm
- wcsxfrm
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 96f459c8360969146f8cf76a48c9141000066745
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214296"
---
# <a name="strxfrm-wcsxfrm-strxfrml-wcsxfrml"></a>strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l

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

*Liczba*<br/>
Maksymalna liczba znaków do umieszczenia w *strDest*.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwraca długość ciągu przekształcone, nie licząc zamykającego kończącego znaku null. Jeśli wartość zwracana jest większa niż lub równa *liczba*, zawartość *strDest* jest nieprzewidywalne. W przypadku błędu, każda funkcja ustawia **errno** i zwraca **INT_MAX**. Nieprawidłowy znak **errno** ustawiono **EILSEQ**.

## <a name="remarks"></a>Uwagi

**Strxfrm —** funkcja przekształca ciągu wskazywany przez *strSource* w nowym sortowane formularz, która jest przechowywana w *strDest*. Nie więcej niż *liczba* znaków, łącznie ze znakiem zerowym, są przetwarzane i umieszczane w ciągu wynikowym. Transformacja jest wykonywane przy użyciu ustawień regionalnych **LC_COLLATE** ustawienie kategorii. Aby uzyskać więcej informacji na temat **LC_COLLATE**, zobacz [setlocale](setlocale-wsetlocale.md). **strxfrm —** używa bieżących ustawień regionalnych dla wszelkich zachowań; **_strxfrm_l —** jest identyczna, z tą różnicą, że używa ustawień regionalnych przekazanych w zamiast bieżących ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Po przekształceniu wywołanie **strcmp —** daje wyniki identyczne z tymi wywołanie, za pomocą dwóch ciągów przekształcone **strcoll —** stosowane do oryginalnego dwa ciągi. Podobnie jak w przypadku **strcoll —** i **stricoll —**, **strxfrm —** automatycznie obsługuje ciągi znaków wielobajtowych zgodnie z potrzebami.

**wcsxfrm —** to wersja znaku dwubajtowego **strxfrm —**; argumenty ciągu **wcsxfrm —** są wskaźnikami znaków dwubajtowych. Dla **wcsxfrm —** po przekształcać ciągu, po wywołaniu **wcscmp —** daje wyniki identyczne z tymi wywołanie, za pomocą dwóch ciągów przekształcone **wcscoll —** stosowane do oryginalny dwa ciągi. **wcsxfrm —** i **strxfrm —** zachowują się identycznie. **wcsxfrm —** używa bieżących ustawień regionalnych dla wszelkich zachowań; **_wcsxfrm_l —** używa ustawień regionalnych przekazanych zamiast bieżących ustawień regionalnych.

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli *strSource* jest wskaźnikiem wartości null lub *strDest* jest **NULL** wskaźnika (chyba że liczba jest równy zero), lub jeśli *liczba* jest większa niż **INT_MAX**, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** do **EINVAL** i zwracają **INT_MAX**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsxfrm —**|**strxfrm**|**strxfrm**|**wcsxfrm**|
|**_tcsxfrm_l**|**_strxfrm_l**|**_strxfrm_l**|**_wcsxfrm_l**|

W ustawieniach regionalnych "języka C" kolejność znaków w zestawie znaków (zestaw znaków ASCII) jest taka sama, jak w porządku leksykograficznym znaków. Jednak w innych lokalizacjach, w kolejności znaków w zestawie znaków mogą się różnić z kolejnością znaków leksykograficznych. Na przykład, w niektórych Europejskiego ustawień regionalnych znaków ' "(wartość 0x61) poprzedza znak" &\#x00E4; " (wartość 0xE4) w zestawie znaków, ale znak "ä" poprzedza znak "a" leksykograficznie.

W lokalizacjach, w których zestaw znaków i kolejnością znaków leksykograficznych różnią się, należy użyć **strxfrm —** dla oryginalnego ciągów i następnie **strcmp —** na wynikowej ciągów w celu utworzenia leksykograficznych ciąg Porównanie zgodnie z bieżących ustawień regionalnych **LC_COLLATE** ustawienie kategorii. W związku z tym, aby porównać dwóch ciągów lexicographically w powyższych ustawień regionalnych, należy użyć **strxfrm —** na oryginalnym ciągów, a następnie **strcmp —** na ciągi wynikowe. Alternatywnie możesz użyć **strcoll —** zamiast **strcmp —** na oryginalnym ciągów.

**strxfrm —** jest zasadniczo otokę [LCMapString](/windows/desktop/api/winnls/nf-winnls-lcmapstringa) z **LCMAP_SORTKEY**.

Wartość następującego wyrażenia jest rozmiar tablicy potrzebne do przechowywania **strxfrm —** przemian ciąg źródłowy:

`1 + strxfrm( NULL, string, 0 )`

W ustawieniach "języka C" regionalnych tylko **strxfrm —** jest odpowiednikiem następujących czynności:

```C
strncpy( _string1, _string2, _count );
return( strlen( _string1 ) );
```

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strxfrm**|\<string.h>|
|**wcsxfrm**|\<Włącz String.h > lub \<wchar.h >|
|**_strxfrm_l**|\<string.h>|
|**_wcsxfrm_l**|\<Włącz String.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll, funkcje](../../c-runtime-library/strcoll-functions.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
