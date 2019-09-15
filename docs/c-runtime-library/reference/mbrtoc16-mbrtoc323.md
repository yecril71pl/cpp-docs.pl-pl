---
title: mbrtoc16, mbrtoc323
ms.date: 11/04/2016
api_name:
- mbrtoc16
- mbrtoc32
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
- mbrtoc16
- mbrtoc32
- uchar/mbrtoc16
- uchar/mbrtoc32
helpviewer_keywords:
- mbrtoc16 function
- mbrtoc32 function
ms.assetid: 099ade4d-56f7-4e61-8b45-493f1d7a64bd
ms.openlocfilehash: 52bcec5911fdc2ecbb073ae0042777aa4eb2b963
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952440"
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16, mbrtoc32

Tłumaczy pierwszy znak wielobajtowy w wąskim ciągu na odpowiednik znaku UTF-16 lub UTF-32.

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

*punktu*<br/>
Wskaźnik do **char16_t** lub **char32_t** równoważnego znaku wielobajtowego do przekonwertowania. Jeśli wartość jest równa null, funkcja nie przechowuje wartości.

*source*<br/>
Wskaźnik do ciągu znaków wielobajtowych do przekonwertowania.

*max_bytes*<br/>
Maksymalna liczba bajtów w *źródle* do sprawdzenia dla znaku do przekonwertowania. Powinna to być wartość z zakresu od jednej do liczby bajtów, łącznie z dowolnym terminatorem o wartości null, pozostałą w *źródle*.

*state*<br/>
Wskaźnik do obiektu stanu konwersji **mbstate_t** używany do interpretowania ciągu wielobajtowego do co najmniej jednego znaku wyjściowego.

## <a name="return-value"></a>Wartość zwracana

Po powodzeniu zwraca wartość pierwszego z tych warunków, które mają zastosowanie, z uwzględnieniem bieżącej wartości *stanu* :

|Wartość|Warunek|
|-----------|---------------|
|0|Następne *max_bytes* lub mniej znaków konwertowane ze *źródła* odpowiadają znakom szerokości zerowej, która jest wartością przechowywaną, jeśli *miejsce docelowe* nie ma wartości null.<br /><br /> *stan* zawiera początkowy stan przesunięcia.|
|Od 1 do *max_bytes*włącznie|Zwracana wartość to liczba bajtów *źródła* , które ukończyły prawidłowy znak wielobajtowy. Przekonwertowany znak dwubajtowy jest przechowywany, jeśli *miejsce docelowe* nie ma wartości null.|
|-3|Następny znak dwubajtowy wynikający z poprzedniego wywołania funkcji został zapisany w *miejscu docelowym* , jeśli *miejsce docelowe* nie ma wartości null. Żadne bajty ze *źródła* nie są używane przez to wywołanie funkcji.<br /><br /> Gdy *Źródło* wskazuje znak wielobajtowy, który wymaga więcej niż jednego znaku szerokiego do reprezentowania (na przykład para zastępcza), wartość *stanu* jest aktualizowana, tak aby następne wywołanie funkcji zapisywał dodatkowy znak.|
|-2|Następne *max_bytes* bajty reprezentują niekompletny, ale może być prawidłowym znakiem wielobajtowym. Żadna wartość nie jest przechowywana w *miejscu docelowym*. Ten wynik może wystąpić, jeśli *max_bytes* ma wartość zero.|
|-1|Wystąpił błąd kodowania. Następna *max_bytes* lub mniejsza liczba bajtów nie przyczyniają się do pełnego i prawidłowego znaku wielobajtowego. Żadna wartość nie jest przechowywana w *miejscu docelowym*.<br /><br /> **EILSEQ** jest przechowywany w **errno** i *stan* konwersji jest nieokreślony.|

## <a name="remarks"></a>Uwagi

Funkcja **mbrtoc16** odczytuje do *max_bytes* bajtów ze *źródła* w celu znalezienia pierwszego kompletnego, prawidłowego znaku wielobajtowego, a następnie zapisuje odpowiednik znaku UTF-16 w *miejscu docelowym*. Bajty źródłowe są interpretowane zgodnie z bieżącymi ustawieniami wielobajtowymi wątków. Jeśli znak wielobajtowy wymaga więcej niż jednego znaku wyjściowego UTF-16, takiego jak para zastępcza, wartość *stanu* jest ustawiona do przechowywania następnego znaku UTF-16 w *miejscu docelowym* przy następnym wywołaniu **mbrtoc16**. Funkcja **mbrtoc32** jest taka sama, ale dane wyjściowe są przechowywane jako znaki UTF-32.

Jeśli *Źródło* ma wartość null, te funkcje zwracają odpowiednik wywołania wykonanego przy użyciu argumentów o **wartości null** dla *miejsca docelowego*, **""** dla *źródła*i 1 dla *max_bytes*. Przekazanie wartości *docelowy* i *max_bytes* są ignorowane.

Jeśli *Źródło* nie ma wartości null, funkcja rozpoczyna się na początku ciągu i sprawdza, czy *max_bytes* bajty, aby określić liczbę bajtów potrzebnych do ukończenia następnego znaku wielobajtowego, w tym wszystkie sekwencje przesunięcia. Jeśli badane bajty zawierają prawidłowy i kompletny znak wielobajtowy, funkcja konwertuje znak na równoważny 16-bitowy lub 32-bitowy znak lub znaki. Jeśli *Lokalizacja docelowa* nie jest równa null, funkcja przechowuje pierwszy (i możliwy tylko) znak wyniku w miejscu docelowym. Jeśli wymagane są dodatkowe znaki wyjściowe, wartość jest ustawiona w *stanie*, więc kolejne wywołania funkcji wyprowadzają znaki dodatkowe i zwracają wartość-3. Jeśli nie są wymagane żadne znaki wyjściowe, *stan* jest ustawiany na początkowy stan przesunięcia.

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|C++nagłówki|
|--------------|--------------|------------------|
|**mbrtoc16**, **mbrtoc32**|\<uchar.h>|\<cuchar >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[c16rtomb, c32rtomb](c16rtomb-c32rtomb1.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbsrtowcs](mbsrtowcs.md)<br/>
[mbsrtowcs_s](mbsrtowcs-s.md)<br/>
