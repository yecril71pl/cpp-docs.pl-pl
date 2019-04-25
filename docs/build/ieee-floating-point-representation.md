---
title: Odwzorowanie liczby zmiennoprzecinkowej IEEE
ms.date: 11/04/2016
helpviewer_keywords:
- float keyword
- real*8 value
- floating-point numbers, IEEE representation
- double data type, floating-point representation
- IEEE floating point representation
- real*10 value
- long double
- real*4 value
ms.assetid: 537833e8-fe05-49fc-8169-55fd0314b195
ms.openlocfilehash: 69686e7e1c8994b799607eebf7e50387ed688272
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188837"
---
# <a name="ieee-floating-point-representation"></a>Odwzorowanie liczby zmiennoprzecinkowej IEEE

Microsoft Visual C++ jest zgodne z normami liczbowych IEEE. Standard IEEE 754 opisano formaty zmiennoprzecinkowych, sposobem reprezentowania liczb rzeczywistych sprzętu. Istnieją co najmniej pięć wewnętrznego formaty liczb zmiennoprzecinkowych, które są reprezentowanych w sprzęcie docelowe za pomocą kompilatora MSVC, ale kompilator używa tylko dwa z nich. *Pojedynczej precyzji* (4-bajtową) i *podwójnej precyzji* formaty (8-bajtową) są używane w programie Visual C++. Pojedynczej precyzji jest zadeklarowany za pomocą słowa kluczowego **float**. Podwójnej precyzji jest zadeklarowany za pomocą słowa kluczowego **double**. Określa również standardu IEEE *połowie precyzji* (2-bajtowych) i *poczwórnej precyzji* formatów (16-bajtową), a także *podwójnej extended precyzji* (10-bajtową) Format, który niektóre kompilatory języków C i C++ zaimplementować jako **typu long double** typu danych. W kompilatora MSVC **typu long double** — typ danych jest traktowany jako typ samodzielny, ale typ magazynu mapuje **double**. Jest jednak wewnętrzne i język asemblera obsługę obliczeń przy użyciu innych formatach, w tym formacie (10-bajtową) podwójnej extended precyzji, jeśli są obsługiwane przez sprzęt.

Wartości są przechowywane w następujący sposób:

|Wartość|Przechowywany jako|
|-----------|---------------|
|pojedynczej precyzji|Zaloguj się bit, wykładnik 8-bitową, mantysa 23-bitowy|
|podwójnej precyzji|Zaloguj się bit, wykładnik 11-bitowy, mantysa do 52-bitowy|
|podwójnej extended precyzji|Zaloguj się bit, wykładnik 15-bitowy, mantysa 64-bitowych|

W formatach pojedynczej precyzji, jak i podwójną precyzją, w części ułamkowej, wywoływana jest zakładanego 1 wiodących *mantysa* (a czasami określane jako *mantysy*), to znaczy nie są przechowywane w pamięci, dzięki czemu można mantysy rzeczywistości 24 lub 53 bitów, nawet, jeśli są przechowywane tylko 23 lub 52 bitów. Format podwójnej extended precyzji faktycznie przechowuje ten bit.

Wykładniki są obciążona o połowę ich, możliwej wartości. Oznacza to, że odjąć to odchylenie od przechowywanych wykładnik, aby uzyskać rzeczywiste wykładnik potęgi. Jeśli wykładnik przechowywane jest mniejsza niż różnica, jest faktycznie ujemnego wykładnika.

Wykładniki obciążona są w następujący sposób:

|Wykładnik|Obciążona|
|--------------|---------------|
|8-bitowa (pojedynczej precyzji)|127|
|11-bitowych (podwójnej precyzji)|1023|
|15-bitowych (podwójnej extended precyzji)|16383|

Nie są te wykładniki potęgi dziesięciu; są one potęgi liczb. Oznacza to 8-bitowej składowaną wykładniki do zakresu od -127 do 127, przechowywane jako 0 do 254. Wartość 2<sup>127</sup> jest w przybliżeniu równa 10<sup>38</sup>, czyli rzeczywisty limit pojedynczej precyzji.

Mantysy jest przechowywana jako ułamek binarne formularza 1.XXX.... Ta część ma wartość większa niż lub równa 1 i mniej niż 2. Należy pamiętać, że liczb rzeczywistych zawsze są przechowywane w *znormalizowane formularza*; oznacza to mantysa jest przesunięty w lewo taki sposób, że bit wyższego rzędu mantysy ma zawsze numer 1. Ponieważ ten bit jest zawsze 1, zakłada się (nie przechowywanych) w formatach pojedynczej precyzji, jak i podwójną precyzją. Binarny (dziesiętna) punktu zakłada się, że na prawo od wiodących 1.

