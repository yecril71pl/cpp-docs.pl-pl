---
title: wctomb_s, _wctomb_s_l
ms.date: 4/2/2020
api_name:
- _wctomb_s_l
- wctomb_s
- _o__wctomb_s_l
- _o_wctomb_s
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctomb_s
- _wctomb_s_l
helpviewer_keywords:
- wctomb_s function
- wctomb_s_l function
- string conversion, wide characters
- wide characters, converting
- _wctomb_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 7e94a888-deed-4dbd-b5e9-d4a0455538b8
ms.openlocfilehash: 63839f70fa334fadd961eb173343d1b406268cfd
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910442"
---
# <a name="wctomb_s-_wctomb_s_l"></a>wctomb_s, _wctomb_s_l

Konwertuje znak szeroki do odpowiadającego mu znaku wielobajtowego. Wersja [wctomb, _wctomb_l](wctomb-wctomb-l.md) z ulepszeniami zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t wctomb_s(
   int *pRetValue,
   char *mbchar,
   size_t sizeInBytes,
   wchar_t wchar
);
errno_t _wctomb_s_l(
   int *pRetValue,
   char *mbchar,
   size_t sizeInBytes,
   wchar_t wchar,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*pRetValue*<br/>
Liczba bajtów lub kod wskazujący wynik.

*mbchar*<br/>
Adres znaku wielobajtowego.

*sizeInBytes*<br/>
Rozmiar bufora *mbchar*.

*WCHAR*<br/>
Znak dwubajtowy.

*locale*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie, kod błędu w przypadku niepowodzenia.

Warunki błędów

|*mbchar*|*sizeInBytes*|Wartość zwracana|*pRetValue*|
|--------------|-------------------|------------------|-----------------|
|**NULL**|>0|**EINVAL**|nie zmodyfikowano|
|ile|>**INT_MAX**|**EINVAL**|nie zmodyfikowano|
|ile|za mały|**EINVAL**|nie zmodyfikowano|

Jeśli wystąpi którykolwiek z powyższych warunków błędu, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja **wctomb** zwraca **EINVAL** i ustawia **errno** na **EINVAL**.

## <a name="remarks"></a>Uwagi

Funkcja **wctomb_s** konwertuje swój argument *WCHAR* na odpowiedni znak wielobajtowy i zapisuje wynik w *mbchar*. Można wywołać funkcję z dowolnego punktu w dowolnym programie.

Jeśli **wctomb_s** konwertuje znak szeroki do znaku wielobajtowego, umieszcza liczbę bajtów (która nigdy nie jest większa niż **MB_CUR_MAX**) w znaku szerokiego do liczby całkowitej wskazywanej przez *pRetValue*. Jeśli *WCHAR* jest znakiem dwubajtowym znaku null (L ' \ 0 '), **wctomb_s** wypełnia *pRetValue* z 1. Jeśli docelowy wskaźnik *mbchar* ma **wartość null**, **wctomb_s** umieszcza 0 w *pRetValue*. Jeśli konwersja nie jest możliwa w bieżących ustawieniach regionalnych, **wctomb_s** Put-1 w *pRetValue*.

**wctomb_s** używa bieżących ustawień regionalnych dla informacji zależnych od ustawień regionalnych; **_wctomb_s_l** jest identyczny, z tą różnicą, że w zamian korzysta z przekazaną ustawieniami regionalnymi. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**wctomb_s**|\<STDLIB. h>|
|**_wctomb_s_l**|\<STDLIB. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Ten program ilustruje zachowanie funkcji **wctomb** .

```cpp
// crt_wctomb_s.cpp
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
    int i;
    wchar_t wc = L'a';
    char *pmb = (char *)malloc( MB_CUR_MAX );

    printf_s( "Convert a wide character:\n" );
    wctomb_s( &i, pmb, MB_CUR_MAX, wc );
    printf_s( "   Characters converted: %u\n", i );
    printf_s( "   Multibyte character: %.1s\n\n", pmb );
}
```

```Output
Convert a wide character:
   Characters converted: 1
   Multibyte character: a
```

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Ustawienie](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
