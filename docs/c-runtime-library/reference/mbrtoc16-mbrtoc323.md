---
title: mbrtoc16, mbrtoc323
ms.date: 4/2/2020
api_name:
- mbrtoc16
- mbrtoc32
- _o_mbrtoc16
- _o_mbrtoc32
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
- mbrtoc16
- mbrtoc32
- uchar/mbrtoc16
- uchar/mbrtoc32
helpviewer_keywords:
- mbrtoc16 function
- mbrtoc32 function
ms.assetid: 099ade4d-56f7-4e61-8b45-493f1d7a64bd
ms.openlocfilehash: 113c103cfedfe1982c8524623b259c3d58d4f4e2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234071"
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

*punktu*\
Wskaźnik do **`char16_t`** lub **`char32_t`** równoważnego znaku wielobajtowego UTF-8 do przekonwertowania. Jeśli wartość jest równa null, funkcja nie przechowuje wartości.

*zewnętrz*\
Wskaźnik na ciąg znaków wielobajtowych UTF-8 do przekonwertowania.

*max_bytes*\
Maksymalna liczba bajtów w *źródle* do sprawdzenia dla znaku do przekonwertowania. Ten argument powinien być wartością z przedziału od 1 do liczby bajtów, łącznie z dowolnym terminatorem o wartości null, pozostałą w *źródle*.

*Państwu*\
Wskaźnik do obiektu stanu konwersji **mbstate_t** używany do interpretowania ciągu wielobajtowego UTF-8 do co najmniej jednego znaku wyjściowego.

## <a name="return-value"></a>Wartość zwracana

Po powodzeniu zwraca wartość pierwszego z tych warunków, które mają zastosowanie, z uwzględnieniem bieżącej wartości *stanu* :

|Wartość|Warunek|
|-----------|---------------|
|0|Kolejne *max_bytes* lub mniej znaków przekonwertowane ze *źródła* odpowiadają znakom dwubajtowym null, czyli wartością przechowywaną, jeśli *miejsce docelowe* nie ma wartości null.<br /><br /> *stan* zawiera początkowy stan przesunięcia.|
|Od 1 do *max_bytes*włącznie|Zwracana wartość to liczba bajtów *źródła* , które ukończyły prawidłowy znak wielobajtowy. Przekonwertowany znak dwubajtowy jest przechowywany, jeśli *miejsce docelowe* nie ma wartości null.|
|-3|Następny znak dwubajtowy wynikający z poprzedniego wywołania funkcji został zapisany w *miejscu docelowym* , jeśli *miejsce docelowe* nie ma wartości null. Żadne bajty ze *źródła* nie są używane przez to wywołanie funkcji.<br /><br /> Gdy *Źródło* wskazuje znak wielobajtowy UTF-8, który wymaga więcej niż jeden dwubajtowy znak do reprezentowania (na przykład para zastępcza), wartość *stanu* jest aktualizowana, tak aby następne wywołanie funkcji zapisywał dodatkowy znak.|
|-2|Kolejne *max_bytes* bajty reprezentują niekompletny, ale może być prawidłowym znakiem wielobajtowym UTF-8. Żadna wartość nie jest przechowywana w *miejscu docelowym*. Ten wynik może wystąpić, jeśli *max_bytes* wynosi zero.|
|-1|Wystąpił błąd kodowania. Następny *max_bytes* lub mniej bajtów nie przyczynia się do pełnego i prawidłowego znaku wielobajtowego UTF-8. Żadna wartość nie jest przechowywana w *miejscu docelowym*.<br /><br /> **EILSEQ** jest przechowywany w **errno** i nie *określono wartości stanu* konwersji.|

## <a name="remarks"></a>Uwagi

Funkcja **mbrtoc16** odczytuje do *max_bytes* bajty ze *źródła* , aby znaleźć pierwszy kompletny, prawidłowy znak wielobajtowy UTF-8, a następnie przechowuje odpowiedni znak UTF-16 w *miejscu docelowym*. Jeśli znak wymaga więcej niż jednego znaku wyjściowego UTF-16, takiego jak para zastępcza, wartość *stanu* jest ustawiona na przechowywanie następnego znaku UTF-16 w *miejscu docelowym* przy następnym wywołaniu **mbrtoc16**. Funkcja **mbrtoc32** jest taka sama, ale dane wyjściowe są przechowywane jako znaki UTF-32.

Jeśli *Źródło* ma wartość null, te funkcje zwracają odpowiednik wywołania wykonanego przy użyciu argumentów o **wartości null** dla *miejsca docelowego* `""` (pusty ciąg zakończony wartością null) dla *źródła*i 1 dla *max_bytes*. Przekazanie wartości *docelowej* i *max_bytes* są ignorowane.

Jeśli *Źródło* nie ma wartości null, funkcja rozpoczyna się na początku ciągu i sprawdza, czy *max_bytes* bajtów, aby określić liczbę bajtów potrzebnych do ukończenia następnego znaku wielobajtowego UTF-8, w tym wszystkie sekwencje przesunięcia. Jeśli badane bajty zawierają prawidłowy i kompletny znak wielobajtowy UTF-8, funkcja konwertuje znak na równoważny 16-bitowy lub 32-bitowy znak lub znaki. Jeśli *miejsce docelowe* nie ma wartości null, funkcja przechowuje pierwszy (i możliwy tylko) znak wyniku w miejscu docelowym. Jeśli wymagane są dodatkowe znaki wyjściowe, wartość jest ustawiona w *stanie*, więc kolejne wywołania funkcji wyprowadzają znaki dodatkowe i zwracają wartość-3. Jeśli nie są wymagane żadne znaki wyjściowe, *stan* jest ustawiany na początkowy stan przesunięcia.

Aby skonwertować znaki wielobajtowe inne niż UTF-8 na znaki UTF-16 LE, użyj funkcji [mbrtowc](mbrtowc.md), [mbtowc lub _mbtowc_l](mbtowc-mbtowc-l.md) .

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek C++|
|--------------|--------------|------------------|
|**mbrtoc16**, **mbrtoc32**|\<uchar.h>|\<cuchar>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../compatibility.md).

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../data-conversion.md)\
[Ustawienie](../locale.md)\
[Interpretacja sekwencji znaków wielobajtowych](../interpretation-of-multibyte-character-sequences.md)\
[c16rtomb, c32rtomb](c16rtomb-c32rtomb1.md)\
[mbrtowc](mbrtowc.md)\
[mbsrtowcs](mbsrtowcs.md)\
[mbsrtowcs_s](mbsrtowcs-s.md)
