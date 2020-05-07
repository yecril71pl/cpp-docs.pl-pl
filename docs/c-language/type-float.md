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

Liczby zmiennoprzecinkowe używają formatu IEEE (Institute of Electrical and Electronics Engineers). Wartości o pojedynczej precyzji z typem zmiennoprzecinkowym mają 4 bajty, składające się z bitu znaku, 8-127 bitowego mantysyego pliku binarnego i 23-bitowego. Mantysy reprezentuje liczbę z zakresu od 1,0 do 2,0. Ponieważ bit wysokiego rzędu mantysy ma zawsze wartość 1, nie jest on przechowywany w liczbie. Ta reprezentacja daje zakres około 3.4 E-38 do 3.4 E + 38 dla typu zmiennoprzecinkowego.

Można zadeklarować zmienne jako zmiennoprzecinkowe lub podwójne, w zależności od potrzeb aplikacji. Główne różnice między tymi dwoma typami są istotnym znaczeniem, które mogą reprezentować, wymaganym przez nich magazynem oraz ich zakresem. W poniższej tabeli przedstawiono relacje między wymaganiami dotyczącymi istotności i magazynu.

### <a name="floating-point-types"></a>Typy zmiennoprzecinkowe

|Typ|Znaczące cyfry|Liczba bajtów|
|----------|------------------------|---------------------|
|float|6 - 7|4|
|double|15 - 16|8|

Zmienne zmiennoprzecinkowe są reprezentowane przez mantysy, który zawiera wartość liczby oraz wykładnik, który zawiera kolejność wielkości liczby.

W poniższej tabeli przedstawiono liczbę bitów przydzieloną do mantysy oraz wykładnik dla każdego typu zmiennoprzecinkowego. Najbardziej znaczący bit dowolnego typu float lub Double jest zawsze bitem znaku. Jeśli wartość to 1, liczba jest uznawana za negatywną; w przeciwnym razie jest uznawana za liczbę dodatnią.

### <a name="lengths-of-exponents-and-mantissas"></a>Długości wykładników i mantysy

|Typ|Długość wykładnika|Długość mantysy|
|----------|---------------------|---------------------|
|float|8 bitów|23 bity|
|double|11 bitów|52 bitów|

Ponieważ wykładniki są przechowywane w postaci niepodpisanej, wykładnik jest podzielny o połowę możliwej wartości. Dla typu float, odchylenie wynosi 127; dla typu Double jest 1023. Rzeczywistą wartość wykładnika można obliczyć, odejmując wartość bias z wartości wykładnika.

Mantysy jest przechowywany jako ułamek binarny o wartości większej lub równej 1 i mniejszej niż 2. W przypadku typów zmiennoprzecinkowych i podwójnie jest implikowane wiodące 1 w mantysy w najbardziej znaczących pozycjach w bitach, więc mantysy są odpowiednio 24 i 53 bitów, nawet jeśli najbardziej znaczący bit nigdy nie jest przechowywany w pamięci.

Zamiast właśnie opisanej metody Storage pakiet zmiennoprzecinkowy może przechowywać binarne liczby zmiennoprzecinkowe jako liczby nieznormalizowane. "Liczby nieznormalizowane" to wartości niezerowe liczb zmiennoprzecinkowych z zastrzeżonymi wartościami wykładnika, w których najbardziej znaczący bit mantysy wynosi 0. Przy użyciu nieznormalizowanego formatu zakres liczby zmiennoprzecinkowej można rozszerzyć o koszt dokładności. Nie można kontrolować, czy liczba zmiennoprzecinkowa jest reprezentowana w znormalizowanym lub nieznormalizowanym formacie; Pakiet zmiennoprzecinkowy określa reprezentację. Pakiet zmiennoprzecinkowy nigdy nie używa nieznormalizowanej formy, chyba że wykładnik stanie się mniejszy niż minimalny, który może być reprezentowany w znormalizowanym formularzu.

W poniższej tabeli przedstawiono minimalne i maksymalne wartości, które można przechowywać w zmiennych każdego typu zmiennoprzecinkowego. Wartości wymienione w tej tabeli dotyczą tylko znormalizowanych liczb zmiennoprzecinkowych; nieznormalizowane liczby zmiennoprzecinkowe mają mniejszą wartość minimalną. Należy zauważyć, że liczby przechowywane w rejestrach 80*x*87 są zawsze reprezentowane w postaci znormalizowanej 80 w sposób znormalizowany. liczby można reprezentować tylko w nieznormalizowanym formacie, gdy są przechowywane w 32-bitowych lub 64-bitowych zmiennych zmiennoprzecinkowych (zmienne typu float i Type Long).

### <a name="range-of-floating-point-types"></a>Zakres typów zmiennoprzecinkowych

|Typ|Wartość minimalna|Wartość maksymalna|
|----------|-------------------|-------------------|
|float|1,175494351 E-38|3,402823466 E + 38|
|double|2.2250738585072014 E-308|1.7976931348623158 E + 308|

Jeśli dokładność nie jest mniejsza niż wartość magazynu, należy rozważyć użycie typu float dla zmiennych zmiennoprzecinkowych. Odwrotnie, jeśli precyzja jest najważniejszym kryterium, użyj typu Double.

Zmienne zmiennoprzecinkowe mogą być podwyższane do typu większego znaczenia (od typu zmiennoprzecinkowego do typu Double). Promocja często odbywa się po wykonaniu arytmetycznych zmiennych zmiennoprzecinkowych. Ta arytmetyczna jest zawsze wykonywana w miarę jak najwyższego stopnia dokładności jako zmienna o najwyższym stopniu precyzji. Rozważmy na przykład następujące deklaracje typów:

```
float f_short;
double f_long;
long double f_longer;

f_short = f_short * f_long;
```

W poprzednim przykładzie zmienna `f_short` jest podwyższana do typu Double i pomnożona przez; `f_long` następnie wynik jest zaokrąglany do typu float przed przypisaniem `f_short`do.

W poniższym przykładzie (który używa deklaracji z poprzedniego przykładu) arytmetyczne jest wykonywane w postaci zmiennoprzecinkowej (32-bitowej) precyzji dla zmiennych; następnie wynik zostanie podwyższony do typu Double:

```
f_longer = f_short * f_short;
```

## <a name="see-also"></a>Zobacz też

[Magazyn typów podstawowych](../c-language/storage-of-basic-types.md)
