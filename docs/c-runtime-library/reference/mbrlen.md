---
title: mbrlen
ms.date: 11/04/2016
apiname:
- mbrlen
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mbrlen
helpviewer_keywords:
- mbrlen function
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
ms.openlocfilehash: ec9079b9b164e2b609a956ddf3a75cd42923bafc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156775"
---
# <a name="mbrlen"></a>mbrlen

Określ liczbę bajtów, które są wymagane do ukończenia znaków wielobajtowych przy bieżących ustawieniach regionalnych z możliwością ponownego uruchomienia w środku znaków wielobajtowych.

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
Wskaźnik na następny bajt, aby sprawdzić w ciągu znaków wielobajtowych.

*Liczba*<br/>
Maksymalna liczba bajtów do wglądu.

*mbstate*<br/>
Wskaźnik do bieżącego stanu shift bajt początkowy *str*.

## <a name="return-value"></a>Wartość zwracana

Jeden z następujących wartości:

|||
|-|-|
0|Następne *liczba* lub mniejsza liczba bajtów zakończą się znak wielobajtowy, który reprezentuje znak dwubajtowy o wartości null.
1, aby *liczba*włącznie|Następne *liczba* lub mniejsza liczba bajtów Zakończ prawidłowym znakiem wielobajtowym. Wartość zwracana jest liczba bajtów, kończące znaki wielobajtowe.
(size_t)(-2)|Następne *liczba* bajtów Współtworzenie niekompletne, ale potencjalnie prawidłowy znak wielobajtowy i wszystkie *liczba* bajty zostały przetworzone.
(size_t)(-1)|Wystąpił błąd kodowania. Następne *liczba* lub mniejszej liczby bajtów nie przyczyniają się do kompletne i prawidłowy znak wielobajtowy. W tym przypadku **errno** jest ustawiona na EILSEQ i stan konwersji, w *mbstate* jest nieokreślona.

## <a name="remarks"></a>Uwagi

**Mbrlen —** funkcja sprawdza co najwyżej *liczba* bajty począwszy od bajt wskazywany przez *str* do określenia liczby bajtów, które są wymagane do wykonania następnego znak wielobajtowy, w tym wszelkie sekwencje shift. Jest to równoważne wywołanie `mbrtowc(NULL, str, count, &mbstate)` gdzie *mbstate* jest albo dostarczonych przez użytkownika **mbstate_t** albo statyczny obiekt wewnętrzny, dostarczone przez bibliotekę.

**Mbrlen —** funkcji zapisuje i używa stanu shift niekompletne znaku wielobajtowego w *mbstate* parametru. Dzięki temu **mbrlen —** możliwości ponownego uruchamiania środku znak wielobajtowy, jeśli muszą być co najwyżej badanie *liczba* bajtów. Jeśli *mbstate* jest pustym wskaźnikiem, **mbrlen —** używa wewnętrznych statyczne **mbstate_t** obiekt ma być przechowywany stan shift. Ponieważ wewnętrzny **mbstate_t** obiekt nie jest metodą o bezpiecznych wątkach, zalecamy zawsze przydzielić i przekazania własnych *mbstate* parametru.

**Mbrlen —** funkcja różni się od [_mbclen —, mblen —, _mblen_l —](mbclen-mblen-mblen-l.md) przez jego restartability. Stan shift jest przechowywany w *mbstate* dla kolejnych wywołań tej samej lub innych funkcji ponownego uruchamiania. Podczas korzystania z funkcji ponownego uruchamiania i nonrestartable mieszania, wyniki są niezdefiniowane.  Na przykład, aplikacja powinna używać **wcsrlen** zamiast **wcslen —** Jeśli kolejne wywołanie **wcsrtombs —** jest używana zamiast **wcstombs —**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|Nie dotyczy|Nie dotyczy|**mbrlen**|Nie dotyczy|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**mbrlen**|\<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Ten przykład przedstawia sposób interpretacji znaków wielobajtowych zależy od bieżącej stronie kodowej i pokazuje możliwości wznawianie **mbrlen —**.

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
