---
title: mbrlen
ms.date: 11/04/2016
api_name:
- mbrlen
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbrlen
helpviewer_keywords:
- mbrlen function
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
ms.openlocfilehash: c9559731f39db35e03f640bb30b9af3fff00cf66
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952507"
---
# <a name="mbrlen"></a>mbrlen

Określ liczbę bajtów, które są wymagane do ukończenia znaku wielobajtowego w bieżących ustawieniach regionalnych, z możliwością ponownego uruchomienia w środku znaku wielobajtowego.

## <a name="syntax"></a>Składnia

```C
size_t mbrlen(
   const char * str,
   size_t count,
   mbstate_t * mbstate
);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Wskaźnik do następnego bajtu do sprawdzenia w ciągu znaków wielobajtowych.

*liczbą*<br/>
Maksymalna liczba bajtów do sprawdzenia.

*mbstate*<br/>
Wskaźnik do bieżącego stanu przesunięcia początkowego bajtu *str*.

## <a name="return-value"></a>Wartość zwracana

Jedna z następujących wartości:

|||
|-|-|
0|Kolejna *Liczba* lub mniejsza liczba bajtów Ukończ znak wielobajtowy, który reprezentuje szeroki znak null.
1 do *zliczenia*włącznie|Kolejna *Liczba* lub mniejsza liczba bajtów ukończą prawidłowy znak wielobajtowy. Zwracana wartość to liczba bajtów zakończonych znakiem wielobajtowym.
(size_t)(-2)|Kolejna *Liczba* bajtów przyczynia się do niekompletnego, ale potencjalnie prawidłowego znaku wielobajtowego i wszystkie bajty *licznika* zostały przetworzone.
(size_t)(-1)|Wystąpił błąd kodowania. Kolejna lub mniejsza *Liczba* bajtów nie przyczyniają się do pełnego i prawidłowego znaku wielobajtowego. W tym przypadku **errno** jest ustawiony na EILSEQ i stan konwersji w *mbstate* jest nieokreślony.

## <a name="remarks"></a>Uwagi

Funkcja **mbrlen** sprawdza z największą liczbą bajtów rozpoczynającą się od bajtu wskazywanym przez *str* , aby określić *liczbę bajtów,* które są wymagane do ukończenia następnego znaku wielobajtowego, w tym wszystkie sekwencje przesunięcia. Jest równoważne wywołaniu `mbrtowc(NULL, str, count, &mbstate)` , gdzie *mbstate* jest obiektem **mbstate_t** udostępnionym przez użytkownika lub statycznym obiektem wewnętrznym dostarczonym przez bibliotekę.

Funkcja **mbrlen** zapisuje i używa stanu przesunięcia niekompletnego znaku wielobajtowego w parametrze *mbstate* . Dzięki temu **mbrlen** możliwość ponownego uruchomienia w środku znaku wielobajtowego, jeśli jest to konieczne, badanie z największą *liczbą* bajtów. Jeśli *mbstate* jest wskaźnikiem typu null, **mbrlen** używa wewnętrznego, statycznego obiektu **mbstate_t** do przechowywania stanu przesunięcia. Ponieważ wewnętrzny obiekt **mbstate_t** nie jest bezpieczny wątkowo, zalecamy, aby zawsze przydzielić i przekazać własny parametr *mbstate* .

Funkcja **mbrlen** różni się od [_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md) według ich ponownego uruchomienia. Stan przesunięcia jest przechowywany w *mbstate* dla kolejnych wywołań do tych samych lub innych funkcji, które można uruchomić ponownie. Wyniki są niezdefiniowane podczas mieszania użycia funkcji ponownego uruchamiania i nieuruchomionych ponownie.  Na przykład aplikacja powinna używać **wcsrlen** zamiast **wcslen** , jeśli podczas kolejnego wywołania **wcsrtombs** zostanie użyta wartość **wcstombs**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|Nie dotyczy|Nie dotyczy|**mbrlen**|Nie dotyczy|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**mbrlen**|\<WCHAR. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Ten przykład pokazuje, jak interpretacja znaków wielobajtowych zależy od bieżącej strony kodowej i demonstruje możliwości wznawiania **mbrlen**.

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

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
