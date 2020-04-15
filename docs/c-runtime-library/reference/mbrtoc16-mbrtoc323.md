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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 91755d19eacf73f19700eed7fffbffc529d4e235
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340979"
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16, mbrtoc32

Tłumaczy pierwszy znak wielobajtowy UTF-8 w ciągu na równoważny znak UTF-16 lub UTF-32.

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

*Docelowy*\
Wskaźnik do **char16_t** lub **char32_t** odpowiednika znaku wielobajtowego UTF-8 do konwersji. Jeśli wartość null, funkcja nie przechowuje wartości.

*Źródła*\
Wskaźnik do ciągu znaków wielobajtowych UTF-8 do konwersji.

*max_bytes*\
Maksymalna liczba bajtów w *źródle* do zbadania dla znaku do konwersji. Ten argument powinien być wartością między jednym a liczbą bajtów, w tym dowolnym zerowym terminatorem, *pozostającym*w źródle .

*Państwa*\
Wskaźnik do obiektu stanu konwersji **mbstate_t** używanego do interpretowania wielobajtowego ciągu UTF-8 na jeden lub więcej znaków wyjściowych.

## <a name="return-value"></a>Wartość zwracana

Po powodzenie zwraca wartość pierwszego z tych warunków, który ma zastosowanie, biorąc pod uwagę bieżącą wartość *stanu:*

|Wartość|Warunek|
|-----------|---------------|
|0|Następny *max_bytes* lub mniej znaków przekonwertowanych ze *źródła* odpowiada znakowi szerokości null, który jest wartością przechowywaną, jeśli *miejsce docelowe* nie jest null.<br /><br /> *stan* zmiany zawiera stan początkowej zmiany.|
|Od 1 *do max_bytes*włącznie|Zwrócona wartość to liczba bajtów *źródła,* które wypełniają prawidłowy znak wielobajtowy. Przekonwertowany znak szeroki jest przechowywany, jeśli *miejsce docelowe* nie jest null.|
|-3|Następny znak szeroki wynikające z poprzedniego wywołania funkcji został zapisany w *miejscu docelowym,* jeśli *miejsce docelowe* nie jest null. Żadne bajty ze *źródła* nie są używane przez to wywołanie funkcji.<br /><br /> Gdy *źródło* wskazuje znak wielobajtowy UTF-8, który wymaga więcej niż jednego znaku szerokiego do reprezentowania (na przykład pary zastępczej), wartość *stanu* jest aktualizowana, tak aby następne wywołanie funkcji wypisywało dodatkowy znak.|
|-2|Następny *max_bytes* bajtów reprezentują niekompletny, ale potencjalnie prawidłowy znak wielobajtowy UTF-8. Żadna wartość nie jest przechowywana w *miejscu docelowym*. Ten wynik może wystąpić, jeśli *max_bytes* wynosi zero.|
|-1|Wystąpił błąd kodowania. Następny *max_bytes* lub mniej bajtów nie przyczyniają się do pełnego i prawidłowego znaku wielobajtowego UTF-8. Żadna wartość nie jest przechowywana w *miejscu docelowym*.<br /><br /> **EILSEQ** jest przechowywany w **errno** i *stan* wartości stanu konwersji jest nieokreślony.|

## <a name="remarks"></a>Uwagi

Funkcja **mbrtoc16** odczytuje do *max_bytes* bajtów ze *źródła,* aby znaleźć pierwszy kompletny, prawidłowy znak wielobajtowy UTF-8, a następnie przechowuje równoważny znak UTF-16 w *miejscu docelowym*. Jeśli znak wymaga więcej niż jednego znaku wyjściowego UTF-16, takiego jak para zastępcza, wartość *stanu* jest ustawiona na przechowywanie następnego znaku UTF-16 w *miejscu docelowym* przy następnym wywołaniu **mbrtoc16**. Funkcja **mbrtoc32** jest identyczna, ale dane wyjściowe są przechowywane jako znak UTF-32.

Jeśli *źródło* ma wartość null, te funkcje zwracają odpowiednik wywołania wywołanego przy użyciu argumentów **NULL** dla *miejsca docelowego* `""` (pusty, zakończony zerem ciąg) dla *źródła*i 1 dla *max_bytes*. Przekazane wartości *miejsca docelowego* i *max_bytes* są ignorowane.

Jeśli *źródło* nie jest null, funkcja rozpoczyna się na początku ciągu i sprawdza do *max_bytes* bajtów, aby określić liczbę bajtów wymaganych do ukończenia następnego znaku wielobajtowego UTF-8, w tym sekwencji zmian. Jeśli badane bajty zawierają prawidłowy i kompletny znak wielobajtowy UTF-8, funkcja konwertuje znak na równoważny znak lub znaki o szerokości 16-bitowej lub 32-bitowej. Jeśli *miejsce docelowe* nie jest null, funkcja przechowuje pierwszy (i ewentualnie tylko) znak wynik w miejscu docelowym. Jeśli wymagane są dodatkowe znaki wyjściowe, wartość jest ustawiona w *stanie*, tak aby kolejne wywołania funkcji wyjściowe dodatkowe znaki i zwrócić wartość -3. Jeśli nie więcej znaków wyjściowych są wymagane, a następnie *stan* jest ustawiony na stan początkowego przesunięcia.

Aby przekonwertować znaki wielobajtowe inne niż UTF-8 na znaki LE UTF-16, należy użyć funkcji [mbrtowc,](mbrtowc.md) [mbtowc lub _mbtowc_l.](mbtowc-mbtowc-l.md)

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**mbrtoc16**, **mbrtoc32**|\<uchar.h>|\<> cuchar|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../compatibility.md).

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../data-conversion.md)\
[Ustawień regionalnych](../locale.md)\
[Interpretacja sekwencji znaków wielobajtowych](../interpretation-of-multibyte-character-sequences.md)\
[c16rtomb, c32rtomb](c16rtomb-c32rtomb1.md)\
[mbrtowc (mbrtowc)](mbrtowc.md)\
[mbsrtowcs](mbsrtowcs.md)\
[mbsrtowcs_s](mbsrtowcs-s.md)
