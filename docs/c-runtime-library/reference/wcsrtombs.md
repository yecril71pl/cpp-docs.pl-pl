---
title: wcsrtombs
ms.date: 4/2/2020
api_name:
- wcsrtombs
- _o_wcsrtombs
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
- wcsrtombs
helpviewer_keywords:
- wcsrtombs function
- string conversion, wide characters
- wide characters, strings
ms.assetid: a8d21fec-0d36-4085-9d81-9b1c61c7259d
ms.openlocfilehash: af22a7d55c5f4958db6962e98f212fb5bb89e61e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328060"
---
# <a name="wcsrtombs"></a>wcsrtombs

Konwertuj szeroki ciąg znaków na jego wielobajtową reprezentację ciągu znaków. Dostępna jest bezpieczniejsza wersja tej funkcji; patrz [wcsrtombs_s](wcsrtombs-s.md).

## <a name="syntax"></a>Składnia

```C
size_t wcsrtombs(
   char *mbstr,
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
size_t wcsrtombs(
   char (&mbstr)[size],
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parametry

*mbstr*<br/>
Wynikowa przekonwertowana lokalizacja adresu ciągu znaków wielobajtowych.

*wcstr*<br/>
Pośrednio wskazuje położenie szerokiego ciągu znaków, który ma zostać przekonwertowany.

*Liczba*<br/>
Liczba znaków do przekonwertowania.

*mbstate*<br/>
Wskaźnik do obiektu stanu konwersji **mbstate_t.**

## <a name="return-value"></a>Wartość zwracana

Zwraca liczbę bajtów pomyślnie przekonwertowanych, z wyłączeniem zerowego zakończenia bajtu zerowego (jeśli istnieje), w przeciwnym razie -1, jeśli wystąpił błąd.

## <a name="remarks"></a>Uwagi

Funkcja **wcsrtombs** konwertuje ciąg szerokich znaków, począwszy od określonego stanu konwersji zawartego w *mbstate*, z wartości pośrednich wskazanych w *wcstr*, na adres *mbstr*. Konwersja będzie kontynuowana dla każdego znaku, dopóki nie zostanie napotkany znak o zerowym zakończeniu, po napotkaniu niezdyskliżernego znaku lub gdy następny znak przekroczy limit zawarty w *count*. Jeśli **wcsrtombs** napotka znak null o szerokim znaku (L'\0") przed lub po wystąpieniu *licznika,* konwertuje go na 8-bitowy 0 i zatrzymuje.

W związku z tym ciąg znaków wielobajtowych w *mbstr* jest zakończony zerem tylko wtedy, **gdy wcsrtombs** napotka szeroki znak null znak podczas konwersji. Jeśli sekwencje wskazane przez *wcstr* i *mbstr* nakładają się, zachowanie **wcsrtombs** jest niezdefiniowana. **wcsrtombs** ma wpływ na kategorię LC_TYPE bieżących ustawień regionalnych.

Funkcja **wcsrtombs** różni się od [wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md) przez jego możliwości ponownego uruchomienia. Stan konwersji jest przechowywany w *mbstate* dla kolejnych wywołań do tej samej lub innych funkcji, które można ponownie uruchomić. Wyniki są niezdefiniowane podczas mieszania użycia funkcji, które można ponownie uruchomić i niepodważalne.  Na przykład aplikacja będzie używać **wcsrlen** zamiast **wcsnlen**, jeśli kolejne wywołanie **wcsrtombs** zostały użyte zamiast **wcstombs**.

Jeśli argument *mbstr* ma **wartość NULL**, **wcsrtombs** zwraca wymagany rozmiar w bajtach ciągu docelowego. Jeśli *mbstate* ma wartość null, używany jest wewnętrzny stan konwersji **mbstate_t.** Jeśli sekwencja znaków *wchar* nie ma odpowiedniej reprezentacji znaków wielobajtowych, zwracana jest liczba -1, a **errno** jest ustawione na **EILSEQ**.

W języku C++ ta funkcja ma przeciążenie szablonu, który wywołuje nowszy, bezpieczny odpowiednik tej funkcji. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="exceptions"></a>Wyjątki

Funkcja **wcsrtombs** jest wielowątkowa, o ile żadna funkcja w bieżącym wątku wywołuje **setlocale** podczas wykonywania tej funkcji, a *mbstate* nie jest null.

## <a name="example"></a>Przykład

```cpp
// crt_wcsrtombs.cpp
// compile with: /W3
// This code example converts a wide
// character string into a multibyte
// character string.

#include <stdio.h>
#include <memory.h>
#include <wchar.h>
#include <errno.h>

#define MB_BUFFER_SIZE 100

int main()
{
    const wchar_t   wcString[] =
                    {L"Every good boy does fine."};
    const wchar_t   *wcsIndirectString = wcString;
    char            mbString[MB_BUFFER_SIZE];
    size_t          countConverted;
    mbstate_t       mbstate;

    // Reset to initial shift state
    ::memset((void*)&mbstate, 0, sizeof(mbstate));

    countConverted = wcsrtombs(mbString, &wcsIndirectString,
                               MB_BUFFER_SIZE, &mbstate); // C4996
    // Note: wcsrtombs is deprecated; consider using wcsrtombs_s
    if (errno == EILSEQ)
    {
        printf( "An encoding error was detected in the string.\n" );
    }
    else
    {
        printf( "The string was successfuly converted.\n" );
    }
}
```

```Output
The string was successfuly converted.
```

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**wcsrtombs**|\<wchar.h>|

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
