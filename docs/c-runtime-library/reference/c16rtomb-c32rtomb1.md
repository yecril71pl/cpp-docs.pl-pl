---
title: c16rtomb, c32rtomb
ms.date: 01/22/2018
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
ms.openlocfilehash: a16effe48442ccbb5144b57ead2fb15c908fe898
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943430"
---
# <a name="c16rtomb-c32rtomb"></a>c16rtomb, c32rtomb

Przekonwertuj znak dwubajtowy UTF-16 lub UTF-32 na znak wieloznaczny w bieżącym ustawieniach regionalnych.

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

*mbchar*<br/>
Wskaźnik do tablicy w celu zapisania znaku wielobajtowego.

*WCHAR*<br/>
Znak dwubajtowy do przekonwertowania.

*state*<br/>
Wskaźnik do obiektu **mbstate_t** .

## <a name="return-value"></a>Wartość zwracana

Liczba bajtów przechowywanych w obiekcie array *mbchar*, łącznie z dowolnymi sekwencjami przesunięcia. Jeśli *WCHAR* nie jest prawidłowym znakiem dwubajtowym, zwracana jest wartość (**size_t**) (-1), **errno** jest ustawiona na **EILSEQ**, a wartość *stanu* jest nieokreślona.

## <a name="remarks"></a>Uwagi

Funkcja **c16rtomb** KONWERTUJE znak UTF-16 *WCHAR* na równoważną sekwencję znaków wielobajtowych w bieżącym ustawieniach regionalnych. Jeśli *mbchar* nie jest pustym wskaźnikiem, funkcja przechowuje przekonwertowaną sekwencję w obiekcie array wskazywanym przez *mbchar*. Do **MB_CUR_MAX** bajty są przechowywane w *mbchar*, a *stan* jest ustawiony na wynikający z nich stan zmiany wielobajtowego.    Jeśli *WCHAR* jest znakiem dwubajtowym, sekwencja wymagana do przywrócenia stanu początkowej zmiany jest przechowywana, w razie potrzeby, po którym następuje znak null, a *stan* jest ustawiony na początkowy stan konwersji. Funkcja **c32rtomb** jest taka sama, ale KONWERTUJE znak UTF-32.

Jeśli *mbchar* jest wskaźnikiem typu null, zachowanie jest równoważne wywołaniu funkcji, która zastępuje bufor wewnętrzny dla *mbchar* i o szerokim znaku null dla *WCHAR*.

Obiekt stanu konwersji *stanu* umożliwia wykonywanie kolejnych wywołań tej funkcji i innych funkcji, które są uruchamiane ponownie, które utrzymują stan przesunięcia znaków danych wyjściowych wielobajtowych. Wyniki są niezdefiniowane w przypadku używania funkcji ponownego uruchamiania i nie uruchamianych ponownie lub jeśli wywołanie metody **setlocaling** jest nawiązywane między wywołaniami funkcji, które można uruchomić ponownie.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**c16rtomb**, **c32rtomb**|C, C++: \<uchar.h>|

Aby uzyskać informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtoc16, mbrtoc32](mbrtoc16-mbrtoc323.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
