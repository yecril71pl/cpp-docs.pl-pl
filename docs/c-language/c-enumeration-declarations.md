---
title: Deklaracje modułów Wyliczających C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declarations, enumerations
- define directive (#define), alternative to
- enumerators, declaring
- '#define directive, alternative to'
- named constants, enumeration declarations
- declaring enumerations
ms.assetid: bd18f673-4dda-4bc1-92fd-d1ce10074910
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 697e4f37c8a59c40df80e29ff89f2021f61fb468
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389744"
---
# <a name="c-enumeration-declarations"></a>Deklaracje modułów wyliczających języka C
Wyliczenie składa się z zestawem stałe całkowite nazwanego. Deklaracja typu wyliczenia nadaje nazwę tagu — wyliczenie (opcjonalnie) i definiuje zestaw identyfikatorów całkowitą o nazwie (o nazwie "wyliczenie zestawu," "stałe modułu wyliczającego", "wyliczenia" lub "Członkowie"). Zmienna typu wyliczenia przechowuje jedną z wartości wyliczenia zestawu wynika z tego typu.  
  
 Zmienne `enum` typu można używać w wyrażeniach indeksowanie i jako argumentów wszystkich operatorów arytmetycznych. Wyliczenia alternatywną `#define` dyrektywy preprocesora z korzyści, że wartości mogą być generowane automatycznie i przestrzegać normalnych reguł zakresu.  
  
 ANSI C wyrażeń określających wartości stałej modułu wyliczającego zawsze mieć `int` typ; w związku z tym magazynu skojarzonego ze zmienną wyliczenie magazynu wymaganego przez pojedynczy `int` wartość. Można użyć stała wyliczenia lub wartość typu wyliczeniowego dowolnym języku C pozwala wyrażeniem liczby całkowitej.  
  
## <a name="syntax"></a>Składnia  
 *Specyfikator wyliczenia*:  
 **wyliczenia***identyfikator* opt **{** *listy modułu wyliczającego* **}**   
  
 **wyliczenia***identyfikator*  
  
 Opcjonalny *identyfikator* nazwy typu wyliczenia zdefiniowanych przez *modułu wyliczającego listy*. Ten identyfikator jest często nazywana "tag" określony przez listy wyliczenia. Specyfikator typu formularza  
  
```  
  
enum  
identifier  
{  
enumerator-list  
}  
  
```  
  
 deklaruje *identyfikator* jako tag wyliczenie określony przez *listy modułu wyliczającego* nonterminal. *Listy modułu wyliczającego* definiuje "zawartość modułu wyliczającego." *Listy modułu wyliczającego* jest szczegółowo opisana poniżej.  
  
 Jeśli deklaracja tag jest widoczne, kolejne deklaracje tagu, ale pominąć *listy modułu wyliczającego* Określ poprzednio zadeklarowany typ wyliczeniowy. Tag musi odwoływać się do zdefiniowanego typu wyliczenia i typu wyliczenia musi być w bieżącym zakresie. Ponieważ typ wyliczeniowy jest zdefiniowany w innym miejscu, *listy modułu wyliczającego* nie pojawia się w tej deklaracji. Deklaracje typów pochodnych wyliczeń i `typedef` deklaracje dla typów wyliczenia można zastosować tag wyliczenie przed zdefiniowaniem typem wyliczenia.  
  
## <a name="syntax"></a>Składnia  
 *Moduł wyliczający listy*:  
 *enumerator*  
  
 *Moduł wyliczający listy* **,**  `enumerator`  
  
 `enumerator`:  
 *Stała wyliczenia*  
  
 *Stała wyliczenia***=***wyrażenie stałej*  
  
 *Stała wyliczenia*:  
 *Identyfikator*  
  
 Każdy *stała wyliczenia* w *listy wyliczenia* nazwy wartości wyliczenia zestawu. Domyślnie pierwszy *stała wyliczenia* skojarzonego z wartością 0. Następne *stała wyliczenia* na liście jest skojarzony z wartością ( *wyrażenia* + 1), chyba że jawnie skojarzyć ją z inną wartość. Nazwa *stała wyliczenia* jest odpowiednikiem wartości.  
  
 Można użyć *stała wyliczenia = wyrażenie stałej* do przesłonięcia sekwencji domyślne wartości. W związku z tym jeśli *stała wyliczenia = wyrażenie stałej* pojawia się w *listy modułu wyliczającego*, *stała wyliczenia* jest skojarzona z wartości podanej przez *wyrażenia*. *Wyrażenia* musi mieć `int` wpisz i może być ujemna.  
  
 Elementy członkowskie zestawu wyliczenia mają zastosowanie następujące reguły:  
  
-   Wyliczenia mogą zawierać zduplikowanych wartości stałych. Na przykład można skojarzyć wartość 0 z dwóch różnych identyfikatorów, być może o nazwie `null` i `zero`, w tym samym zestawie.  
  
-   Identyfikatory na liście wyliczenia musi się różnić od innych identyfikatorów w tym samym zakresie z taką samą widoczność, łącznie z zwykłej nazwy zmiennych i identyfikatory w inne listy wyliczenia.  
  
-   Tagi wyliczania przestrzegać normalnych reguł zakresu. Muszą być różne od innych wyliczenia, struktury i złożenia tagi z taką samą widoczność.  
  
## <a name="examples"></a>Przykłady  
 Tych przykładach deklaracje modułów wyliczających:  
  
```  
enum DAY            /* Defines an enumeration type    */  
{  
    saturday,       /* Names day and declares a       */  
    sunday = 0,     /* variable named workday with    */   
    monday,         /* that type                      */  
    tuesday,  
    wednesday,      /* wednesday is associated with 3 */  
    thursday,  
    friday  
} workday;  
```  
  
 Wartość 0 jest skojarzony z `saturday` domyślnie. Identyfikator `sunday` jest jawnie ustawiona na 0. Domyślnie pozostałych identyfikatorów są nadawane wartości 1 do 5.  
  
 W tym przykładzie wartość z zestawu `DAY` jest przypisany do zmiennej `today`.  
  
```  
enum DAY today = wednesday;  
```  
  
 Należy pamiętać, że można przypisać wartość jest używana nazwa stałej wyliczenia. Ponieważ `DAY` typ wyliczeniowy został wcześniej zadeklarowany, tylko tag wyliczenie `DAY` jest konieczne.  
  
 Aby jawnie przypisać wartość do zmiennej wyliczany typ danych, należy użyć rzutowanie typu:  
  
```  
workday = ( enum DAY ) ( day_value - 1 );  
```  
  
 To rzutowanie jest zalecane w języku C, ale nie jest wymagana.  
  
```  
enum BOOLEAN  /* Declares an enumeration data type called BOOLEAN */  
{  
    false,     /* false = 0, true = 1 */  
    true   
};   
  
enum BOOLEAN end_flag, match_flag; /* Two variables of type BOOLEAN */  
```  
  
 Ta deklaracja można również określić jako  
  
```  
enum BOOLEAN { false, true } end_flag, match_flag;\  
```  
  
 lub jako  
  
```  
enum BOOLEAN { false, true } end_flag;  
enum BOOLEAN match_flag;  
```  
  
 Przykładem, który używa tych zmiennych może wyglądać następująco:  
  
```  
if ( match_flag == false )  
    {  
     .  
     .   /* statement */   
     .  
    }  
    end_flag = true;  
```  
  
 Również mogą być deklarowane typy danych bez nazwy modułu wyliczającego. Nazwa typu danych zostanie pominięty, ale mogą być deklarowane zmienne. Zmienna `response` jest zmienną typu zdefiniowanego:  
  
```  
enum { yes, no } response;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../cpp/enumerations-cpp.md)