---
title: "Wartość kategorii: Lvalues i Rvalues (Visual C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- R-values [C++]
- L-values [C++]
ms.assetid: a8843344-cccc-40be-b701-b71f7b5cdcaf
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e06dca827d6b5cb5d457a2eda6aa143bb5d0fe5e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="lvalues-and-rvalues-visual-c"></a>Lvalues i Rvalues (Visual C++)
Wyrażenie języka C++, co ma typ i który należy do *kategorii wartość*. Kategorie wartość stanowią podstawę dla reguł, które kompilatory należy wykonać podczas tworzenia, kopiowania i przenoszenia obiekty tymczasowe podczas obliczania wyrażenia. 

 C ++ 17 standardowe definiuje kategorie wartości wyrażenia w następujący sposób:

- A *glvalue* to wyrażenie, którego oceny określa tożsamości obiektu, pole bitowe lub funkcji. 
- A *prvalue bez* to wyrażenie, którego oceny inicjuje obiekt lub pola bitowego lub oblicza wartość operand operatora, jak określony przez kontekst, w którym jest wyświetlana. 
- *Xvalue* jest glvalue, który wskazuje obiekt lub pola bitowego, którego zasoby mogą być ponownie używane (zazwyczaj, ponieważ jest pod koniec okresu jego istnienia). [Przykład: xvalues, takie jak wywołania funkcji, których typem zwracanym jest odwołanie do r-wartości lub Rzutowanie na typ referencyjny wartościowany prawostronnie yield niektóre rodzaje wyrażeń zawierających odwołania do r-wartości (8.3.2). ] 
- *L-wartością* jest glvalue, który nie jest xvalue. 
- *Prawostronnie* prvalue bez lub xvalue. 

Na poniższym diagramie przedstawiono relacje między kategorie:

 ![Kategorie wartość wyrażeń C++](media/value_categories.png "kategorie wartość wyrażeń języka C++")  
 
 L-wartością ma adres, który można uzyskać dostępu do programu. Wyrażenia l-wartością przykłady nazwy zmiennych, łącznie z `const` zmiennych, elementów tablicy funkcji wywołania, które zwracają odwołania do wartości pola bitowe, Unii i elementów członkowskich klasy. 
 
 Wyrażenie prvalue bez nie ma adresu, który jest dostępny dla programu. Przykładami prvalue bez wyrażeń literałów, wywołania funkcji, które zwracany typ innych niż odwołanie i tymczasowe obiekty, które są tworzone podczas evalution wyrażenie, ale dostępna tylko przez kompilator. 

 Wyrażenie wartości x nie ma adresu, ale można zainicjować odwołania do r-wartości, która zapewnia dostęp do wyrażenia. Przykłady obejmują wywołania funkcji, które zwracają odwołania do r-wartości i indeks dolny tablicy, element członkowski i wskaźnika do wyrażeń elementów członkowskich gdzie odwołania do r-wartości jest tablicą ani obiektem. 
 
 W poniższym przykładzie pokazano kilka poprawne i niepoprawne użycia lvalues i rvalues:  
  
```  
// lvalues_and_rvalues2.cpp  
int main()  
{  
   int i, j, *p;  
  
   // Correct usage: the variable i is an lvalue and the literal 7 is a prvalue.  
   i = 7;  
  
   // Incorrect usage: The left operand must be an lvalue (C2106).  `j * 4` is a prvalue.
   7 = i; // C2106  
   j * 4 = 7; // C2106  
  
   // Correct usage: the dereferenced pointer is an lvalue.  
   *p = i;   
  
   const int ci = 7;  
   // Incorrect usage: the variable is a non-modifiable lvalue (C3892).  
   ci = 9; // C3892  
  
   // Correct usage: the conditional operator returns an lvalue.  
   ((i < 3) ? i : j) = 7;  
}  
```  
  
> [!NOTE]
>  Przykłady w tym temacie przedstawiono poprawne i niepoprawne użycie, gdy nie są przeciążone operatory. Przez przeładowanie operatorów, możesz wprowadzić wyrażenia takie jak `j * 4` l-wartością.  

  
 Warunki *l-wartością* i *r-wartości* są często używane w przypadku odwoływania się do odwołania do obiektów. Aby uzyskać więcej informacji o odwołaniach, zobacz [deklarator odwołania do l-wartością: &](../cpp/lvalue-reference-declarator-amp.md) i [deklarator odwołania do r-wartości: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe pojęcia](../cpp/basic-concepts-cpp.md)   
 [Deklarator odwołania do wartości: &](../cpp/lvalue-reference-declarator-amp.md)   
 [Deklarator odwołania do wartości R: &&](../cpp/rvalue-reference-declarator-amp-amp.md)