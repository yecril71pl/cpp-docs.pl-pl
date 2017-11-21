---
title: 'Operatory relacyjne: &lt;, &gt;, &lt;=, i &gt;= | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- <
- '>'
dev_langs: C++
helpviewer_keywords:
- '> operator'
- less than operator
- relational operators [C++], syntax
- '>= operator'
- greater than or equal to operators [C++]
- greater than operators [C++]
- < operator
- less than or equal to operator
- <= operator
ms.assetid: d346b53d-f14d-4962-984f-89d39a17ca0f
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 25ff07e3f80d51a0bfe06ae3b1c6dc7d5728bcf0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="relational-operators-lt-gt-lt-and-gt"></a>Operatory relacyjne: &lt;, &gt;, &lt;=, i&gt;=
## <a name="syntax"></a>Składnia  
  
```  
expression < expression  
expression > expression  
expression <= expression  
expression >= expression  
```  
  
## <a name="remarks"></a>Uwagi  
 Operatory relacyjne binarne ustalić się następująco:  
  
-   Mniej niż (**\<**)  
  
-   Większa (**>**)  
  
-   Mniejsze niż lub równe (**\<=**)  
  
-   Większe lub równe (**>=**)  
  
 Operatory relacyjne mają łączność od lewej do prawej. Oba argumenty operatorów relacyjnych musi być typu arytmetycznego lub wskaźnikowego. Dają one wartości typu `bool`. Wartość zwracana jest **false** (0), jeśli relacji w wyrażeniu jest wartość FAŁSZ; w przeciwnym razie, wartość zwracana jest **true** (1).  
  
## <a name="example"></a>Przykład  
  
```  
// expre_Relational_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   cout  << "The true expression 3 > 2 yields: "  
         << (3 > 2) << endl  
         << "The false expression 20 < 10 yields: "  
         << (20 < 10) << endl;  
}  
```  
  
 Wyrażenia w poprzednim przykładzie musi być ujęta w nawiasy, ponieważ operator wstawiania strumienia (**<<**) mają wyższy priorytet niż operatory relacyjne. W związku z tym pierwsze wyrażenie bez nawiasów będzie traktowane jako:  
  
```  
(cout << "The true expression 3 > 2 yields: " << 3) < (2 << "\n");  
```  
  
 Popularne konwersje arytmetyczne objęte [konwersje standardowe](standard-conversions.md) są stosowane do argumentów operacji typu arytmetycznego.  
  
## <a name="comparing-pointers"></a>Porównywanie wskaźników  
 Gdy dwa wskaźniki do obiektów tego samego typu są porównywane, wynik zależy od lokalizacji obiektów wskazywanych w przestrzeni adresowej programu. Wskaźniki można również porównać do stałego wyrażenia, które jest szacowane na 0 lub do wskaźnika typu void *. Jeśli wskaźnik jest porównywana względem wskaźnika typu void \*, inne wskaźnika jest niejawnie przekonwertowana na typ void \*. Następnie dokonywane jest porównanie.  
  
 Nie można porównać dwóch wskaźników różnego typu, chyba że:  
  
-   Jeden typ to typ klasy pochodzącej z drugiego typu.  
  
-   Co najmniej jeden ze wskaźników jest jawnie konwertowany (rzutowany) na typ void *. (Inne wskaźnika jest niejawnie przekonwertowana na typ void \* do konwersji.)  
  
 Wynik porównania dwóch wskaźników tego samego typu, które wskazują ten sam obiekt zawsze będzie równy. Jeżeli porównywane są dwa wskaźniki do niestatycznych elementów członkowskich obiektu, obowiązują następujące zasady:  
  
-   Klasa nie jest to typ Unii, a dwa elementy członkowskie nie są rozdzielone *specyfikatora dostępu*, takich jak publicznych, chronionych lub prywatnych, wskaźnik do elementu członkowskiego zadeklarowany ostatnio zostanie porównany większa niż wskaźnika do elementu członkowskiego zadeklarowana wcześniej.  
  
-   Jeśli dwa elementy członkowskie są oddzielone *specyfikatora dostępu*, wyniki są niezdefiniowane.  
  
-   Jeśli typem klasy jest unia, wskaźniki do różnych elementów członkowskich danych w tej unii są sobie równe.  
  
 Jeśli dwa wskaźniki wskazują elementy tej samej tablicy lub na pierwszy element poza tablicą, wskaźnik do obiektu z wyższym indeksem dolnym daje większy wynik porównania. Porównanie wskaźników jest gwarantowane jako prawidłowe tylko wtedy, gdy wskaźniki dotyczą obiektów w jednej tablicy lub do pierwszej lokalizacji poza tablicą.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia z operatorami Dwuargumentowymi](../cpp/expressions-with-binary-operators.md)   
 [Operatory C++ wbudowanych, priorytet i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C relacyjnych i operatory porównania](../c-language/c-relational-and-equality-operators.md)