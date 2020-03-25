---
title: Odwzorowanie liczby zmiennoprzecinkowej IEEE
ms.date: 05/06/2019
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
ms.openlocfilehash: bb8523256c05479b303dec66ca79caa28e7cda03
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169815"
---
# <a name="ieee-floating-point-representation"></a>Odwzorowanie liczby zmiennoprzecinkowej IEEE

Firma C++ Microsoft (MSVC) jest zgodna ze standardami cyfr IEEE. Standard IEEE-754 opisuje formaty zmiennoprzecinkowe w sposób przedstawiający rzeczywiste liczby sprzętu. Istnieje co najmniej pięć formatów wewnętrznych dla liczb zmiennoprzecinkowych, które są możliwe do zaprezentowania na sprzęcie przeznaczonym dla kompilatora MSVC, ale kompilator używa tylko dwóch z nich. Formaty o *pojedynczej precyzji* (4-bajtowe) i *podwójnej precyzji* (8-bajtowe) są używane w MSVC. Pojedyncza precyzja jest zadeklarowana przy użyciu słowa kluczowego **zmiennoprzecinkowego**. Podwójna precyzja jest zadeklarowana przy użyciu słowa kluczowego **Double**. IEEE standard określa również formaty *o połowie dokładności* (2-bajtowe) i *czterokrotnie Precision* (16-bajtowe), a także format *podwójnej precyzji* (10-bajtowe), który jest używany przez niektóre języki C++ C i kompilatory jako dane typu **Long Double** . W kompilatorze MSVC typ danych **Long Double** jest traktowany jako typ odrębny, ale typ magazynu jest mapowany na wartość **Double**. Istnieje jednak obsługa obliczeń w języku wewnętrznym i wielojęzycznym przy użyciu innych formatów, w tym formatu podwójnej precyzji (10-bajtowej), który jest obsługiwany przez sprzęt.

Wartości są przechowywane w następujący sposób:

|Wartość|Przechowywane jako|
|-----------|---------------|
|Pojedyncza precyzja|bit znaku, 8-bitowy wykładnik, 23-bitowy mantysę|
|Podwójna precyzja|bit znaku, 11-bitowy wykładnik, 52-bitowy mantysę|
|podwójnie rozszerzona precyzja|bit znaku, 15-bitowy wykładnik, 64-bitowy mantysę|

W formatach o pojedynczej precyzji i o podwójnej precyzji założono wiodącą 1 część ułamkową, nazywaną *mantysę* (i czasami określaną jako *mantysy*), która nie jest przechowywana w pamięci, więc mantysy są w rzeczywistości 24 lub 53 bitów, nawet jeśli są przechowywane tylko 23 lub 52 bitów. Format podwójnej precyzji w rzeczywistości przechowuje ten bit.

Wykładniki są rozdzielone połowami możliwych wartości. Oznacza to odjęcie tego bias od przechowywanego wykładniku w celu uzyskania rzeczywistego wykładnika. Jeśli przechowany wykładnik jest mniejszy niż wartość bias, jest to w rzeczywistości ujemna wykładnik.

Wykładniki są rozłączone w następujący sposób:

|Zapis|Obciążone przez|
|--------------|---------------|
|8-bitowa (pojedyncza precyzja)|127|
|11-bitowa (Podwójna precyzja)|1023|
|15-bitowa (podwójnie rozszerzona precyzja)|16383|

Te wykładniki nie są potęgami dziesięciu; są one potęgami dwóch. Oznacza to, że 8-bitowe zapisane wykładniki mogą przyjmować od-127 do 127, przechowywane jako 0 do 254. Wartość 2<sup>127</sup> jest w przybliżeniu równa 10<sup>38</sup>, która jest rzeczywistym limitem pojedynczej precyzji.

Mantysę jest przechowywany jako ułamek binarny formularza 1.XXX... Ten ułamek ma wartość większą lub równą 1 i mniejszą niż 2. Należy zauważyć, że liczby rzeczywiste są zawsze przechowywane w *znormalizowanej postaci*; oznacza to, że mantysęa jest przesunięta w lewo, tak aby bit mantysę o wysokiej kolejności miał wartość zawsze 1. Ponieważ ten bit jest zawsze 1, zakłada się, że nie jest on przechowywany w formatach o pojedynczej precyzji i podwójnej precyzji. Zakłada się, że punkt binarny (nie dziesiętny) jest po prawej stronie wiodącej wartości 1.

