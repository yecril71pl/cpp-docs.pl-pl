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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: ee25b18bfbb86b34e46c8c6776e8ab83157613e8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328169"
---
# <a name="wcrtomb_s"></a>wcrtomb_s

Konwertuj szeroki znak na jego wielobajtową reprezentację znaków. Wersja [wcrtomb](wcrtomb.md) z ulepszeniami zabezpieczeń, jak opisano w [funkcji zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*pZawąkaWartość*<br/>
Zwraca liczbę bajtów zapisanych lub -1, jeśli wystąpił błąd.

*mbchar*<br/>
Wynikowy znak przekonwertowany wielobajtowy.

*rozmiarOfmbchar*<br/>
Rozmiar zmiennej *mbchar* w bajtach.

*Wchar*<br/>
Szeroki znak do konwersji.

*mbstate*<br/>
Wskaźnik do **obiektu mbstate_t.**

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość zero lub **errno,** jeśli wystąpi błąd.

## <a name="remarks"></a>Uwagi

Funkcja **wcrtomb_s** konwertuje szeroki znak, zaczynając od określonego stanu konwersji zawartego w *mbstate,* z wartości zawartej w *wchar,* na adres reprezentowany przez *mbchar*. Wartość *pReturnValue* będzie liczbą przekonwertowanych bajtów, ale nie większą niż **MB_CUR_MAX** bajtów lub -1, jeśli wystąpił błąd.

Jeśli *mbstate* ma wartość null, używany jest wewnętrzny stan konwersji **mbstate_t.** Jeśli znak zawarty w *wchar* nie ma odpowiedniego znaku wielobajtowego, wartość *pReturnValue* będzie -1, a funkcja zwróci wartość **errno** **EILSEQ**.

Funkcja **wcrtomb_s** różni się od [wctomb_s, _wctomb_s_l](wctomb-s-wctomb-s-l.md) możliwością ponownego uruchomienia. Stan konwersji jest przechowywany w *mbstate* dla kolejnych wywołań do tej samej lub innych funkcji, które można ponownie uruchomić. Wyniki są niezdefiniowane podczas mieszania użycia funkcji, które można ponownie uruchomić i niepodważalne. Na przykład aplikacja będzie używać **wcsrlen** zamiast **wcslen**, jeśli kolejne wywołanie **wcsrtombs_s** zostały użyte zamiast **wcstombs_s**.

W języku C++ użycie tej funkcji jest uproszczone przez przeciążenia szablonu; przeciążenia można wywnioskować długość buforu automatycznie (eliminując konieczność określenia argumentu rozmiaru) i mogą automatycznie zastąpić starsze, niezabezpieczone funkcje z ich nowszych, bezpiecznych odpowiedników. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="exceptions"></a>Wyjątki

Funkcja **wcrtomb_s** jest bezpieczna wielowątkowej czynności, o ile żadna funkcja w bieżącym wątku wywołuje **setlocale** podczas wykonywania tej funkcji, a *mbstate* ma wartość null.

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
|**wcrtomb_s**|\<wchar.h>|

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
