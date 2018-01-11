---
title: "C relacyjnych i operatory równości | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- relational operators, syntax
- equality operator
- operators [C], equality
- equality operator, syntax
- operators [C], relational
ms.assetid: c89a3815-a65e-4e0d-8333-0e8dc7fdb30b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6860198b9acce372b710e819a17f534e793f1ead
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="c-relational-and-equality-operators"></a>Operatory relacyjne i porównania języka C
Binarny relacyjnych i operatory równości porównać ich pierwszego operandu na ich drugi argument, aby sprawdzić poprawność określonej relacji. Wynik wyrażenia relacyjne to 1, jeśli testowany relacji jest true i 0, jeśli ma wartość false. Typ wyniku jest `int`.  
  
 **Składnia**  
  
 *wyrażenie relacyjne*:  
 *SHIFT — wyrażenie*  
  
 *wyrażenie relacyjne***\<***shift wyrażenie*   
  
 *wyrażenie relacyjne***>***shift wyrażenie*   
  
 *wyrażenie relacyjne***\<=***shift wyrażenie*   
  
 *wyrażenie relacyjne***>=***shift wyrażenie*   
  
 *wyrażenie równości*:  
 *wyrażenie relacyjne*  
  
 *wyrażenie równości***==***wyrażenie relacyjne*   
  
 *wyrażenie równości***! =***wyrażenie relacyjne*   
  
 Operatory relacyjne i porównania testu się następująco:  
  
|Operator|Relacja przetestowane|  
|--------------|-------------------------|  
|**\<**|Pierwszy argument operacji mniejszy od drugiego operandu|  
|**>**|Pierwszy argument operacji większy niż drugi operand|  
|**\<=**|Pierwszy argument operacji mniejsze niż lub równa do drugiego operandu|  
|**>=**|Pierwszy argument operacji większa lub równa drugiego operandu|  
|`==`|Pierwszy argument operacji równa drugiego operandu|  
|`!=`|Pierwszy argument operacji nie jest równa drugiego operandu|  
  
 Pierwsze cztery operatory w powyższej listy mają wyższy priorytet niż operatory równości (`==` i `!=`). Zapoznaj się z informacjami pierwszeństwo w tabeli [priorytet i kojarzenie operatory języka C](../c-language/precedence-and-order-of-evaluation.md).  
  
 Argumenty operacji może mieć wartości całkowitej, zmiennoprzecinkową lub wskaźnika typu. Typy argumentów operacji mogą być różne. Operatory relacyjne Wykonaj popularne konwersje arytmetyczne w wypadku argumentów operacji typu wartości całkowitych i zmiennoprzecinkowych. Ponadto można użyć następujących kombinacji typów operand z relacyjnych i operatory porównania:  
  
-   Wskaźniki do tego samego typu można zarówno argumentów operacji żadnym relacyjny lub operator równości. Pod względem równości (`==`) i nierówności (`!=`) operatorów, wynik porównania wskazuje, czy dwa wskaźniki adresów w tej samej lokalizacji pamięci. Dla innych operatory relacyjne (**\<**,  **>** ,  **\<** =, i  **>** =), względne położenie adresów pamięci dwóch obiektów wskazywał wskazuje wynik porównania. Operatory porównania tylko przesunięcia.  
  
     Porównanie wskaźników jest zdefiniowana tylko dla elementów tego samego obiektu. Jeśli wskaźniki odwołują się do elementów członkowskich w tablicy, porównanie jest odpowiednikiem porównania odpowiednich indeksów dolnych. Adres pierwszy element tablicy jest "poniżej" adres ostatnim elemencie. W przypadku struktury wskaźników do elementów członkowskich struktury zadeklarowany później jest "większe niż" wskaźników do elementów członkowskich zadeklarowanych wcześniej w strukturze. Wskaźniki do elementów członkowskich Unii tego samego są takie same.  
  
-   Wartość wskaźnika można porównać wartości stałej 0 równości (`==`) i nierówności (`!=`). Wskaźnika o wartości 0 jest nazywany wskaźnika o "wartości null"; oznacza to nie wskazuje on do lokalizacji pamięci prawidłowe.  
  
-   Operatory porównania są zgodne z regułami operatory relacyjne, ale zezwala na dodatkowe możliwości: wskaźnik można porównać wyrażenie stałe całkowite o wartości 0 lub wskaźnik do `void`. Jeśli oba wskaźniki o wartości null znajdują się w dwóch wskaźników, porównaj jako równe. Operatory porównania porównać zarówno segmentu i przesunięcie.  
  
## <a name="examples"></a>Przykłady  
 Poniższe przykłady przedstawiają relacyjne operatory równości i.  
  
```  
int x = 0, y = 0;  
if ( x < y )  
```  
  
 Ponieważ `x` i `y` są takie same, w tym przykładzie wyrażenie daje w wyniku wartość 0.  
  
```  
char array[10];  
char *p;  
  
for ( p = array; p < &array[10]; p++ )  
    *p = '\0';  
```  
  
 Każdy element ustawia fragmentu w tym przykładzie `array` stałej znak null.  
  
```  
enum color { red, white, green } col;  
   .  
   .  
   .  
   if ( col == red )  
   .  
   .  
   .  
```  
  
 Te instrukcje zadeklarować zmiennej wyliczenie o nazwie `col` znacznikiem `color`. W dowolnym momencie zmienna może zawierać wartość 0, 1 lub 2, co stanowi jeden z elementów zestawu wyliczenie `color`: kolor czerwony, biały lub zielony, odpowiednio. Jeśli `col` zawiera 0 gdy **Jeśli** instrukcja jest wykonywana, żadnych instrukcji w zależności od **Jeśli** zostaną wykonane.  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory relacyjne: \<, >, \<=, a > =](../cpp/relational-operators-equal-and-equal.md)   
 [Operatory porównania: == i !=](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)