Format, a następnie dla różnych rozmiarów jest następująca:

|Format|1 bajt|Bajt 2|Bajt 3|4 bajtów|...|n bajtów|
|------------|------------|------------|------------|------------|---------|------------|
|pojedynczej precyzji| `SXXXXXXX`|`XMMMMMMM`|`MMMMMMMM`|`MMMMMMMM`|||
|podwójnej precyzji|`SXXXXXXX`|`XXXXMMMM`|`MMMMMMMM`|`MMMMMMMM`|...|`MMMMMMMM`|
|podwójnej extended precyzji|`SXXXXXXX`|`XXXXXXXX`|`1MMMMMMM`|`MMMMMMMM`|...|`MMMMMMMM`|

`S` reprezentuje bitu znaku `X`firmy obciążonej wykładnika bitów, a `M`firmy bitów mantysa. Należy pamiętać, zakłada, że w pojedynczej precyzji, jak i podwójną precyzją formatach bitu skrajnie po lewej stronie, ale znajduje się na wartość "1" w bajtach 3 format podwójnej extended precyzji.

Aby przenieść punkt binarne prawidłowo, należy najpierw unbias wykładnik a następnie przenieść punkt binarnych z prawej strony lub left odpowiednią liczbę bitów.

## <a name="special-values"></a>Specjalnych wartości

Zmiennoprzecinkowe formaty obejmują niektóre wartości, które są traktowane jako specjalnie.

### <a name="zero"></a>Zero

Nie można znormalizować zero, co czyni go wyniku w postaci znormalizowane wartości pojedynczej precyzji lub podwójnej precyzji. Wzorzec bitowy specjalne zer reprezentuje 0. Możliwe jest również do reprezentowania - 0 jako zero ze znakiem bit, ale - 0 i 0 zawsze Porównuj jako równe.

### <a name="infinities"></a>Nieskończoności

+ ∞; i −∞ wartości są reprezentowane przez wykładnik samych jedynek i mantysę zer. Pozytywne i negatywne nieskończoności może być reprezentowany za pomocą bitu znaku.

### <a name="subnormals"></a>Subnormals

Istnieje możliwość do reprezentowania liczby mniejsze znaczenie niż najmniejsza liczba znormalizowanych. Numery te są znane jako *subnormal* lub *zdenormalizowany* liczb. Jeśli wykładnik jest zer i mantysy jest różna od zera, niejawne bit wiodących mantysy jest traktowany jako zero, nie jeden. Dokładność liczb subnormal ulegnie awarii jak rośnie liczba zer wiodących w mantysa.

### <a name="nan---not-a-number"></a>NaN — nie jest liczbą

Istnieje możliwość, do reprezentowania wartości niebędące liczbą rzeczywistą, np. 0 / 0, w formacie zmiennoprzecinkowych IEEE. Wartość tego typu jest nazywana *NaN*. NaN jest reprezentowany przez wykładnik samych jedynek i mantysy różna od zera. Istnieją dwa rodzaje NaNs, *cichy* NaNs lub QNaNs, i *sygnalizacji* NaNs lub SNaNs. NaNs cichy mają wiodących jeden w mantysy i zwykle są propagowane przy użyciu wyrażenia. Reprezentują one wartość nieokreśloną, na przykład w wyniku dzielenia przez nieskończoności lub mnożenia wartości infinity przez zero. NaNs sygnalizacji mają zerem w mantysa. Są one używane dla operacji, które nie są prawidłowe w celu sygnalizowania, że wyjątków zmiennoprzecinkowych sprzętu.

## <a name="examples"></a>Przykłady

Poniżej przedstawiono kilka przykładów w formacie pojedynczej precyzji:

- Wartość 2 bit znaku ma wartość zero i przechowywanych wykładnik to 128 lub 1000 0000 plików binarnych, czyli 127 powiększoną o 1. Przechowywane mantysę binarnego jest (1). 000 0000 0000 0000 0000 0000, mającej dorozumianych wiodących binarnej i 1 punkt, dlatego mantysę rzeczywisty jest jednym.

   |Wartość|Formuła|Reprezentacja binarna|Wartość szesnastkowa|
   |-|-|-|-|
   |2|1 * 2<sup>1</sup>|0100 0000 0000 0000 0000 0000 0000 0000|0x40000000|

