---
title: "Wyrażenia podstawowe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- primary expressions
- expressions [C++], name
- expressions [C++], literal
- expressions [C++], primary
- expressions [C++], qualified names
ms.assetid: 8ef9a814-6058-4b93-9b6e-e8eb8350b1ca
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 980be1e393fab633f3417dcc250c1820def3ff90
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="primary-expressions"></a>Wyrażenia podstawowe
Wyrażenia podstawowe są blokami konstrukcyjnymi bardziej złożonych wyrażeń. Są one literały, nazwy i nazwy kwalifikowanej przez operatora rozpoznawanie zakresów (`::`).  Wyrażenie podstawowe może mieć jedną z następujących form:  
  
```  
  
      literal  
      this  
:: namename( expression )  
```  
  
 A *literału* jest podstawowym wyrażeniem stałym. Jego typ zależy od postaci jego specyfikacji. Zobacz [literały](../cpp/numeric-boolean-and-pointer-literals-cpp.md) pełne informacje dotyczące określania literały.  
  
 **To** — słowo kluczowe jest wskaźnik do obiektu klasy. Jest on dostępny w ramach funkcji niestatycznego elementu członkowskiego i wskazuje na wystąpienie klasy, dla której wywołano funkcję. **To** poza ciałem funkcji członkowskiej klasy nie można użyć słowa kluczowego.  
  
 Typ **to** wskaźnika jest `type`  **\*const** (gdzie `type` jest nazwą klasy) w funkcjach, które nie zostały modyfikowanie **tego** wskaźnika. W poniższym przykładzie pokazano element członkowski deklaracje funkcji i typów **to**:  
  
```  
// expre_Primary_Expressions.cpp  
// compile with: /LD  
class Example  
{  
public:  
    void Func();          //  * const this  
    void Func() const;    //  const * const this  
    void Func() volatile; //  volatile * const this  
};  
```  
  
 Zobacz [ten wskaźnik](this-pointer.md) Aby uzyskać więcej informacji o modyfikowaniu typ **to** wskaźnika.  
  
 Operator rozpoznawania zakresu (`::`) następuje nazwę stanowi podstawowy wyrażenia.  Nazwy te muszą być nazwami w zakresie globalnym, a nie nazwami elementów członkowskich.  Typ tego wyrażenia zależy od deklaracji nazwy. Jest to wartość l (to znaczy, że może być wyświetlany na lewej stronie wyrażenia operatora przypisania), jeśli nazwa deklarująca to wartość l. Operator rozpoznawania zakresu umożliwia odwoływanie się do globalnej nazwy, nawet jeśli ta nazwa jest ukryta w bieżącym zakresie. Zobacz [zakres](../cpp/scope-visual-cpp.md) przykład sposobu użycia operatora rozpoznawanie zakresów.  
  
 Wyrażenie w nawiasach jest wyrażeniem podstawowym, którego typ i wartość są identyczne jak wyrażenia bez nawiasów. Jest to wartość l, jeśli wyrażenie bez nawiasów jest wartością l.  
  
 W kontekście składni wyrażenia podstawowego powyższych *nazwa* oznacza niczego w składni opisane dla [nazwy](http://msdn.microsoft.com/en-us/1c49cc24-08d5-4884-b170-ba8ed42d80db), mimo że gdy przy użyciu operatora rozpoznawanie zakresów przed nazwą typy nazw które tylko może występować w klasie jest niedozwolone.  Obejmuje to zdefiniowane przez użytkownika nazwy funkcji konwersji i nazwy destruktorów.  
  
 Przykłady wyrażeń podstawowych:  
  
```  
100 // literal  
'c' // literal  
this // in a member function, a pointer to the class instance  
::func // a global function  
::operator + // a global operator function  
::A::B // a global qualified name  
( i + 1 ) // a parenthesized expression  
```  
  
 Poniższe przykłady są wszystkie uznawane za *nazwy*i dlatego głównej wyrażenia, w różne formy:  
  
```  
MyClass // a identifier  
MyClass::f // a qualified name  
operator = // an operator function name  
operator char* // a conversion operator function name  
~MyClass // a destructor name  
A::B   // a qualified name  
A<int> // a template id  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Typy wyrażeń](../cpp/types-of-expressions.md)