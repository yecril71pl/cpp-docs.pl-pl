---
title: wctomb_s —, _wctomb_s_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wctomb_s_l
- wctomb_s
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wctomb_s
- _wctomb_s_l
dev_langs:
- C++
helpviewer_keywords:
- wctomb_s function
- wctomb_s_l function
- string conversion, wide characters
- wide characters, converting
- _wctomb_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 7e94a888-deed-4dbd-b5e9-d4a0455538b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5bdc05f903c1313d4844be8d5fc4fa619505670
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195122"
---
# <a name="wctombs-wctombsl"></a>wctomb_s, _wctomb_s_l

Konwertuje znak dwubajtowy do odpowiedniego znaku wielobajtowego. Wersja [wctomb —, _wctomb_l —](wctomb-wctomb-l.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Liczba bajtów lub kod informujący o wyniku.

*mbchar*<br/>
Adres znaków wielobajtowych.

*sizeInBytes*<br/>
Rozmiar buforu *mbchar*.

*WChar*<br/>
Znakiem dwubajtowym.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie, kod błędu.

Warunki błędów

|*mbchar*|*sizeInBytes*|Wartość zwracana|*pRetValue*|
|--------------|-------------------|------------------|-----------------|
|**NULL**|>0|**EINVAL**|Nie zmodyfikowano|
|Wszystkie|>**INT_MAX**|**EINVAL**|Nie zmodyfikowano|
|Wszystkie|za mały|**EINVAL**|Nie zmodyfikowano|

Jeśli wystąpi dowolne z powyższych warunków błędu, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **wctomb —** zwraca **EINVAL** i ustawia **errno** do **EINVAL**.

## <a name="remarks"></a>Uwagi

**Wctomb_s —** funkcji konwertuje jej *wchar* argument do odpowiedniego znaku wielobajtowego i zapisuje wynik w *mbchar*. Funkcję można wywołać z dowolnego punktu w dowolnym programie.

Jeśli **wctomb_s —** konwertuje znak dwubajtowy znak wielobajtowy, umieszcza je liczba bajtów (która nigdy nie jest większa niż **MB_CUR_MAX**) w szerokich znaków do liczby całkowitej, wskazywana przez *pRetValue*. Jeśli *wchar* jest znakiem null szerokich znaków (L '\0'), **wctomb_s —** wypełnia *pRetValue* z 1. Jeśli wskaźnik docelowej *mbchar* jest **NULL**, **wctomb_s —** umieszcza 0 w *pRetValue*. Jeśli konwersja nie jest możliwe przy bieżących ustawieniach regionalnych **wctomb_s —** umieszcza -1 w *pRetValue*.

**wctomb_s —** używa bieżących ustawień regionalnych dla informacje zależne od ustawień regionalnych; **_wctomb_s_l —** jest identyczna, z tą różnicą, że używa ustawień regionalnych przekazanych w zamian. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**wctomb_s —**|\<stdlib.h>|
|**_wctomb_s_l**|\<stdlib.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Ten program ilustruje zachowanie **wctomb —** funkcji.

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

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[WideCharToMultiByte](/windows/desktop/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
