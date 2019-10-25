---
title: mbrtoc16, mbrtoc323
ms.date: 10/22/2019
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
ms.openlocfilehash: 793eadf433f3117d89b4f0dc7c8397762405406b
ms.sourcegitcommit: 0a5518fdb9d87fcc326a8507ac755936285fcb94
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2019
ms.locfileid: "72811134"
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16, mbrtoc32

Tłumaczy pierwszy znak wielobajtowy UTF-8 w ciągu na odpowiednik znaku UTF-16 lub UTF-32.

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

\ *docelowy*
Wskaźnik do **char16_t** lub **char32_t** równoważnego znaku wielobajtowego UTF-8 do przekonwertowania. Jeśli wartość jest równa null, funkcja nie przechowuje wartości.

\ *źródłowa*
Wskaźnik na ciąg znaków wielobajtowych UTF-8 do przekonwertowania.

*max_bytes*\
Maksymalna liczba bajtów w *źródle* do sprawdzenia dla znaku do przekonwertowania. Ten argument powinien być wartością z przedziału od 1 do liczby bajtów, łącznie z dowolnym terminatorem o wartości null, pozostałą w *źródle*.

\ *stanu*
Wskaźnik do obiektu stanu konwersji **mbstate_t** używany do interpretacji ciągu wielobajtowego UTF-8 do co najmniej jednego znaku wyjściowego.

## <a name="return-value"></a>Wartość zwracana

Po powodzeniu zwraca wartość pierwszego z tych warunków, które mają zastosowanie, z uwzględnieniem bieżącej wartości *stanu* :

|Wartość|Warunek|
|-----------|---------------|
|0|Następne *max_bytes* lub mniej znaków konwertowane ze *źródła* odpowiadają znakom dwubajtowym o wartości null, która jest wartością przechowywaną, jeśli *miejsce docelowe* nie ma wartości null.<br /><br /> *stan* zawiera początkowy stan przesunięcia.|
|Od 1 do *max_bytes*włącznie|Zwracana wartość to liczba bajtów *źródła* , które ukończyły prawidłowy znak wielobajtowy. Przekonwertowany znak dwubajtowy jest przechowywany, jeśli *miejsce docelowe* nie ma wartości null.|
|-3|Następny znak dwubajtowy wynikający z poprzedniego wywołania funkcji został zapisany w *miejscu docelowym* , jeśli *miejsce docelowe* nie ma wartości null. Żadne bajty ze *źródła* nie są używane przez to wywołanie funkcji.<br /><br /> Gdy *Źródło* wskazuje znak wielobajtowy UTF-8, który wymaga więcej niż jeden dwubajtowy znak do reprezentowania (na przykład para zastępcza), wartość *stanu* jest aktualizowana, tak aby następne wywołanie funkcji zapisywał dodatkowy znak.|
|-2|Następne *max_bytes* bajty reprezentują niekompletny, ale może być prawidłowym znakiem wielobajtowym UTF-8. Żadna wartość nie jest przechowywana w *miejscu docelowym*. Ten wynik może wystąpić, jeśli *max_bytes* ma wartość zero.|
|-1|Wystąpił błąd kodowania. Następna *max_bytes* lub mniejsza liczba bajtów nie przyczyniają się do pełnego i prawidłowego znaku wielobajtowego UTF-8. Żadna wartość nie jest przechowywana w *miejscu docelowym*.<br /><br /> **EILSEQ** jest przechowywany w **errno** i nie *określono wartości stanu* konwersji.|

## <a name="remarks"></a>Uwagi

Funkcja **mbrtoc16** odczytuje do *max_bytes* bajtów ze *źródła* w celu znalezienia pierwszego kompletnego, prawidłowego znaku wielobajtowego UTF-8, a następnie zapisuje odpowiednik znaku UTF-16 w *miejscu docelowym*. Jeśli znak wymaga więcej niż jednego znaku wyjściowego UTF-16, takiego jak para zastępcza, wartość *stanu* jest ustawiona na przechowywanie następnego znaku UTF-16 w *miejscu docelowym* przy następnym wywołaniu **mbrtoc16**. Funkcja **mbrtoc32** jest taka sama, ale dane wyjściowe są przechowywane jako znaki UTF-32.

Jeśli *Źródło* ma wartość null, te funkcje zwracają odpowiednik wywołania wykonanego przy użyciu argumentów o **wartości null** dla *miejsca docelowego*, `""` (pusty ciąg zakończony wartością null) dla *źródła*i 1 dla *max_bytes*. Przekazanie wartości *docelowy* i *max_bytes* są ignorowane.

Jeśli *Źródło* nie ma wartości null, funkcja rozpoczyna się na początku ciągu i sprawdza, czy *max_bytes* bajty, aby określić liczbę bajtów potrzebnych do ukończenia następnego znaku wielobajtowego UTF-8, w tym wszystkie sekwencje przesunięcia. Jeśli badane bajty zawierają prawidłowy i kompletny znak wielobajtowy UTF-8, funkcja konwertuje znak na równoważny 16-bitowy lub 32-bitowy znak lub znaki. Jeśli *miejsce docelowe* nie ma wartości null, funkcja przechowuje pierwszy (i możliwy tylko) znak wyniku w miejscu docelowym. Jeśli wymagane są dodatkowe znaki wyjściowe, wartość jest ustawiona w *stanie*, więc kolejne wywołania funkcji wyprowadzają znaki dodatkowe i zwracają wartość-3. Jeśli nie są wymagane żadne znaki wyjściowe, *stan* jest ustawiany na początkowy stan przesunięcia.

Aby skonwertować znaki wielobajtowe inne niż UTF-8 na znaki UTF-16 LE, użyj funkcji [mbrtowc](mbrtowc.md), [mbtowc lub _mbtowc_l](mbtowc-mbtowc-l.md) .

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|C++nagłówki|
|--------------|--------------|------------------|
|**mbrtoc16**, **mbrtoc32**|\<uchar. h >|\<cuchar >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../compatibility.md).

## <a name="see-also"></a>Zobacz także

\ [konwersji danych](../data-conversion.md)
\ [ustawień regionalnych](../locale.md)
[Interpretacja sekwencji znaków wielobajtowych](../interpretation-of-multibyte-character-sequences.md)\
[c16rtomb, c32rtomb](c16rtomb-c32rtomb1.md)\
[mbrtowc](mbrtowc.md)\
[mbsrtowcs](mbsrtowcs.md)\
[mbsrtowcs_s](mbsrtowcs-s.md)
