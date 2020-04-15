---
title: mbrlen
ms.date: 4/2/2020
api_name:
- mbrlen
- _o_mbrlen
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbrlen
helpviewer_keywords:
- mbrlen function
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
ms.openlocfilehash: 7503de22a8310335ddd678335916d3e74dab6e70
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340990"
---
# <a name="mbrlen"></a>mbrlen

Określ liczbę bajtów wymaganych do ukończenia znaku wielobajtowego w bieżących ustawieniach regionalnych, z możliwością ponownego uruchomienia w środku znaku wielobajtowego.

## <a name="syntax"></a>Składnia

```C
size_t mbrlen(
   const char * str,
   size_t count,
   mbstate_t * mbstate
);
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Wskaźnik do następnego bajtu, aby sprawdzić w ciągu znaków wielobajtowych.

*Liczba*<br/>
Maksymalna liczba bajtów do sprawdzenia.

*mbstate*<br/>
Wskaźnik do bieżącego stanu przesunięcia początkowego bajtu *str*.

## <a name="return-value"></a>Wartość zwracana

Jedna z następujących wartości:

|||
|-|-|
0|Następna *liczba* lub mniej bajtów zakończyć znak wielobajtowy, który reprezentuje znak o szerokości null.
1 do *liczenia*, włącznie|Następna *liczba* lub mniej bajtów zakończy prawidłowy znak wielobajtowy. Zwrócona wartość to liczba bajtów, które wypełniają znak wielobajtowy.
(size_t) (-2)|Następna *liczba* bajtów przyczyniają się do niekompletnego, ale potencjalnie prawidłowego znaku wielobajtowego i wszystkie bajty *liczby* zostały przetworzone.
(size_t) (-1)|Wystąpił błąd kodowania. Następna *liczba* lub mniej bajtów nie przyczyniają się do pełnego i prawidłowego znaku wielobajtowego. W takim przypadku **errno** jest ustawiona na EILSEQ i stan konwersji w *mbstate* jest nieokreślony.

## <a name="remarks"></a>Uwagi

Funkcja **mbrlen** sprawdza co najwyżej *liczbę* bajtów, począwszy od bajtu wskazywania przez *str,* aby określić liczbę bajtów wymaganych do ukończenia następnego znaku wielobajtowego, w tym sekwencje przesunięcia. Jest to równoważne `mbrtowc(NULL, str, count, &mbstate)` wywołanie, gdzie *mbstate* jest obiektem **mbstate_t** dostarczonym przez użytkownika lub statycznym obiektem wewnętrznym dostarczonym przez bibliotekę.

Funkcja **mbrlen** zapisuje i używa stanu zmiany niekompletnego znaku wielobajtowego w parametrze *mbstate.* Daje to **mbrlen** możliwość ponownego uruchamiania w środku znaku wielobajtowego w razie potrzeby, badanie co najwyżej *liczba* bajtów. Jeśli *mbstate* jest wskaźnikiem zerowym, **mbrlen** używa wewnętrznego, statycznego **obiektu mbstate_t** do przechowywania stanu zmiany. Ponieważ obiekt **mbstate_t** wewnętrzny nie jest bezpieczny dla wątków, zaleca się zawsze przydzielić i przekazać własny parametr *mbstate.*

Funkcja **mbrlen** różni się od [_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md) przez jego możliwości ponownego uruchomienia. Stan zmiany jest przechowywany w *mbstate* dla kolejnych wywołań do tej samej lub innych funkcji, które można ponownie uruchomić. Wyniki są niezdefiniowane podczas mieszania użycia funkcji, które można ponownie uruchomić i niepodważalne.  Na przykład aplikacja powinna używać **wcsrlen** zamiast **wcslen,** jeśli zamiast **wcstombs**jest używane kolejne wywołanie **wcsrtombs.**

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|nie dotyczy|nie dotyczy|**mbrlen**|nie dotyczy|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**mbrlen**|\<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

W tym przykładzie pokazano, jak interpretacja znaków wielobajtowych zależy od bieżącej strony kodowej i pokazuje możliwość wznowienia **mbrlen**.

```C
// crt_mbrlen.c
// Compile by using: cl crt_mbrlen.c
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <locale.h>
#include <wchar.h>

size_t Example(const char * pStr)
{
    size_t      charLen = 0;
    size_t      charCount = 0;
    mbstate_t   mbState = {0};

    while ((charLen = mbrlen(pStr++, 1, &mbState)) != 0 &&
            charLen != (size_t)-1)
    {
        if (charLen != (size_t)-2) // if complete mbcs char,
        {
            charCount++;
        }
    }
    return (charCount);
}

int main( void )
{
    int         cp;
    size_t      charCount = 0;
    const char  *pSample =
        "\x82\xD0\x82\xE7\x82\xAA\x82\xC8: Shift-jis hiragana.";

    cp = _getmbcp();
    charCount = Example(pSample);
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",
        cp, pSample, charCount);

    setlocale(LC_ALL, "ja-JP"); // Set Japanese locale
    _setmbcp(932); // and Japanese multibyte code page
    cp = _getmbcp();
    charCount = Example(pSample);
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",
        cp, pSample, charCount);
}
```

```Output

Code page: 0
é╨éτé¬é╚: Shift-jis hiragana.
Character count: 29

Code page: 932
????: Shift-jis hiragana.
Character count: 25
```

## <a name="see-also"></a>Zobacz też

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
