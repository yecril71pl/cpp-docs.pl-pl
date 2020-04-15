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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 1ddc9a991f28c4a2ea491f3ddd04d78f6345e255
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367247"
---
# <a name="wctomb_s-_wctomb_s_l"></a>wctomb_s, _wctomb_s_l

Konwertuje szeroki znak na odpowiedni znak wielobajtowy. Wersja [wctomb, _wctomb_l](wctomb-wctomb-l.md) z ulepszeniami zabezpieczeń, jak opisano w [funkcji zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*wartość pRetValue*<br/>
Liczba bajtów lub kod wskazujący wynik.

*mbchar*<br/>
Adres znaku wielobajtowego.

*rozmiarWzdjęty*<br/>
Rozmiar buforu *mbchar*.

*Wchar*<br/>
Szeroki charakter.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli się powiedzie, kod błędu w przypadku awarii.

Warunki błędu

|*mbchar*|*rozmiarWzdjęty*|Wartość zwracana|*wartość pRetValue*|
|--------------|-------------------|------------------|-----------------|
|**Null**|>0|**Einval**|nie zmodyfikowano|
|Wszelki|>**Int_max**|**Einval**|nie zmodyfikowano|
|Wszelki|za mały|**Einval**|nie zmodyfikowano|

Jeśli wystąpi którykolwiek z powyższych warunków błędu, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [obszarze Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, **wctomb** zwraca **wartość EINVAL** i ustawia **errno** na **EINVAL**.

## <a name="remarks"></a>Uwagi

Funkcja **wctomb_s** konwertuje jego argument *wchar* na odpowiedni znak wielobajtowy i przechowuje wynik w *mbchar*. Funkcję można wywołać z dowolnego punktu w dowolnym programie.

Jeśli **wctomb_s** konwertuje szeroki znak na znak wielobajtowy, umieszcza liczbę bajtów (która nigdy nie jest większa niż **MB_CUR_MAX)** w szerokim znaku do liczby całkowitej wskazywalnej przez *pRetValue*. Jeśli *wchar* jest znakiem zerowym o szerokim znaku (L'\0'), **wctomb_s** wypełnia *pRetValue* 1. Jeśli wskaźnik *docelowy mbchar* ma **wartość NULL**, **wctomb_s** umieszcza 0 w *pRetValue*. Jeśli konwersja nie jest możliwa w bieżących ustawieniach regionalnych, **wctomb_s** umieszcza -1 w *pRetValue*.

**wctomb_s** używa bieżących ustawień regionalnych dla informacji zależnych od ustawień regionalnych; **_wctomb_s_l** jest identyczna, z tą różnicą, że używa ustawień regionalnych przekazanych zamiast. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**wctomb_s**|\<>|
|**_wctomb_s_l**|\<>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Program ten ilustruje zachowanie funkcji **wctomb.**

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
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
