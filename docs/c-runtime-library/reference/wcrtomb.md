---
title: wcrtomb
ms.date: 11/04/2016
api_name:
- wcrtomb
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
ms.openlocfilehash: 8d2108b90f6884113f0bd974bf7aa634544adf5f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945219"
---
# <a name="wcrtomb"></a>wcrtomb

Konwertuj znak dwubajtowy na swoją reprezentację znaku wieloznacznego. Dostępna jest bezpieczniejsza wersja tej funkcji; Zobacz [wcrtomb_s](wcrtomb-s.md).

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
Wynikiem konwersji wielobajtowego znaku.

*WCHAR*<br/>
Znak dwubajtowy do przekonwertowania.

*mbstate*<br/>
Wskaźnik do obiektu **mbstate_t** .

## <a name="return-value"></a>Wartość zwracana

Zwraca liczbę bajtów wymaganą do reprezentowania przekonwertowanego znaku wielobajtowego. w przeciwnym razie-1, jeśli wystąpi błąd.

## <a name="remarks"></a>Uwagi

Funkcja **wcrtomb** konwertuje znak dwubajtowy, zaczynając od określonego stanu konwersji zawartego w *mbstate*, z wartości zawartej w *WCHAR*, do adresu reprezentowanego przez *mbchar*. Wartość zwracana to liczba bajtów wymagana do reprezentowania odpowiedniego znaku wielobajtowego, ale nie zwróci więcej niż **MB_CUR_MAX** bajtów.

Jeśli *mbstate* ma wartość null, używany jest wewnętrzny obiekt **mbstate_t** zawierający Stan konwersji *mbchar* . Jeśli *WCHAR* sekwencji znaków nie ma odpowiadającej reprezentacji znaków wielobajtowych, zwracana jest wartość-1, a **errno** jest ustawiona na **EILSEQ**.

Funkcja **wcrtomb** różni się od [wctomb, _wctomb_l,](wctomb-wctomb-l.md) dzięki czemu można jej uruchomić. Stan konwersji jest przechowywany w *mbstate* dla kolejnych wywołań do tych samych lub innych funkcji, które można uruchomić ponownie. Wyniki są niezdefiniowane podczas mieszania użycia funkcji ponownego uruchamiania i nieuruchomionych ponownie. Na przykład aplikacja będzie używać **wcsrlen** zamiast **wcsnlen**, jeśli zamiast **wcstombs**użyto kolejnego wywołania **wcsrtombs** .

W C++programie ta funkcja ma Przeciążenie szablonu, które wywołuje nowsze i bezpieczne odpowiedniki tej funkcji. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Wyjątki

Funkcja **wcrtomb** jest wielowątkowej bezpiecznie, o ile funkcja w bieżącym wątku nie wywołuje metody **setlocaling** , podczas gdy ta funkcja jest wykonywana, a *mbstate* ma wartość null.

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
|**wcrtomb**|\<WCHAR. h >|

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
