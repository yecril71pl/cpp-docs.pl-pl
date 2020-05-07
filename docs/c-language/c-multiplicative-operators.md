---
title: Operatory mnożenia języka C
ms.date: 11/04/2016
helpviewer_keywords:
- arithmetic operators [C++], multiplicative operators
- / operator
- / operator, multiplicative operators
- remainder operator (%)
- operators [C], multiplication
- '% operator'
- slash (/) operator
- multiplication operator [C++], multiplicative operators
ms.assetid: 495471c9-319b-4eb4-bd97-039a025fd3a9
ms.openlocfilehash: f9f5f62e2326826e3087a8668cd9107da4b85388
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81334998"
---
# <a name="c-multiplicative-operators"></a>Operatory mnożenia języka C

Operatory mnożenia wykonują operacje mnożenia (<strong>\*</strong>), dzielenia (**/**) i reszty (**%**).

## <a name="syntax"></a>Składnia

*mnożenia-Expression*: &nbsp; &nbsp; &nbsp; &nbsp; *cast-expression* &nbsp; &nbsp; <strong>\*</strong> &nbsp; &nbsp; **%** *cast-expression* *cast-expression* **/** *cast-expression* *multiplicative-expression* &nbsp; &nbsp; *multiplicative-expression* *multiplicative-expression* mnożenia-Expression Cast- &nbsp;Expression mnożenia &nbsp;- &nbsp;Expression cast-expression mnożenia-Expression Cast Expression &nbsp; &nbsp; &nbsp;

Operandy operatora pozostałej części (**%**) muszą być typu całkowitego. Operatory mnożenia (<strong>\*</strong>) i dzielenia (**/**) mogą przyjmować operandy typu całkowitego lub zmiennoprzecinkowego; Typy operandów mogą być różne.

Operatory mnożenia wykonują zwykle konwersje arytmetyczne dla operandów. Typ wyniku jest typem operandów po konwersji.

> [!NOTE]
> Ponieważ konwersje wykonywane przez operatory multiplikatywne nie przewidują warunków przepełnienia lub niedomiaru, informacje mogą zostać utracone, jeśli wynik operacji multiplikatywnej nie może być przedstawiony w typie operandów po konwersji.

Operatory mnożenia języka C są opisane poniżej:

|Operator|Opis|
|--------------|-----------------|
|<strong>\*</strong>|Operator mnożenia powoduje, że dwa operandy są mnożone.|
|**/**|Operator dzielenia powoduje, że pierwszy operand zostanie podzielony przez drugi. Jeśli dwa operandy całkowite są podzielone, a wynik nie jest liczbą całkowitą, zostanie obcięty zgodnie z następującymi regułami:<br/><br/>-Wynik dzielenia przez 0 jest niezdefiniowany zgodnie ze standardem ANSI C. Kompilator języka Microsoft C generuje błąd w czasie kompilacji lub czasie wykonywania.<br/><br/>— Jeśli oba operandy są dodatnie lub niepodpisane, wynik zostanie obcięty do wartości 0.<br/><br/>-Jeśli jeden z operandów jest ujemny, to wynik operacji jest największą liczbą całkowitą mniejszą lub równą ilorazowi algebraicznych lub jest najmniejszą liczbą całkowitą większą lub równą algebraicznych ilorazu jest zdefiniowana implementacja. (Zobacz poniższą sekcję dotyczącą firmy Microsoft).|
|**%**|Wynik operatora reszty jest resztą, gdy pierwszy operand jest podzielony przez drugi. Gdy podział jest niedokładny, wynik jest określany na podstawie następujących reguł:<br/><br/>-Jeśli prawy operand ma wartość zero, wynik jest niezdefiniowany.<br/><br/>— Jeśli oba operandy są dodatnie lub niepodpisane, wynik jest dodatni.<br/><br/>-Jeśli oba operandy są ujemne, a wynik jest niedokładny, wynikiem jest zdefiniowana implementacja. (Zobacz poniższą sekcję dotyczącą firmy Microsoft).|

### <a name="microsoft-specific"></a>specyficzne dla firmy Microsoft

W przypadku, gdy oba operandy są ujemne, kierunek obcinania zbliża się do 0.

Jeśli każda operacja jest ujemna w oddziale z operatorem reszty, wynik ma taki sam znak jak dzielną (pierwszy operand w wyrażeniu).

## <a name="examples"></a>Przykłady

Deklaracje przedstawione poniżej są używane w następujących przykładach:

```
int i = 10, j = 3, n;
double x = 2.0, y;
```

Ta instrukcja używa operatora mnożenia:

```
y = x * i;
```

W tym przypadku jest `x` mnożony przez `i` , aby nadać wartość 20,0. Wynik ma typ **Double** .

```
n = i / j;
```

W tym przykładzie 10 jest podzielona przez 3. Wynik zostanie obcięty do wartości 0, co daje liczbę całkowitą 3.

```
n = i % j;
```

Ta instrukcja przypisuje `n` liczbę całkowitą, 1, gdy 10 jest podzielona przez 3.

**Specyficzne dla firmy Microsoft**

Znak reszty jest taki sam jak znak dywidendy. Przykład:

```
50 % -6 = 2
-50 % 6 = -2
```

W każdym przypadku `50` i `2` mają ten sam znak.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Operatory mnożenia i operator modulo](../cpp/multiplicative-operators-and-the-modulus-operator.md)
