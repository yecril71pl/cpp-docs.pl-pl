---
title: Operator wyrażenia warunkowego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- conditional operators
- operators [C++], conditional
- expressions [C++], conditional
ms.assetid: c4f1a5ca-0844-44a7-a384-eca584d4e3dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f3bead2a40e38698534e433d8e4289eb8da4dc9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="conditional-expression-operator"></a>Operator wyrażenia warunkowego
C o jeden trójargumentowy: operator wyrażenia warunkowego (**?:**).  
  
## <a name="syntax"></a>Składnia  
 *wyrażenia warunkowego*:  
 *wyrażenie logiczne OR*  
  
 *wyrażenie logiczne lub***?**   *wyrażenie***:***wyrażenia warunkowego*   
  
 *Wyrażenia logicznego lub* musi mieć typ całkowitych, zmiennoprzecinkowych lub wskaźnika. Oceny pod względem jego odpowiednik na 0. Następuje punktu sekwencji *wyrażenia logicznego lub*. Ocena operandy przechodzi w następujący sposób:  
  
-   Jeśli *wyrażenia logicznego lub* nie jest równa 0, *wyrażenie* oceny. Wynik obliczania wyrażenia jest określany przez nonterminal *wyrażenia*. (Oznacza to, że *wyrażenie* jest oceniany, tylko jeśli *wyrażenia logicznego lub* ma wartość true.)  
  
-   Jeśli *wyrażenia logicznego lub* jest równe 0, *wyrażenia warunkowego* oceny. Wynikiem wyrażenia jest wartość *wyrażenia warunkowego*. (Oznacza to, że *wyrażenia warunkowego* jest oceniany, tylko jeśli *wyrażenia logicznego lub* ma wartość false.)  
  
 Należy pamiętać, że albo *wyrażenie* lub *wyrażenia warunkowego* jest obliczane, ale nie oba.  
  
 Typ wyniku operacji warunkowego zależy od typu *wyrażenie* lub *wyrażenia warunkowego* operandu w następujący sposób:  
  
-   Jeśli *wyrażenie* lub *wyrażenia warunkowego* ma typu całkowitego lub przestawne typu (typy mogą być różne), operator wykonuje popularne konwersje arytmetyczne. Typ wyniku jest typ operandy po konwersji.  
  
-   Jeśli oba *wyrażenie* i *wyrażenia warunkowego* ma tej samej struktury, Unią lub typ wskaźnika, tego samego typu struktury, Unia lub wskaźnik jest typu wyniku.  
  
-   Jeśli oba argumenty typu `void`, wynik ma typ `void`.  
  
-   Jeśli którykolwiek argument operacji jest wskaźnik do obiektu dowolnego typu, a drugiego operandu jest wskaźnik do `void`, wskaźnik do obiektu jest konwertowany na wskaźnik do `void` i wynikiem jest wskaźnik do `void`.  
  
-   Jeśli dowolny *wyrażenie* lub *wyrażenia warunkowego* wskaźnik i drugiego operandu jest wyrażenie stałe o wartości 0, typ wyniku typu wskaźnika.  
  
 Typ porównania dla wskaźników dowolny typ Kwalifikatory (**const** lub `volatile`) w typie, do którego wskaźnik wskazuje są nieistotne, ale typ wyniku dziedziczy kwalifikatory oba składniki warunkowej.  
  
## <a name="examples"></a>Przykłady  
 W poniższych przykładach pokazano używa operator warunkowy:  
  
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
  
 W tym przykładzie dwie funkcje `f1` i `f2`, a dwie zmienne `x` i `y`, został zadeklarowany. Nowsze w programie, jeśli dwie zmienne mają taką samą wartość, funkcja `f1` jest wywoływana. W przeciwnym razie `f2` jest wywoływana.  
  
## <a name="see-also"></a>Zobacz też  
 [Operator warunkowy: ? :](../cpp/conditional-operator-q.md)