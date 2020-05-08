---
title: wcsrtombs_s
ms.date: 4/2/2020
api_name:
- wcsrtombs_s
- _o_wcsrtombs_s
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
- wcsrtombs_s
helpviewer_keywords:
- string conversion, wide characters
- wcsrtombs_s function
- wide characters, strings
ms.assetid: 9dccb766-113c-44bb-9b04-07a634dddec8
ms.openlocfilehash: c804d232dbcce67b8d467eaa37ccf2b15282881a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910599"
---
# <a name="wcsrtombs_s"></a>wcsrtombs_s

Przekonwertuj ciąg znaków dwubajtowych na reprezentację w postaci ciągu znaków. Wersja [wcsrtombs](wcsrtombs.md) z ulepszeniami zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t wcsrtombs_s(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
errno_t wcsrtombs_s(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parametry

*pReturnValue*<br/>
Rozmiar w bajtach przekonwertowanego ciągu, łącznie z terminatorem wartości null.

*mbstr*<br/>
Adres buforu dla wyniku konwertowanego ciągu znaków wielobajtowych.

*sizeInBytes*<br/>
Rozmiar w bajtach buforu *mbstr* .

*wcstr*<br/>
Wskazuje ciąg znaków dwubajtowych do przekonwertowania.

*liczbą*<br/>
Maksymalna liczba bajtów, które mają być przechowywane w buforze *mbstr* , lub [_TRUNCATE](../../c-runtime-library/truncate.md).

*mbstate*<br/>
Wskaźnik do obiektu stanu konwersji **mbstate_t** .

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie, kod błędu w przypadku niepowodzenia.

|Błąd|Wartość zwracana i **errno**|
|---------------------|------------------------------|
|*mbstr* ma **wartość NULL** i *sizeInBytes* > 0|**EINVAL**|
|*wcstr* ma **wartość null**|**EINVAL**|
|Bufor docelowy jest zbyt mały, aby zawierał przekonwertowany ciąg (chyba że *licznik* jest **_TRUNCATE**; Zobacz uwagi poniżej)|**ERANGE**|

Jeśli wystąpi którykolwiek z tych warunków, wyjątek nieprawidłowego parametru jest wywoływany zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, funkcja zwraca kod błędu i ustawia **errno** , jak wskazano w tabeli.

## <a name="remarks"></a>Uwagi

Funkcja **wcsrtombs_s** konwertuje ciąg znaków dwubajtowych, do których odnoszą się *wcstr* w postaci znaków wielowartościowych przechowywanych w buforze wskazywanym przez *mbstr*, przy użyciu stanu konwersji zawartego w *mbstate*. Konwersja będzie kontynuowana dla każdego znaku do momentu spełnienia jednego z następujących warunków:

- Napotkano zerowy znak dwubajtowy

- Napotkano znak dwubajtowy, którego nie można przekonwertować

- Liczba bajtów przechowywanych w buforze *mbstr* jest równa *Count*.

Ciąg docelowy jest zawsze zakończony wartością null (nawet w przypadku błędu).

Jeśli *Liczba* jest wartością specjalną [_TRUNCATE](../../c-runtime-library/truncate.md), wówczas **wcsrtombs_s** konwertuje tyle ciągu jako ciąg, jak zmieści się w buforze docelowym, pozostawiając nadal miejsce na terminator o wartości null.

Jeśli **wcsrtombs_s** pomyślnie przekonwertuje ciąg źródłowy, umieści rozmiar w bajtach przekonwertowanego ciągu, łącznie z terminatorem wartości null, na *&#42;PReturnValue* (podany *pReturnValue* nie ma **wartości null**). Dzieje się tak nawet wtedy, gdy argument *mbstr* ma **wartość null** i umożliwia określenie wymaganego rozmiaru buforu. Należy pamiętać, że jeśli *mbstr* ma **wartość null**, *Count* jest ignorowany.

Jeśli **wcsrtombs_s** napotka znak dwubajtowy, nie może on zostać skonwertowany na znak wieloznaczny, umieszcza-1 w * \*pReturnValue*, ustawia bufor docelowy na pusty ciąg, **ustawia errno** na **EILSEQ**i zwraca **EILSEQ**.

Jeśli sekwencje wskazywane przez *wcstr* i *mbstr* nakładają się na siebie, zachowanie **wcsrtombs_s** jest niezdefiniowane. na **wcsrtombs_s** ma wpływ Kategoria LC_TYPE bieżących ustawień regionalnych.

> [!IMPORTANT]
> Upewnij się, że *wcstr* i *mbstr* nie nakładają się na siebie, i że *licznik* poprawnie odzwierciedla liczbę szerokich znaków do przekonwertowania.

Funkcja **wcsrtombs_s** różni się od [wcstombs_s, _wcstombs_s_l](wcstombs-s-wcstombs-s-l.md) od jej uruchomienia. Stan konwersji jest przechowywany w *mbstate* dla kolejnych wywołań do tych samych lub innych funkcji, które można uruchomić ponownie. Wyniki są niezdefiniowane podczas mieszania użycia funkcji ponownego uruchamiania i nieuruchomionych ponownie. Na przykład aplikacja będzie używać **wcsrlen** zamiast **wcslen**, jeśli podczas kolejnego wywołania do **wcsrtombs_s** były używane zamiast **wcstombs_s**.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonów; przeciążenia mogą automatycznie wywnioskować długość buforu (eliminując konieczność określenia argumentu rozmiaru) i mogą automatycznie zastąpić starsze, niezabezpieczone funkcje z ich nowszymi, bezpiecznymi odpowiednikami. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="exceptions"></a>Wyjątki

Funkcja **wcsrtombs_s** jest bezpiecznie wielowątkowej, dopóki żadna funkcja w bieżącym wątku nie wywołuje metody **setlocaling** , podczas gdy ta funkcja jest wykonywana, a *mbstate* ma wartość null.

## <a name="example"></a>Przykład

```cpp
// crt_wcsrtombs_s.cpp
//
// This code example converts a wide
// character string into a multibyte
// character string.
//

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
    errno_t         err;
    mbstate_t       mbstate;

    // Reset to initial shift state
    ::memset((void*)&mbstate, 0, sizeof(mbstate));

    err = wcsrtombs_s(&countConverted, mbString, MB_BUFFER_SIZE,
                      &wcsIndirectString, MB_BUFFER_SIZE, &mbstate);
    if (err == EILSEQ)
    {
        printf( "An encoding error was detected in the string.\n" );
    }
    else
    {
        printf( "The string was successfully converted.\n" );
    }
}
```

```Output
The string was successfully converted.
```

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**wcsrtombs_s**|\<WCHAR. h>|

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Ustawienie](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