Format, a następnie dla różnych rozmiarów jest następujący:

|Format|bajt 1|bajt 2|bajt 3|bajt 4|Przyciski ...|bajt n|
|------------|------------|------------|------------|------------|---------|------------|
|Pojedyncza precyzja| `SXXXXXXX`|`XMMMMMMM`|`MMMMMMMM`|`MMMMMMMM`|||
|Podwójna precyzja|`SXXXXXXX`|`XXXXMMMM`|`MMMMMMMM`|`MMMMMMMM`|Przyciski ...|`MMMMMMMM`|
|podwójnie rozszerzona precyzja|`SXXXXXXX`|`XXXXXXXX`|`1MMMMMMM`|`MMMMMMMM`|Przyciski ...|`MMMMMMMM`|

`S` reprezentuje bit znaku, `X`jest bitami wykładniczymi, a `M`jest bita mantysę. Należy pamiętać, że bit z lewej strony jest przyjęty w formatach o pojedynczej precyzji i podwójnej precyzji, ale jest obecny jako "1" w bajcie 3 formatu podwójnej precyzji.

Aby prawidłowo przesunąć punkt binarny, najpierw należy rozwiązać ten wykładnik, a następnie przenieść punkt binarny w prawo lub w lewo do odpowiedniej liczby bitów.

## <a name="special-values"></a>Wartości specjalne

Formaty zmiennoprzecinkowe zawierają niektóre wartości, które są traktowane specjalnie.

### <a name="zero"></a>Zero

Nie można znormalizować wartości zero, co sprawia, że nie jest to możliwe w znormalizowanym formacie pojedynczej precyzji lub podwójnej precyzji. Specjalny wzorzec bitowy wszystkich zer reprezentuje 0. Możliwe jest również, aby reprezentować-0 jako zero z ustawionym bitem znaku, ale wartość 0 i 0 zawsze są porównywane jako równe.

### <a name="infinities"></a>Nieskończoności

Wartości + ∞ i − ∞ są reprezentowane przez wykładnik wszystkich i mantysę zer. Nieskończoności dodatnie i ujemne mogą być reprezentowane przy użyciu bitu znaku.

### <a name="subnormals"></a>Subnormalne

Istnieje możliwość reprezentowania liczby mniejszych wielkości niż najmniejszy znormalizowany numer. Te liczby są znane jako liczby *normalne* lub *nienormalne* . Jeśli wykładnik ma wartość zero, a mantysę jest różna od zera, to niejawny wiodący bit mantysę jest uznawany za zero, a nie jeden. Precyzja wartości zwykłych jest określana jako liczba zer wiodących w mantysę.

### <a name="nan---not-a-number"></a>NaN — nie jest liczbą

Istnieje możliwość reprezentowania wartości, które nie są liczbami rzeczywistymi, na przykład 0/0, w formacie zmiennoprzecinkowym IEEE. Wartość tego rodzaju jest nazywana *NaN*. Wartość NaN jest reprezentowana przez wykładnik wszystkich i niezerowych mantysę. Istnieją dwa rodzaje NaNs, *quiet* Nans lub QNaNs oraz *sygnalizowanie* Nans lub SNaNs. Cicha NaNs zawiera jedną z nich w mantysę i jest ogólnie rozmnożona przez wyrażenie. Reprezentują one wartość nieokreśloną, taką jak wynik dzielenia przez nieskończoność lub mnożenia nieskończoności przez zero. Sygnalizowanie NaNs mają wiodące zero w mantysę. Są one używane w przypadku operacji, które są nieprawidłowe, aby sygnalizować wyjątek sprzętu zmiennoprzecinkowego.

## <a name="examples"></a>Przykłady

Poniżej przedstawiono kilka przykładów w formacie o pojedynczej precyzji:

- W przypadku wartości 2 bit znaku jest równy zero, a zapisany wykładnik to 128, lub 1000 0000 w postaci binarnej, która jest 127 plus 1. Przechowywany binarny mantysę to (1.) 000 0000 0000 0000 0000 0000, który ma implikowany wiodący znak 1 i binarny, więc rzeczywista mantysę to jeden.

   |Wartość|Formuła|Reprezentacja binarna|Wartość szesnastkowa|
   |-|-|-|-|
   |2|1 * 2<sup>1</sup>|0100 0000 0000 0000 0000 0000 0000 0000|0x40000000|

