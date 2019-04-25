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
ms.openlocfilehash: fdf208ffba3e3d63d8672b84af8cf6168b34dc3f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326420"
---
# <a name="c-multiplicative-operators"></a>Operatory mnożenia języka C

Operatory multiplikatywne wykonać mnożenie (<strong>\*</strong>), dzielenie (**/**) i resztę (**%**) operacji.

## <a name="syntax"></a>Składnia

*wyrażenie mnożenia*: &nbsp; &nbsp; &nbsp; &nbsp; *wyrażenie cast* &nbsp; &nbsp; &nbsp; &nbsp; *wyrażenia mnożenia* <strong>\*</strong> *wyrażenie cast* &nbsp; &nbsp; &nbsp; &nbsp; *wyrażenia mnożenia* **/** *wyrażenie cast* &nbsp; &nbsp; &nbsp; &nbsp; *wyrażenia mnożenia* **%** *wyrażenie cast*

Argumenty operacji operatora resztę (**%**) musi być typu całkowitego. ILOCZYN (<strong>\*</strong>) i dzielenia (**/**) operatory można przyjmują operandy całkowitego lub zmiennoprzecinkowego typ -; typy argumentów mogą być różne.

Operatory multiplikatywne przeprowadzania zwykle konwersje arytmetyczne operandów. Typ wyniku jest typem operandu po konwersji.

> [!NOTE]
>  Ponieważ konwersje wykonywane przez operatory multiplikatywne nie przewidują warunków przepełnienia lub niedomiaru, informacje mogą zostać utracone, jeśli wynik operacji multiplikatywnej nie może być przedstawiony w typie operandów po konwersji.

Operatory mnożenia języka C zostały opisane poniżej:

|Operator|Opis|
|--------------|-----------------|
|<strong>\*</strong>|Operator mnożenia powoduje pomnożenie dwóch argumentów operacji.|
|**/**|Operator dzielenia powoduje, że pierwszy operand podzielony przez drugi. Jeśli dwa operandy liczby całkowitej są podzielone i nie jest liczbą całkowitą, zostanie obcięta zgodnie z następującymi zasadami:<br/><br/>-Wyniku dzielenie przez 0 jest niezdefiniowane zgodnie ze standardem ANSI C. Kompilator Microsoft C: generuje błąd w czasie kompilacji lub w czasie wykonywania.<br/><br/>— Jeśli oba operandy są dodatnie lub unsigned, wynik jest obcinana do 0.<br/><br/>— Jeśli jeden z operandów jest liczbą ujemną, wynik operacji największa liczba całkowita mniejsza niż iloraz algebraicznych czy jest to najmniejsza liczba całkowita większa lub równa algebraicznych iloraz jest definiowany przez implementację. (Zobacz poniżej sekcję Specific firmy Microsoft).|
|**%**|Wynik operator reszty jest resztę, gdy pierwszy operand jest dzielona przez drugi. Gdy podział jest niedokładny, wynik jest określany przez następujące reguły:<br/><br/>— Jeśli prawy operand jest zero, wynik jest niezdefiniowany.<br/><br/>— Jeśli oba operandy są dodatnie lub unsigned, wynik jest dodatni.<br/><br/>— Jeśli jeden z operandów jest ujemna, a wynik jest niedokładny, wynik jest definiowany przez implementację. (Zobacz poniżej sekcję Specific firmy Microsoft).|

**Microsoft Specific**

W regionie, w której jeden z operandów jest ujemna kierunku obcięcie jest kierunku 0.

Jeśli którejkolwiek z tych operacji jest ujemna działu za pomocą operatora resztę, wynik ma taki sam znak jak dzielna (pierwszego operandu w wyrażeniu).

**END specyficzny dla Microsoft**

## <a name="examples"></a>Przykłady

Deklaracje poniżej są używane w poniższych przykładach:

```
int i = 10, j = 3, n;
double x = 2.0, y;
```

Ta instrukcja używa operator mnożenia:

```
y = x * i;
```

W tym przypadku `x` jest mnożony przez `i` celu podania wartości 20.0. Wynik zawiera **double** typu.

```
n = i / j;
```

W tym przykładzie 10 jest dzielona przez 3. Wynik jest obcinana do 0, reaguje na wartość całkowitą 3.

```
n = i % j;
```

Ta instrukcja przypisuje `n` pozostałej liczby całkowitej, 1, gdy 10 jest dzielona przez 3.

**Microsoft Specific**

Znak reszta jest taka sama jak znak dzielna. Na przykład:

```
50 % -6 = 2
-50 % 6 = -2
```

W każdym przypadku `50` i `2` mają taki sam znak.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Operatory mnożenia i Operator modulo](../cpp/multiplicative-operators-and-the-modulus-operator.md)
