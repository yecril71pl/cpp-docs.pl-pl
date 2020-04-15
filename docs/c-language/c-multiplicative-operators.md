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

Operatory mnożenia wykonują<strong>\*</strong>mnożenie ( ), podział (**/**) i pozostałe (**%**) operacje.

## <a name="syntax"></a>Składnia

*multiplicative-expression* &nbsp; &nbsp; &nbsp; &nbsp;: *wyrażenie rzutowania* &nbsp; &nbsp; &nbsp; &nbsp; *mnożenie-wyrażenie* <strong>\*</strong> *rzutowania-wyrażenie* &nbsp; &nbsp; &nbsp; &nbsp; *mnożenie-wyrażenie* **/** *rzutowania-wyrażenie* &nbsp; &nbsp; &nbsp; &nbsp; *mnożenie-wyrażenie* **%** *rzutowania*

Argumenty pozostałego operatora (**%**) muszą być integralną częścią. Operatory mnożenia<strong>\*</strong>(**/**) i podziału ( ) mogą przyjmować operandy typu integralnego lub pływającego; typy operandów mogą być różne.

Operatory mnożenia wykonują zwykłe konwersje arytmetyczne na operandach. Typ wyniku jest typem argumentów po konwersji.

> [!NOTE]
> Ponieważ konwersje wykonywane przez operatory multiplikatywne nie przewidują warunków przepełnienia lub niedomiaru, informacje mogą zostać utracone, jeśli wynik operacji multiplikatywnej nie może być przedstawiony w typie operandów po konwersji.

Operatory mnożenia C są opisane poniżej:

|Operator|Opis|
|--------------|-----------------|
|<strong>\*</strong>|Operator mnożenia powoduje, że jego dwa argumenty mają zostać pomnożone.|
|**/**|Operator podziału powoduje, że pierwszy operand być podzielone przez drugi. Jeśli dwie liczby całkowite są podzielone, a wynik nie jest całkowitej liczby, jest obcinane zgodnie z następującymi regułami:<br/><br/>- Wynik podziału o 0 jest nieokreślony zgodnie ze standardem ANSI C. Kompilator Microsoft C generuje błąd w czasie kompilacji lub czasie wykonywania.<br/><br/>- Jeśli oba argumenty są dodatnie lub niepodpisane, wynik jest obcinany w kierunku 0.<br/><br/>- Jeśli albo operand jest ujemny, czy wynik operacji jest największą liczeczką całkowitą mniejszą lub równą ilorazowi algebraicznego, czy też jest najmniejszą liczą całkowitą większą lub równą ilorazowi algebraicznego jest zdefiniowana implementacja. (Zobacz sekcję specyficzną dla firmy Microsoft poniżej).|
|**%**|Wynik pozostałego operatora jest pozostałą częścią, gdy pierwszy operand jest podzielony przez drugi. Gdy podział jest niedokładny, wynik jest określany przez następujące zasady:<br/><br/>- Jeśli prawy operand wynosi zero, wynik jest nieokreślony.<br/><br/>- Jeśli oba argumenty są dodatnie lub niepodpisane, wynik jest pozytywny.<br/><br/>- Jeśli którykolwiek z operand jest ujemny, a wynik jest niedokładny, wynik jest zdefiniowany implementacji. (Zobacz sekcję specyficzną dla firmy Microsoft poniżej).|

### <a name="microsoft-specific"></a>specyficzne dla firmy Microsoft

W podziale, gdzie albo operand jest ujemny, kierunek obcinania jest w kierunku 0.

Jeśli którakolwiek z operacji jest ujemna w podziale z operatorem pozostałej, wynik ma ten sam znak co dywidenda (pierwszy argument w wyrażeniu).

## <a name="examples"></a>Przykłady

Poniższe deklaracje są używane dla następujących przykładów:

```
int i = 10, j = 3, n;
double x = 2.0, y;
```

Ta instrukcja używa operatora mnożenia:

```
y = x * i;
```

W takim `x` przypadku jest `i` mnożona przez podać wartość 20,0. Wynik ma **podwójny** typ.

```
n = i / j;
```

W tym przykładzie 10 jest dzielona przez 3. Wynik jest obcinany w kierunku 0, dając wartość całkowitą 3.

```
n = i % j;
```

Ta instrukcja `n` przypisuje pozostałą część całkowitą, 1, gdy 10 jest podzielony przez 3.

**Specyficzne dla firmy Microsoft**

Znak pozostałej części jest taki sam jak znak dywidendy. Przykład:

```
50 % -6 = 2
-50 % 6 = -2
```

W każdym `50` przypadku `2` i mają ten sam znak.

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[Operatory mnożenia i operator modułu](../cpp/multiplicative-operators-and-the-modulus-operator.md)
