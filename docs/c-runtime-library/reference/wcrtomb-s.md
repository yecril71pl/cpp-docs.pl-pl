---
title: wcrtomb_s
ms.date: 4/2/2020
api_name:
- wcrtomb_s
- _o_wcrtomb_s
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
- wcrtomb_s
helpviewer_keywords:
- wide characters, converting
- wcrtomb_s function
- multibyte characters
- characters, converting
ms.assetid: 9a8a1bd0-1d60-463d-a3a2-d83525eaf656
ms.openlocfilehash: 51985b008565cbe550065b85261b8beb53ed6f89
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915962"
---
# <a name="wcrtomb_s"></a>wcrtomb_s

Konwertuj znak dwubajtowy na swoją reprezentację znaku wieloznacznego. Wersja [wcrtomb](wcrtomb.md) z ulepszeniami zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t wcrtomb_s(
   size_t *pReturnValue,
   char *mbchar,
   size_t sizeOfmbchar,
   wchar_t *wchar,
   mbstate_t *mbstate
);
template <size_t size>
errno_t wcrtomb_s(
   size_t *pReturnValue,
   char (&mbchar)[size],
   wchar_t *wchar,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parametry

*pReturnValue*<br/>
Zwraca liczbę bajtów zapisanych lub-1, jeśli wystąpił błąd.

*mbchar*<br/>
Wynikiem konwersji wielobajtowego znaku.

*sizeOfmbchar*<br/>
Rozmiar zmiennej *mbchar* w bajtach.

*WCHAR*<br/>
Znak dwubajtowy do przekonwertowania.

*mbstate*<br/>
Wskaźnik do obiektu **mbstate_t** .

## <a name="return-value"></a>Wartość zwracana

Zwraca zero lub wartość **errno** , jeśli wystąpi błąd.

## <a name="remarks"></a>Uwagi

Funkcja **wcrtomb_s** konwertuje znak dwubajtowy, zaczynając od określonego stanu konwersji zawartego w *mbstate*, z wartości zawartej w *WCHAR*, do adresu reprezentowanego przez *mbchar*. Wartość *pReturnValue* będzie liczbą przekonwertowanych bajtów, ale nie więcej niż **MB_CUR_MAX** bajtów lub wartość-1, jeśli wystąpił błąd.

Jeśli *mbstate* ma wartość null, używany jest wewnętrzny stan konwersji **mbstate_t** . Jeśli znak zawarty w *WCHAR* nie ma odpowiedniego znaku wielobajtowego, wartość *pReturnValue* będzie równa-1, a funkcja zwróci wartość **errno** **EILSEQ**.

Funkcja **wcrtomb_s** różni się od [wctomb_s, _wctomb_s_l](wctomb-s-wctomb-s-l.md) od jej uruchomienia. Stan konwersji jest przechowywany w *mbstate* dla kolejnych wywołań do tych samych lub innych funkcji, które można uruchomić ponownie. Wyniki są niezdefiniowane podczas mieszania użycia funkcji ponownego uruchamiania i nieuruchomionych ponownie. Na przykład aplikacja będzie używać **wcsrlen** zamiast **wcslen**, jeśli podczas kolejnego wywołania do **wcsrtombs_s** były używane zamiast **wcstombs_s**.

W języku C++ korzystanie z tej funkcji jest uproszczone przez przeciążenia szablonów; przeciążenia mogą automatycznie wywnioskować długość buforu (eliminując konieczność określenia argumentu rozmiaru) i mogą automatycznie zastąpić starsze, niezabezpieczone funkcje z ich nowszymi, bezpiecznymi odpowiednikami. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="exceptions"></a>Wyjątki

Funkcja **wcrtomb_s** jest bezpiecznie wielowątkowej, dopóki żadna funkcja w bieżącym wątku nie wywołuje metody **setlocaling** , podczas gdy ta funkcja jest wykonywana, a *mbstate* ma wartość null.

## <a name="example"></a>Przykład

```C
// crt_wcrtomb_s.c
// This program converts a wide character
// to its corresponding multibyte character.
//

#include <string.h>
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    errno_t     returnValue;
    size_t      pReturnValue;
    mbstate_t   mbstate;
    size_t      sizeOfmbStr = 1;
    char        mbchar = 0;
    wchar_t*    wchar = L"Q\0";

    // Reset to initial conversion state
    memset(&mbstate, 0, sizeof(mbstate));

    returnValue = wcrtomb_s(&pReturnValue, &mbchar, sizeof(char),
                            *wchar, &mbstate);
    if (returnValue == 0) {
        printf("The corresponding wide character \"");
        wprintf(L"%s\"", wchar);
        printf(" was converted to a the \"%c\" ", mbchar);
        printf("multibyte character.\n");
    }
    else
    {
        printf("No corresponding multibyte character "
               "was found.\n");
    }
}
```

```Output
The corresponding wide character "Q" was converted to a the "Q" multibyte character.
```

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**wcrtomb_s**|\<WCHAR. h>|

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Ustawienie](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
