---
title: Operator wyrażenia warunkowego
ms.date: 11/04/2016
helpviewer_keywords:
- conditional operators
- operators [C++], conditional
- expressions [C++], conditional
ms.assetid: c4f1a5ca-0844-44a7-a384-eca584d4e3dd
ms.openlocfilehash: a64317c75e48111148053cc7efb62fb5a6d79f7f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749195"
---
# <a name="conditional-expression-operator"></a>Operator wyrażenia warunkowego

C ma jeden operator trójskładnikowy: operator wyrażenia warunkowego (**? :**).

## <a name="syntax"></a>Składnia

*wyrażenie warunkowe:*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie logiczne OR*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie logiczne-OR*  **?**  *wyrażenie*  **:**  *wyrażenie warunkowe*

Wyrażenie *logiczne OR* musi mieć typ integralny, przestawny lub wskaźnik. Jest on oceniany pod względem jego równoważności do 0. Punkt sekwencji następuje *wyrażenie logiczne-OR .* Ocena operandów przebiega w następujący sposób:

- Jeśli *wyrażenie logiczne-OR* nie jest równe 0, *wyrażenie* jest oceniane. Wynik oceny wyrażenia jest podawany przez *wyrażenie*nieterminalne . (Oznacza *to,* że wyrażenie jest oceniane tylko wtedy, *gdy wyrażenie logiczne-OR* jest prawdziwe).)

- Jeśli *wyrażenie logiczne-OR* jest równe 0, obliczane jest *wyrażenie warunkowe.* Wynikiem wyrażenia jest wartość *wyrażenia warunkowego*. (Oznacza to, że *wyrażenie warunkowe* jest oceniane tylko wtedy, gdy *wyrażenie logiczne-OR* jest fałszywe).

Należy zauważyć, że *wyrażenie* lub *wyrażenie warunkowe* jest oceniane, ale nie oba.

Typ wyniku operacji warunkowej zależy od typu *wyrażenia* lub *argumentu wyrażenia warunkowego* w następujący sposób:

- Jeśli *wyrażenie* lub *wyrażenie warunkowe* ma typ integralny lub zmiennoprzecinowy (ich typy mogą być różne), operator wykonuje zwykłe konwersje arytmetyczne. Typ wyniku jest typem argumentów po konwersji.

- Jeśli zarówno *wyrażenie,* jak i *wyrażenie warunkowe* mają tę samą strukturę, unię lub typ wskaźnika, typem wyniku jest ta sama struktura, unia lub typ wskaźnika.

- Jeśli oba argumenty mają `void`typ, wynik `void`ma typ .

- Jeśli którykolwiek z operandów jest wskaźnikiem do obiektu dowolnego typu, `void`a drugi argument jest wskaźnikiem, `void` wskaźnik do obiektu jest `void`konwertowany na wskaźnik, a wynikiem jest wskaźnik do .

- Jeśli *wyrażenie* lub *wyrażenie warunkowe* jest wskaźnikiem, a drugi argument jest wyrażeniem stałym o wartości 0, typem wyniku jest typ wskaźnika.

W porównaniu typów dla wskaźników wszelkie kwalifikatory `volatile`typu **(const** lub) w typie, do którego punkty wskaźnika są nieistotne, ale typ wyniku dziedziczy kwalifikatory z obu składników warunkowego.

## <a name="examples"></a>Przykłady

Poniższe przykłady pokazują zastosowania operatora warunkowego:

```
j = ( i < 0 ) ? ( -i ) : ( i );
```

W tym przykładzie przypisuje `i` `j`wartość bezwzględną do . Jeśli `i` jest mniejsza niż `-i` 0, `j`jest przypisany do . Jeśli `i` jest większa lub równa `i` 0, `j`jest przypisana do .

```cpp
void f1( void );
void f2( void );
int x;
int y;
    .
    .
    .
( x == y ) ? ( f1() ) : ( f2() );
```

W tym przykładzie `f1` dwie `f2`funkcje i `x` , `y`i dwie zmienne i , są zadeklarowane. W dalszej części programu, jeśli dwie zmienne `f1` mają taką samą wartość, funkcja jest wywoływana. W `f2` przeciwnym razie jest wywoływana.

## <a name="see-also"></a>Zobacz też

[Operator warunkowy: ? :](../cpp/conditional-operator-q.md)
