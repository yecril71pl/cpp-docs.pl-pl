---
title: mbrtoc16, mbrtoc323 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- mbrtoc16 function
- mbrtoc32 function
ms.assetid: 099ade4d-56f7-4e61-8b45-493f1d7a64bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a12e90f9a4bc0cc27df421c27d77a1b9b69334b9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16, mbrtoc32

Tłumaczy wielobajtowe pierwszego znaku w ciągu typu narrow na równoważne znaku UTF-16 lub UTF-32.

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

*Miejsce docelowe*<br/>
Wskaźnik do **char16_t** lub **char32_t** równoważne znaków wielobajtowych do konwersji. Jeśli wartość null, funkcja nie przechowuje wartość.

*source*<br/>
Wskaźnik do ciągu znaków wielobajtowych do konwersji.

*max_bytes*<br/>
Maksymalna liczba bajtów w *źródła* do sprawdzenia znaku do konwersji. Powinna to być wartość z przedziału od jeden i liczba bajtów, w tym wszelkie terminatorem null w *źródła*.

*state*<br/>
Wskaźnik do **mbstate_t** obiekt stanu konwersji sposób interpretowania wielobajtowe ciąg do co najmniej jeden znak danych wyjściowych.

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia, zwraca wartość pierwszego z tych warunków, których dotyczy, ponieważ jego bieżący *stanu* wartość:

|Wartość|Warunek|
|-----------|---------------|
|0|Następne *max_bytes* lub mniej znaków skonwertowane z *źródła* odpowiadają null znaków dwubajtowych jest to wartość, jeśli *docelowego* nie jest zerowa.<br /><br /> *Stan* zawiera stan początkowy shift.|
|Między 1 a *max_bytes*włącznie|Wartość zwracana jest liczba bajtów *źródła* który ukończyć prawidłowy znaków wielobajtowych. Przekonwertowana znaków dwubajtowych są przechowywane, jeśli *docelowego* nie jest zerowa.|
|-3|Następny znak szeroki wynikające z poprzedniego wywołania funkcji przechowywanych w *docelowego* Jeśli *docelowego* nie jest zerowa. Brak bajtów z *źródła* są używane przez wywołanie tej funkcji.<br /><br /> Gdy *źródła* wskazuje znaków wielobajtowych, która wymaga więcej niż jednego znaku dwubajtowe do reprezentowania (na przykład para zastępcza), a następnie *stanu* wartość jest aktualizowana, dzięki czemu zapisuje następnego wywołania funkcji  limit dodatkowych znaków.|
|-2|Następne *max_bytes* bajty reprezentują ukończona, ale potencjalnie prawidłowy, wielobajtowe znaków. Wartość nie jest przechowywana w *docelowego*. Wynik ten może wystąpić, jeśli *max_bytes* wynosi zero.|
|-1|Wystąpił błąd kodowania. Następne *max_bytes* lub mniej bajtów nie wspierają znaków wielobajtowych pełne i prawidłowe. Wartość nie jest przechowywana w *docelowego*.<br /><br /> **Eilseq —** są przechowywane w **errno** i stan konwersji *stanu* jest nieokreślony.|

## <a name="remarks"></a>Uwagi

**Mbrtoc16** funkcja odczytuje do *max_bytes* bajtów z *źródła* można znaleźć pierwszego znaków wielobajtowych pełną, prawidłowy, a następnie zapisuje równoważne UTF-16 znak w *docelowego*. Źródło, z jaką bajty są interpretowane zgodnie z bieżącym wielobajtowe ustawienia regionalne wątku. Jeśli znaków wielobajtowych wymaga więcej niż jednego znaku danych wyjściowych UTF-16, takie jak para zastępcza, a następnie *stanu* ma wartość przechowywania po następnym znaku UTF-16 *docelowego* na następne wywołanie **mbrtoc16**. **Mbrtoc32** funkcji jest taki sam, ale dane wyjściowe są przechowywane w postaci znaku UTF-32.

Jeśli *źródła* ma wartość null, te funkcje, które są zwracane odpowiednikiem połączenie zostało nawiązane przy użyciu argumentów **NULL** dla *docelowego*, **""** dla *źródła*, a wartość 1 dla *max_bytes*. Przekazane wartości *docelowego* i *max_bytes* są ignorowane.

Jeśli *źródła* jest nie null, funkcja rozpoczyna się od początku ciągu i sprawdza do *max_bytes* bajtów, aby określić liczbę bajtów wymaganą do wykonania następnego znaków wielobajtowych, łącznie z wszystkie sekwencje shift. Jeśli zbadane bajtów zawiera prawidłowe i kompletne znaków wielobajtowych, funkcja konwertuje znak na równoważne znaków dwubajtowych 16-bitowych lub 32-bitowy lub znaków. Jeśli *docelowego* jest nie null, funkcja magazynów znak wynik pierwszy (i prawdopodobnie tylko) w lokalizacji docelowej. Jeśli wymagane są dodatkowe dane wyjściowe znaków, wartość jest ustawiana w *stanu*, dzięki czemu kolejne wywołania funkcji output dodatkowe znaki i zwraca wartość -3. Jeśli żadne więcej danych wyjściowych znaki nie są wymagane, następnie *stanu* ma ustawioną wartość stanu początkowego przesunięcia.

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek C++|
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