- Wartość -2. Taki sam jak + 2, z tą różnicą, że ustawiono bitu znaku. Ta zasada obowiązuje dla wartości ujemnych wszystkich liczb zmiennoprzecinkowych format IEEE.

   |Wartość|Formuła|Reprezentacja binarna|Wartość szesnastkowa|
   |-|-|-|-|
   |-2|-1 * 2<sup>1</sup>|1100 0000 0000 0000 0000 0000 0000 0000|0xC0000000|

- Wartość 4. Ten sam mantysę wykładnik zwiększa się o jeden (obciążonej wartość 129 lub 100 0000 1 w pliku binarnym.

   |Wartość|Formuła|Reprezentacja binarna|Wartość szesnastkowa|
   |-|-|-|-|
   |4|1 * 2<sup>2</sup>|0100 0000 1000 0000 0000 0000 0000 0000|0x40800000|

- Wartość 6. Wykładnik tej samej mantysę jest większa o połowę — jego (1). 100 0000 ... 0000 0000, który, ponieważ jest to ułamek binarnego jest 1 1/2, ponieważ wartości cyfr ułamkowych, jaka jest 1/2, 1/4, 1/8 i tak dalej.

   |Wartość|Formuła|Reprezentacja binarna|Wartość szesnastkowa|
   |-|-|-|-|
   |6|1.5 * 2<sup>2</sup>|0100 0000 1100 0000 0000 0000 0000 0000|0x40C00000|

- Wartość 1. Tego samego mantysę jako inne potęgi liczby dwa obciążonej wykładnik jest pojedynczo mniej niż dwa 127 lub 011 1111 1 w pliku binarnym.

   |Wartość|Formuła|Reprezentacja binarna|Wartość szesnastkowa|
   |-|-|-|-|
   |1|1 * 2<sup>0</sup>|0011 1111 1000 0000 0000 0000 0000 0000|0x3F800000|

- Wartość 0,75. Obciążonej wykładnik jest 126 011 1111 0 w pliku binarnego i mantysy jest (1). 100 0000 ... 0000 0000, która jest 1 1/2.

   |Wartość|Formuła|Reprezentacja binarna|Wartość szesnastkowa|
   |-|-|-|-|
   |0.75|1.5 * 2<sup>-1</sup>|0011 1111 0100 0000 0000 0000 0000 0000|0x3F400000|

- Wartość 2.5. Dokładnie tak samo jak dwa poza tym, że bitu, który reprezentuje 1/4 jest ustawiana w mantysa.

   |Wartość|Formuła|Reprezentacja binarna|Wartość szesnastkowa|
   |-|-|-|-|
   |2.5|1.25 * 2<sup>1</sup>|0100 0000 0010 0000 0000 0000 0000 0000|0x40200000|

- 1/10 jest ułamek powtarzające się w pliku binarnym. Mantysy jest po prostu shy w wersji 1.6 i wykładnik obciążonej tym, że w wersji 1.6 podzielony przez 16 (jest to 1 1101 011 plików binarnych, czyli 123 w zapisie dziesiętnym). Wartość true, wykładnik jest 123-127 = - 4, co oznacza, że współczynnik mnożenia 2<sup>-4</sup> = 1/16. Należy zauważyć, że przechowywane mantysę jest zaokrąglana w górę w ostatnim bitowej — próba do reprezentowania liczby wyniku, jak to możliwe. (Przyczyna 1/10 do 1/100 są dokładnie reprezentowanych w pliku binarnym jest podobny do przyczyna to nie dokładnie reprezentowanych w zapisie dziesiętnym 1/3.)

   |Wartość|Formuła|Reprezentacja binarna|Wartość szesnastkowa|
   |-|-|-|-|
   |0.1|1.6 * 2<sup>-4</sup>|0011 1101 1100 1100 1100 1100 1100 1101|0x3DCCCCCD|

- Zero jest szczególnym przypadkiem używa formuły możliwe stałego dodatnie wartości minimalnej, która jest zer.

   |Wartość|Formuła|Reprezentacja binarna|Wartość szesnastkowa|
   |-|-|-|-|
   |0|1 * 2<sup>-128</sup>|0000 0000 0000 0000 0000 0000 0000 0000|0x00000000|

## <a name="see-also"></a>Zobacz także

[Dlaczego liczby zmiennoprzecinkowe mogą tracić dokładność](why-floating-point-numbers-may-lose-precision.md)