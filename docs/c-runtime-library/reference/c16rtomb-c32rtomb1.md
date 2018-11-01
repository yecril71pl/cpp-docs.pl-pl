---
title: c16rtomb, c32rtomb1
ms.date: 11/04/2016
apiname:
- c16rtomb
- c32rtomb
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- c16rtomb
- c32rtomb
- uchar/c16rtomb
- uchar/c32rtomb
helpviewer_keywords:
- c16rtomb function
- c32rtomb function
ms.assetid: 7f5743ca-a90e-4e3f-a310-c73e16f4e14d
ms.openlocfilehash: 0d735363bbb317b06c1ebc73a2b0678479a243ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536594"
---
# <a name="c16rtomb-c32rtomb"></a>c16rtomb, c32rtomb

Konwertuj UTF-16 lub UTF-32 znaków dwubajtowych znaków wielobajtowych przy bieżących ustawieniach regionalnych.

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
Wskaźnik do tablicy do przechowywania wielobajtowy znak przekonwertowany.

*WChar*<br/>
Szeroki znak do przekształcenia.

*state*<br/>
Wskaźnik do **mbstate_t** obiektu.

## <a name="return-value"></a>Wartość zwracana

Liczbę bajtów przechowywanych w tablicy obiektów *mbchar*, włączając wszelkie sekwencje shift. Jeśli *wchar* nie jest prawidłową znakiem dwubajtowym, wartość (**size_t**)(-1) zostaną zwrócone, **errno** jest ustawiona na **EILSEQ**, a wartość *stanu* jest nieokreślona.

## <a name="remarks"></a>Uwagi

**C16rtomb** funkcja konwertuje znak UTF-16 *wchar* sekwencji równoważne wielobajtowym wąskie przy bieżących ustawieniach regionalnych. Jeśli *mbchar* nie jest wskaźnikiem typu null, magazyny funkcja przekonwertowanego sekwencję w obiekt array wskazywany przez *mbchar*. Maksymalnie **MB_CUR_MAX** bajtów są przechowywane w *mbchar*, i *stanu* jest ustawiona na Wynikowy stan wielobajtowych shift.    Jeśli *wchar* jest null znakiem dwubajtowym, wymagane do sekwencji przywracania stanu początkowego przesunięcia są przechowywane, jeśli to konieczne, następuje znak null i *stanu* jest ustawiony do stanu początkowego konwersji. **C32rtomb** funkcji są identyczne, ale konwertuje znaków UTF-32.

Jeśli *mbchar* jest pustym wskaźnikiem, zachowanie jest odpowiednikiem wywołania funkcji, która zastępuje buforu wewnętrznego dla *mbchar* oraz szerokiego znaku null dla *wchar*.

*Stanu* konwersji stan obiektu pozwala na utworzenie kolejnych wywołań tej funkcji i innych funkcji ponownego uruchamiania, które obsługi stanu shift znaków wielobajtowych danych wyjściowych. Wyniki są niezdefiniowane podczas jednoczesnego korzystania z funkcji ponownego uruchamiania i bez ponownego uruchamiania, czy wywołanie **setlocale** składa się między wywołaniami funkcji ponownego uruchamiania.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**c16rtomb**, **c32rtomb**|C, C++: \<uchar.h >|

Aby uzyskać informacje o zgodności – zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtoc16, mbrtoc32](mbrtoc16-mbrtoc323.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
