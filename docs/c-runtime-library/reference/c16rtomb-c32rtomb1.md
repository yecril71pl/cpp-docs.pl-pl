---
title: c16rtomb, c32rtomb
ms.date: 10/22/2019
api_name:
- c16rtomb
- c32rtomb
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
- c16rtomb
- c32rtomb
- uchar/c16rtomb
- uchar/c32rtomb
helpviewer_keywords:
- c16rtomb function
- c32rtomb function
ms.assetid: 7f5743ca-a90e-4e3f-a310-c73e16f4e14d
ms.openlocfilehash: 8f480d9b450b528275fea78ae878269fa6a4fa54
ms.sourcegitcommit: 0a5518fdb9d87fcc326a8507ac755936285fcb94
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2019
ms.locfileid: "72811063"
---
# <a name="c16rtomb-c32rtomb"></a>c16rtomb, c32rtomb

Przekonwertuj znak dwubajtowy UTF-16 lub UTF-32 na znak wielowymiarowy UTF-8.

## <a name="syntax"></a>Składnia

```C
size_t c16rtomb(
    char *mbchar,
    char16_t wchar,
    mbstate_t *state
);
size_t c32rtomb(
    char *mbchar,
    char32_t wchar,
    mbstate_t *state
);
```

### <a name="parameters"></a>Parametry

*mbchar*\
Wskaźnik na tablicę do przechowywania przekonwertowanego znaku wielobajtowego UTF-8.

*wchar*\
Znak dwubajtowy do przekonwertowania.

\ *stanu*
Wskaźnik do obiektu **mbstate_t** .

## <a name="return-value"></a>Wartość zwracana

Liczba bajtów przechowywanych w obiekcie array *mbchar*, łącznie z dowolnymi sekwencjami przesunięcia. Jeśli *WCHAR* nie jest prawidłowym znakiem dwubajtowym, zwracana jest wartość (**size_t**) (-1), **errno** jest ustawiona na **EILSEQ**, a wartość *State* jest nieokreślona.

## <a name="remarks"></a>Uwagi

Funkcja **c16rtomb** KONWERTUJE znak UTF-16 Le *WCHAR* na równoważną sekwencję wielobajtową kodowania UTF-8. Jeśli *mbchar* nie jest pustym wskaźnikiem, funkcja przechowuje przekonwertowaną sekwencję w obiekcie array wskazywanym przez *mbchar*. Do **MB_CUR_MAX** bajty są przechowywane w *mbchar*, a *stan* jest ustawiony na wynikający z nich stan zmiany wielobajtowego.

Jeśli *WCHAR* jest znakiem dwubajtowym, sekwencja wymagana do przywrócenia stanu początkowej zmiany jest przechowywana, w razie potrzeby, po którym następuje znak null. *stan* jest ustawiony na początkowy stan konwersji. Funkcja **c32rtomb** jest taka sama, ale KONWERTUJE znak UTF-32.

Jeśli *mbchar* jest wskaźnikiem typu null, zachowanie jest równoważne wywołaniu funkcji, która zastępuje bufor wewnętrzny dla *mbchar* i o szerokim znaku null dla *WCHAR*.

Obiekt stanu konwersji *stanu* umożliwia wykonywanie kolejnych wywołań tej funkcji i innych funkcji, które są uruchamiane ponownie, które utrzymują stan przesunięcia znaków danych wyjściowych wielobajtowych. Wyniki są niezdefiniowane w przypadku korzystania z funkcji ponownego uruchamiania i nieuruchomionych ponownie.

Aby skonwertować znaki UTF-16 na znaki wielobajtowe inne niż UTF-8, użyj funkcji [wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md), [wcstombs_s lub _wcstombs_s_l](wcstombs-s-wcstombs-s-l.md) .

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**c16rtomb**, **c32rtomb**|C, C++:\<uchar. h >|

Aby uzyskać informacje o zgodności, zobacz [zgodność](../compatibility.md).

## <a name="see-also"></a>Zobacz także

\ [konwersji danych](../data-conversion.md)
\ [ustawień regionalnych](../locale.md)
[Interpretacja sekwencji znaków wielobajtowych](../interpretation-of-multibyte-character-sequences.md)\
[mbrtoc16, mbrtoc32](mbrtoc16-mbrtoc323.md)\
[wcrtomb](wcrtomb.md)\
[wcrtomb_s](wcrtomb-s.md)