- Wartość-2. Analogicznie jak + 2, z tą różnicą, że jest ustawiony bit znaku. Dotyczy to wartości ujemnych dla wszystkich liczb zmiennoprzecinkowych w formacie IEEE.

   |Wartość|Formuła|Reprezentacja binarna|Wartość szesnastkowa|
   |-|-|-|-|
   |-2|-1 * 2<sup>1</sup>|1100 0000 0000 0000 0000 0000 0000 0000|0xC0000000|

- Wartość 4. Ten sam mantysę, wykładnik zwiększa się o jeden (wartość bias to 129 lub 100 0000 1 w postaci binarnej.

   |Wartość|Formuła|Reprezentacja binarna|Wartość szesnastkowa|
   |-|-|-|-|
   |4|1 * 2<sup>2</sup>|0100 0000 1000 0000 0000 0000 0000 0000|0x40800000|

- Wartość 6. Ten sam wykładnik, mantysę jest większy o połowę — jest (1.) 100 0000... 0000 0000, ponieważ jest to ułamek binarny, to 1 1/2, ponieważ wartości ułamkowe cyfr to 1/2, 1/4, 1/8 i tak dalej.

   |Wartość|Formuła|Reprezentacja binarna|Wartość szesnastkowa|
   |-|-|-|-|
   |6|1,5<sup>* 2</sup>|0100 0000 1100 0000 0000 0000 0000 0000|0x40C00000|

- Wartość 1. Takie same mantysę jak inne uprawnienia dwóch, wykładnik, który jest mniejszy niż dwa o 127 lub 011 1111 1 w formacie binarnym.

   |Wartość|Formuła|Reprezentacja binarna|Wartość szesnastkowa|
   |-|-|-|-|
   |1|1 * 2<sup>0</sup>|0011 1111 1000 0000 0000 0000 0000 0000|0x3F800000|

- Wartość 0,75. Wykładnik z obciążeniem to 126, 011 1111 0 w postaci binarnej, a mantysę to (1.) 100 0000... 0000 0000, czyli 1 1/2.

   |Wartość|Formuła|Reprezentacja binarna|Wartość szesnastkowa|
   |-|-|-|-|
   |0.75|1,5 * 2<sup>-1</sup>|0011 1111 0100 0000 0000 0000 0000 0000|0x3F400000|

- Wartość 2,5. Dokładnie takie same, jak dwa, z wyjątkiem tego, że bit reprezentujący 1/4 jest ustawiony w mantysę.

   |Wartość|Formuła|Reprezentacja binarna|Wartość szesnastkowa|
   |-|-|-|-|
   |2.5|1,25<sup>* 2</sup>|0100 0000 0010 0000 0000 0000 0000 0000|0x40200000|

- 1/10 jest powtarzaną częścią binarną. Mantysę jest lubiszem 1,6, a wykładnik z różnicami oznacza, że 1,6 jest podzielona przez 16 (jest 011 1101 1 w postaci binarnej, która jest 123 w postaci dziesiętnej). Prawdziwe wykładnika to 123-127 =-4, co oznacza, że współczynnik, przez który ma być mnożony, wynosi 2<sup>-4</sup> = 1/16. Należy zauważyć, że składowane mantysę jest zaokrąglane w górę ostatniego bitu — próba reprezentowania niereprezentowanego numeru jak dokładnie tak, jak to możliwe. (Przyczyny, że 1/10 i 1/100 nie są dokładnie reprezentowane w postaci binarnej, są podobne do przyczyny, że 1/3 nie można dokładnie przedstawić w postaci dziesiętnej).

   |Wartość|Formuła|Reprezentacja binarna|Wartość szesnastkowa|
   |-|-|-|-|
   |0.1|1,6 * 2<sup>– 4</sup>|0011 1101 1100 1100 1100 1100 1100 1101|0x3DCCCCCD|

- Zero jest szczególnym przypadkiem, który używa formuły dla minimalnej możliwej reprezentacji wartości dodatniej, która jest równa zero.

   |Wartość|Formuła|Reprezentacja binarna|Wartość szesnastkowa|
   |-|-|-|-|
   |0|1 * 2<sup>– 128</sup>|0000 0000 0000 0000 0000 0000 0000 0000|0x00000000|

## <a name="see-also"></a>Zobacz też

[Dlaczego liczby zmiennoprzecinkowe mogą tracić dokładność](why-floating-point-numbers-may-lose-precision.md)
