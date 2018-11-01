---
title: mbrtoc16, mbrtoc323
ms.date: 11/04/2016
apiname:
- mbrtoc16
- mbrtoc32
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
- mbrtoc16
- mbrtoc32
- uchar/mbrtoc16
- uchar/mbrtoc32
helpviewer_keywords:
- mbrtoc16 function
- mbrtoc32 function
ms.assetid: 099ade4d-56f7-4e61-8b45-493f1d7a64bd
ms.openlocfilehash: 7c1683bad8d015071eb2267283630e2f61995fb9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534631"
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16, mbrtoc32

Wykonuje translację pierwszy znak wielobajtowy z ciągu wąskiego na odpowiadające znaki UTF-16 lub UTF-32.

## <a name="syntax"></a>Składnia

```C
size_t mbrtoc16(
   char16_t* destination,
   const char* source,
   size_t max_bytes,
   mbstate_t* state
);

size_t mbrtoc32(
   char32_t* destination,
   const char* source,
   size_t max_bytes,
   mbstate_t* state
);

```

### <a name="parameters"></a>Parametry

*miejsce docelowe*<br/>
Wskaźnik do **char16_t** lub **char32_t** równoważne znaków wielobajtowych do przekonwertowania. Jeśli ma wartość null, funkcja przechowuje wartość.

*source*<br/>
Wskaźnik do ciągu znaków wielobajtowych do przekonwertowania.

*max_bytes*<br/>
Maksymalna liczba bajtów w *źródła* zbadanie znaku do konwersji. Powinna to być wartość z zakresu od jednego liczbę bajtów, łącznie z dowolnego z terminatorem null, w pozostałych *źródła*.

*state*<br/>
Wskaźnik do **mbstate_t** konwersji stan obiektu używaną do interpretacji parametru wielobajtowy ciąg do jednego lub więcej znaków danych wyjściowych.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia, zwraca wartość pierwszego z tych warunków, które ma zastosowanie przy obecnym *stanu* wartość:

|Wartość|Warunek|
|-----------|---------------|
|0|Następne *max_bytes* lub mniej znaków przekonwertowana z *źródła* odnoszą się do wartości null znak dwubajtowy wartość jest przechowywana w przypadku *docelowy* nie ma wartości null.<br /><br /> *Stan* zawiera stan przesunięcia początkowego.|
|Między 1 a *max_bytes*włącznie|Wartość zwracana jest liczba bajtów *źródła* , wykonaj prawidłowym znakiem wielobajtowym. Przekonwertowany znak dwubajtowy jest zapisywana, jeśli *docelowy* nie ma wartości null.|
|-3|Następnego znaku dwubajtowego, wynikające z poprzedniego wywołania do funkcji zostały zapisane w *docelowy* Jeśli *docelowy* nie ma wartości null. Brak bajtów z *źródła* są używane przez to wywołanie do funkcji.<br /><br /> Gdy *źródła* wskazuje znak wielobajtowy, który wymaga więcej niż jeden znak dwubajtowy, aby przedstawić (na przykład Para dwuskładnikowa), a następnie *stanu* wartość jest aktualizowana, aby następnym wywołaniu funkcji zapisuje  limit dodatkowego znaku.|
|-2|Następne *max_bytes* bajty reprezentują ukończona, ale potencjalnie prawidłowy, wielobajtowych znaków. Wartość nie jest przechowywany w *docelowy*. W tym może wystąpić, jeśli *max_bytes* wynosi zero.|
|-1|Wystąpił błąd kodowania. Następne *max_bytes* lub mniejszej liczby bajtów nie przyczyniają się do kompletne i prawidłowy znak wielobajtowy. Wartość nie jest przechowywany w *docelowy*.<br /><br /> **EILSEQ** są przechowywane w **errno** i stan konwersji *stanu* jest nieokreślona.|

## <a name="remarks"></a>Uwagi

**Mbrtoc16** funkcja odczytuje maksymalnie *max_bytes* bajtów z *źródła* można znaleźć pierwszego znaku wielobajtowego pełną, prawidłową, a następnie zapisuje równoważne UTF-16 znak w *docelowy*. Bajty źródła są interpretowane zgodnie z bieżącym wielobajtowych ustawienia regionalne wątku. Jeśli znak wielobajtowy wymaga więcej niż jeden znak dane wyjściowe UTF-16, takie jak para zastępcza, a następnie *stanu* ma wartość następnego znaku UTF-16 w przechowywania *docelowy* w następnym wywołaniu **mbrtoc16**. **Mbrtoc32** funkcji są identyczne, ale dane wyjściowe są przechowywane w postaci znaku UTF-32.

Jeśli *źródła* ma wartość null, te funkcje, które są zwracane wielokrotność połączenie zostało nawiązane przy użyciu argumentów **NULL** dla *docelowy*, **""** dla *źródła*i 1 dla *max_bytes*. Przekazany wartości *docelowy* i *max_bytes* są ignorowane.

Jeśli *źródła* jest inna niż null, funkcja rozpoczyna się od początku ciągu i sprawdza maksymalnie *max_bytes* bajtów w celu określenia liczby bajtów wymaganej do wykonania następnego znaku wielobajtowego w tym wszystkie sekwencje shift. Jeśli zbadane bajtów zawiera znak wielobajtowy prawidłowe i kompletne, funkcja konwertuje znak na równoważne 16-bitowe czy 32-bitowe szeroki znak lub znaki. Jeśli *docelowy* jest nie jest to null, magazyny funkcja wynik pierwszą (i prawdopodobnie tylko) znak w miejscu docelowym. Jeśli wymagane są dodatkowe dane wyjściowe znaki, wartość jest ustawiana w *stanu*, dzięki czemu kolejnych wywołań funkcji wyjściowych dodatkowe znaki i zwracają wartość -3. Jeśli nie więcej znaków danych wyjściowych są wymagane, następnie *stanu* jest ustawiony do stanu początkowego przesunięcia.

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**mbrtoc16**, **mbrtoc32**|\<uchar.h>|\<cuchar >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[c16rtomb, c32rtomb](c16rtomb-c32rtomb1.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbsrtowcs](mbsrtowcs.md)<br/>
[mbsrtowcs_s](mbsrtowcs-s.md)<br/>
