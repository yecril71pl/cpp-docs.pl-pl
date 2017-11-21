---
title: "Parametrów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- arguments [C++], function
- function parameters
- parameters [C++]
- function arguments, vs. parameters
- parameters [C++], function
- functions [C], parameters
- function parameters, syntax
- ellipses (...), parameters
- '... ellipsis'
ms.assetid: 8f2b8026-78b5-4e21-86a3-bf0f91f05689
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 93e3b33e6e5e9eee52ec08eac32c47bf0ae6213f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="parameters"></a>Parametry
Argumenty są nazwy wartości przekazanych do funkcji według wywołania funkcji. Parametry są wartościami, które Funkcja spodziewa się otrzymywać. W prototypu funkcji nawiasów po nazwie funkcji zawiera pełną listę parametrów funkcji i ich typów. Deklaracji parametru określić typy, rozmiarów i identyfikatory wartości przechowywanych w parametrach.  
  
## <a name="syntax"></a>Składnia  
 *Definicja funkcji*:  
 *Specyfikatory deklaracji* opt*seq atrybutu* opt*lista deklaracji deklarator* opt*złożonej instrukcji*  
  
 /\**seq atrybutu* jest Specific Microsoft * /  
  
 *deklarator* :  
 *wskaźnik* opt*bezpośrednio deklarator*  
  
 *deklarator bezpośrednio*:/\* deklarator funkcji\*/  
 *deklarator bezpośrednio***(***listy parametrów typu***)** / * nowy styl deklarator      \*/  
  
 *listy parametrów typu*: /\* listy parametrów\*/  
 *listy parametrów*  
  
 *Lista parametrów***,...**   
  
 *Lista parametrów*:  
 *Deklaracja parametru*  
  
 *Lista parametrów***,***deklaracji parametru*   
  
 *Deklaracja parametru*:  
 *Specyfikatory deklaracji deklarator*  
  
 *Specyfikatory deklaracji abstrakcyjny — deklarator* opcjonalnych  
  
 *Listy parametrów typu* jest sekwencją liczb rozdzielonych przecinkami deklaracji parametrów. Formularz każdego parametru na liście parametrów wygląda następująco:  
  
```  
[register]  type-specifier [declarator]   
```  
  
 Parametry funkcji zadeklarowana z **automatycznie** atrybutu generować błędy. Identyfikatory parametry są używane w treści funkcji do odwoływania się do wartości przekazanych do funkcji. Można określić nazwę parametrów w prototyp, ale nazwy się znaleźć poza zakresem na końcu deklaracji. W związku z tym nazwy parametrów można przypisać taki sam sposób lub w inny sposób w definicji funkcji. Te identyfikatory nie można ponownie zdefiniować w najbardziej zewnętrznej bloku treści funkcji, ale można je w blokach wewnętrznej, zagnieżdżonej tak, jakby listy parametrów były w otaczającym bloku.  
  
 Każdy identyfikator w *listy parametrów typu* musi być poprzedzona jego specyfikator odpowiedniego typu, jak pokazano w poniższym przykładzie:  
  
```  
void new( double x, double y, double z )  
{  
    /* Function body here */  
}  
```  
  
 Jeśli co najmniej jeden parametr występuje na liście parametrów, listy może kończyć się przecinek następują trzy kropki (**,...** ). Ta konstrukcja o nazwie "wielokropka notacji," wskazuje zmienna liczba argumentów funkcji. (Zobacz [wywołania ze zmienną liczbą argumentów](../c-language/calls-with-a-variable-number-of-arguments.md) Aby uzyskać więcej informacji.) Jednak wywołanie funkcji musi mieć co najmniej tyle argumenty są parametry przed ostatnim przecinkiem.  
  
 Jeśli ma być przekazany do funkcji bez argumentów, lista parametrów zastępuje słowa kluczowego `void`. To `void` różni się od jako specyfikatora typu.  
  
 Kolejność i typ parametrów, takich jak jakimkolwiek użyciem notacji wielokropka musi być taka sama w wszystkie deklaracje funkcji (jeśli istnieje) i definicji funkcji. Typy argumentów po popularne konwersje arytmetyczne musi być zgodny z przypisania z typami odpowiednich parametrów. (Zobacz [popularne konwersje arytmetyczne](../c-language/usual-arithmetic-conversions.md) uzyskać informacji o konwersje arytmetyczne.) Argumenty następujących wielokropka nie są sprawdzane. Parametr może mieć żadnych podstawowe, struktury, złożenia, wskaźnik, lub typu tablicy.  
  
 Kompilator niezależnie wykonuje popularne konwersje arytmetyczne dla każdego parametru i na każdy argument w razie potrzeby. Po konwersji nie parametru jest krótszy niż `int`, i żaden parametr nie ma **float** typu, chyba że jako określony typ parametru jest jawnie **float** w prototypu. Oznacza to, na przykład deklarowanie parametrów jako `char` ma ten sam efekt co deklarowanie go jako `int`.  
  
## <a name="see-also"></a>Zobacz też  
 [Definicje funkcji języka C](../c-language/c-function-definitions.md)