---
title: wcrtomb
ms.date: 4/2/2020
api_name:
- wcrtomb
- _o_wcrtomb
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
- wcrtomb
helpviewer_keywords:
- wide characters, converting
- wcrtomb function
- multibyte characters
- characters, converting
ms.assetid: 717f1b21-2705-4b7f-b6d0-82adc5224340
ms.openlocfilehash: eda857b80404aebe46b090741e0b56d4fe692f34
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328094"
---
# <a name="wcrtomb"></a>wcrtomb

Konwertuj szeroki znak na jego wielobajtową reprezentację znaków. Dostępna jest bezpieczniejsza wersja tej funkcji; patrz [wcrtomb_s](wcrtomb-s.md).

## <a name="syntax"></a>Składnia

```C
size_t wcrtomb(
   char *mbchar,
   wchar_t wchar,
   mbstate_t *mbstate
);
template <size_t size>
size_t wcrtomb(
   char (&mbchar)[size],
   wchar_t wchar,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parametry

*mbchar*<br/>
Wynikowy znak przekonwertowany wielobajtowy.

*Wchar*<br/>
Szeroki znak do konwersji.

*mbstate*<br/>
Wskaźnik do **obiektu mbstate_t.**

## <a name="return-value"></a>Wartość zwracana

Zwraca liczbę bajtów wymaganych do reprezentowania przekonwertowanego znaku wielobajtowego, w przeciwnym razie -1, jeśli wystąpi błąd.

## <a name="remarks"></a>Uwagi

Funkcja **wcrtomb** konwertuje szeroki znak, zaczynając od określonego stanu konwersji zawartego w *mbstate*, z wartości zawartej w *wchar,* na adres reprezentowany przez *mbchar*. Zwracana wartość jest liczbą bajtów wymaganych do reprezentowania odpowiedniego znaku wielobajtowego, ale nie zwróci więcej niż **MB_CUR_MAX** bajtów.

Jeśli *mbstate* ma wartość null, używany jest wewnętrzny **obiekt mbstate_t** zawierający stan konwersji *mbchar.* Jeśli sekwencja znaków *wchar* nie ma odpowiedniej reprezentacji znaków wielobajtowych, zwracana jest liczba -1, a **errno** jest ustawione na **EILSEQ**.

Funkcja **wcrtomb** różni się od [wctomb, _wctomb_l](wctomb-wctomb-l.md) przez jego możliwości ponownego uruchomienia. Stan konwersji jest przechowywany w *mbstate* dla kolejnych wywołań do tej samej lub innych funkcji, które można ponownie uruchomić. Wyniki są niezdefiniowane podczas mieszania użycia funkcji, które można ponownie uruchomić i niepodważalne. Na przykład aplikacja będzie używać **wcsrlen** zamiast **wcsnlen**, jeśli kolejne wywołanie **wcsrtombs** zostały użyte zamiast **wcstombs**.

W języku C++ ta funkcja ma przeciążenie szablonu, który wywołuje nowsze, bezpieczne odpowiedniki tej funkcji. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="exceptions"></a>Wyjątki

Funkcja **wcrtomb** jest wielowątkowa, o ile żadna funkcja w bieżącym wątku wywołuje **setlocale** podczas wykonywania tej funkcji i gdy *mbstate* ma wartość null.

## <a name="example"></a>Przykład

```C
// crt_wcrtomb.c
// compile with: /W3
// This program converts a wide character
// to its corresponding multibyte character.

#include <string.h>
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    size_t      sizeOfCovertion = 0;
    mbstate_t   mbstate;
    char        mbStr = 0;
    wchar_t*    wcStr = L"Q";

    // Reset to initial conversion state
    memset(&mbstate, 0, sizeof(mbstate));

    sizeOfCovertion = wcrtomb(&mbStr, *wcStr, &mbstate); // C4996
    // Note: wcrtomb is deprecated; consider using wcrtomb_s instead
    if (sizeOfCovertion > 0)
    {
        printf("The corresponding wide character \"");
        wprintf(L"%s\"", wcStr);
        printf(" was converted to the \"%c\" ", mbStr);
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
The corresponding wide character "Q" was converted to the "Q" multibyte character.
```

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**wcrtomb**|\<wchar.h>|

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
