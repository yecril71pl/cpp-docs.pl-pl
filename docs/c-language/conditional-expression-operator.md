---
title: Operator wyrażenia warunkowego
ms.date: 11/04/2016
helpviewer_keywords:
- conditional operators
- operators [C++], conditional
- expressions [C++], conditional
ms.assetid: c4f1a5ca-0844-44a7-a384-eca584d4e3dd
ms.openlocfilehash: 9dc93a47d36af92fe370e3f56f504682d49bd1dd
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150626"
---
# <a name="conditional-expression-operator"></a>Operator wyrażenia warunkowego

C ma jeden operator trójargumentowy: operator wyrażenia warunkowego (**?:**).

## <a name="syntax"></a>Składnia

*conditional-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie logiczne OR***?**  *wyrażenie***:***wyrażenia warunkowego*

*Wyrażenie logiczne OR* musi być typu całkowitego, zmiennoprzecinkowego lub wskaźnika. Jego jest oceniany pod względem jego odpowiednik na 0. Następuje punktu sekwencji *wyrażenie logiczne OR*. Ocena argumenty rozpoczynające się w następujący sposób:

- Jeśli *wyrażenie logiczne OR* nie jest równa 0, *wyrażenie* jest oceniany. Wynikiem obliczenia wyrażenia jest nadawana przez nieterminalnych *wyrażenie*. (Oznacza to, że *wyrażenie* jest oceniane tylko wtedy, gdy *wyrażenie logiczne OR* ma wartość true.)

- Jeśli *wyrażenie logiczne OR* jest równa 0, *wyrażenia warunkowego* jest oceniany. Wynikiem wyrażenia jest wartość *wyrażenia warunkowego*. (Oznacza to, że *wyrażenia warunkowego* jest oceniane tylko wtedy, gdy *wyrażenie logiczne OR* ma wartość false.)

Należy pamiętać, że albo *wyrażenie* lub *wyrażenia warunkowego* jest oceniana, ale nie oba.

Typ wyniku operacji warunkowych zależy od rodzaju *wyrażenie* lub *wyrażenia warunkowego* operandu w następujący sposób:

- Jeśli *wyrażenie* lub *wyrażenia warunkowego* ma całkowitego lub zmiennoprzecinkowego typu (ich typów mogą się różnić), operator wykonuje zwykle konwersje arytmetyczne. Typ wyniku jest typem operandu po konwersji.

- Jeśli oba *wyrażenie* i *wyrażenia warunkowego* mają tę samą strukturę, Unia lub typ wskaźnika, typ wyniku jest tego samego typu struktury, Unii lub wskaźnika.

- Jeśli oba operandy typu `void`, wynik ma typ `void`.

- Jeśli jeden z operandów jest wskaźnikiem do obiektu dowolnego typu, a drugi operand jest wskaźnikiem do `void`, wskaźnik do obiektu jest konwertowana na wskaźnik do `void` a wynik jest wskaźnikiem do `void`.

- Jeśli *wyrażenie* lub *wyrażenia warunkowego* jest wskaźnikiem typu, a drugi operand jest wyrażeniem stałym o wartości 0, typ wyniku jest typem wskaźnika.

W porównaniu typów dla wskaźników, dowolny typ Kwalifikatory (**const** lub `volatile`) w typie, do którego punktów wskaźnika są nieistotne, ale typ wyniku dziedziczy kwalifikatory oba składniki warunkowej.

## <a name="examples"></a>Przykłady

W poniższych przykładach pokazano przypadki użycia operatora warunkowego:

```
j = ( i < 0 ) ? ( -i ) : ( i );
```

W tym przykładzie przypisuje wartość bezwzględną liczby `i` do `j`. Jeśli `i` jest mniejszy niż 0, `-i` jest przypisany do `j`. Jeśli `i` jest większa niż lub równa 0, `i` jest przypisany do `j`.

```
void f1( void );
void f2( void );
int x;
int y;
    .
    .
    .
( x == y ) ? ( f1() ) : ( f2() );
```

W tym przykładzie dwie funkcje `f1` i `f2`, a dwie zmienne `x` i `y`, są zadeklarowane. W dalszej części programu, jeśli dwie zmienne mają taką samą wartość, funkcja `f1` jest wywoływana. W przeciwnym razie `f2` jest wywoływana.

## <a name="see-also"></a>Zobacz także

[Operator warunkowy: ? :](../cpp/conditional-operator-q.md)
