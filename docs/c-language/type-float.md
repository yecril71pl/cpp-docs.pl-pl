---
title: Typ float
ms.date: 11/04/2016
helpviewer_keywords:
- type float
- exponent length
- float keyword [C]
- mantissas, length
- floating-point numbers, float type
- ranges, floating-point types
- floating-point numbers, variables
- lengths, mantissa
- double data type, type float
- IEEE floating-point representation
- lengths, exponent
ms.assetid: 706e332b-17a0-4a30-b7d8-5d6cd372524b
ms.openlocfilehash: 61bfd094801165e0c3e41e5de6fcbfb0c5e59504
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346330"
---
# <a name="type-float"></a>Typ float

Liczby zmiennoprzecinkowe, użyj formatu IEEE (Institute of Electrical and Electronics Engineers). Wartości pojedynczej precyzji z typem float mieć 4 bajty, składające się z bitem znaku, wykładnik binarne 127 nadmiarowe 8-bitową i mantysy 23-bitowych. Mantysy reprezentuje liczbą z zakresu od 1.0 i 2.0. Ponieważ bit wyższego rzędu mantysy ma zawsze numer 1, nie są przechowywane w kodzie. Taka reprezentacja oferuje szeroką gamę około 3.4E-38 do 3.4E + 38 dla typu zmiennoprzecinkowego.

Można zadeklarować zmienne, float lub double, w zależności od potrzeb aplikacji. Główne różnice między tymi dwoma typami to znaczenie, które reprezentują, magazynu, których potrzebują oraz ich zakresu. W poniższej tabeli przedstawiono relację między istotności i wymagania dotyczące magazynu.

### <a name="floating-point-types"></a>Typy zmiennoprzecinkowe

|Typ|Cyfr znaczących|Liczba bajtów|
|----------|------------------------|---------------------|
|float|6 - 7|4|
|double|15 - 16|8|

Zmienne zmiennoprzecinkowe są reprezentowane przez mantysy, zawierającego wartość numer i wykładnik, który zawiera rząd wielkości liczby.

W poniższej tabeli przedstawiono liczbę bitów przydzielone do mantysy i wykładnika dla każdego typu zmiennoprzecinkowego. Najbardziej znaczący bit wszelkie float lub double jest zawsze bitu znaku. Jeśli ma wartość 1, numer jest traktowany jako ujemna; w przeciwnym razie uważa się liczbą dodatnią.

### <a name="lengths-of-exponents-and-mantissas"></a>Długości Wykładniki i mantysy

|Typ|Długość wykładnika|Długość mantysy|
|----------|---------------------|---------------------|
|float|8 bitów|23 usługi bits|
|double|Usługa bits 11|52 bitów|

Ponieważ wykładniki są przechowywane w formie bez znaku, wykładnik jest obciążona za pół możliwej wartości. Dla typu zmiennoprzecinkowego jest obliczana 127; Typ podwójnej jest 1023. Rzeczywista wartość wykładnika można obliczyć przez odjęcie wartość obciążenia z wartość wykładnika.

Mantysy jest przechowywana jako ułamek binarne większa lub równa 1 i 2 poniżej. Typy zmiennoprzecinkowe i podwójne dorozumianych 1 wiodących mantysy w jest pozycja najbardziej znaczący bit, dzięki czemu można mantysy rzeczywistości bitów 24 i 53 długo, odpowiednio, nawet najbardziej znaczący bit nigdy nie jest przechowywany w pamięci.

Zamiast metody magazynu właśnie opisanego pakiet zmiennoprzecinkowy można przechowywać binarne liczb zmiennoprzecinkowych jako liczby nieznormalizowany. "Nieznormalizowany liczby" są wartość różną od zera liczb zmiennoprzecinkowych za pomocą zastrzeżonego wartości wykładnika, w których najbardziej znaczący bit mantysy wynosi 0. Przy użyciu formatu nieznormalizowany, można rozszerzyć zakres liczba zmiennoprzecinkowa kosztem dokładności. Nie można kontrolować, czy liczba zmiennoprzecinkowa jest reprezentowany w formie znormalizowane lub nieznormalizowany; Pakiet zmiennoprzecinkowy określa reprezentacji. Pakiet zmiennoprzecinkowy nigdy nie używa nieznormalizowany formy, chyba że wykładnik staje się mniej niż wartość minimalna, którą można przedstawić w znormalizowana postać.

W poniższej tabeli przedstawiono minimalne i maksymalne wartości, można przechowywać w zmiennych każdego typu zmiennoprzecinkowego. Wartości wymienione w poniższej tabeli dotyczą tylko w znormalizowanych liczb zmiennoprzecinkowych; liczby zmiennoprzecinkowe nieznormalizowany miał mniejszą wartość minimalna. Uwaga liczb, że zachowana w 80*x*87 rejestrów zawsze są reprezentowane w 80-bitowych znormalizowana postać; numery tylko mogą być reprezentowane w formularzu nieznormalizowany gdy przechowywany w 32-bitową lub 64-bitowych zmienne zmiennoprzecinkowe (zmienne typu zmiennoprzecinkowego i typu long).

### <a name="range-of-floating-point-types"></a>Zakres wartości zmiennoprzecinkowych

|Typ|Wartość minimalna|Wartość maksymalna|
|----------|-------------------|-------------------|
|float|1.175494351 E - 38|3.402823466 E + 38|
|double|2.2250738585072014 E - 308|1.7976931348623158 E + 308|

Jeśli dokładności jest mniej istotna niż w przypadku magazynu, należy rozważyć użycie typu zmiennoprzecinkowego dla zmienne zmiennoprzecinkowe. Z drugiej strony Jeśli dokładności jest najbardziej istotna, użyj typu double.

Zmienne zmiennoprzecinkowe może być podwyższony do typu większe znaczenie (z typu zmiennoprzecinkowego na typ double). Podwyższanie poziomu często występuje, gdy można wykonać operacji arytmetycznych na zmienne zmiennoprzecinkowe. Ta operacje arytmetyczne zawsze odbywa się w jako wysoki stopień dokładności jako zmienną z najwyższy stopień dokładności. Na przykład należy wziąć pod uwagę następujące deklaracje typu:

```
float f_short;
double f_long;
long double f_longer;

f_short = f_short * f_long;
```

W poprzednim przykładzie, zmienna `f_short` jest promowany do typu double i pomnożona przez `f_long`; wynik jest zaokrąglany do typu zmiennoprzecinkowego przed przypisaniem do `f_short`.

W poniższym przykładzie (który używa deklaracji z poprzedniego przykładu), że operacje arytmetyczne odbywa się w dokładności float (32-bitowy) na zmienne; wynik jest następnie podnoszony do typu double:

```
f_longer = f_short * f_short;
```

## <a name="see-also"></a>Zobacz także

[Magazyn typów podstawowych](../c-language/storage-of-basic-types.md)
