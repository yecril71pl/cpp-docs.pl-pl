---
title: Wyrażenia podstawowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- primary expressions
- expressions [C++], name
- expressions [C++], literal
- expressions [C++], primary
- expressions [C++], qualified names
ms.assetid: 8ef9a814-6058-4b93-9b6e-e8eb8350b1ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4356e15d1b74508b7fc2606b45b5fb2bc9a435eb
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966665"
---
# <a name="primary-expressions"></a>Wyrażenia podstawowe
Wyrażenia podstawowe są blokami konstrukcyjnymi bardziej złożonych wyrażeń. Są literały, nazwy i nazwy kwalifikowane przez operator rozpoznawania zakresu (`::`).  Wyrażenie podstawowe może mieć jedną z następujących form:  
  
```  
  
literal  
this
name  
::name ( expression )  
```  
  
 A *literału* jest podstawowym wyrażeniem stałym. Jego typ zależy od postaci jego specyfikacji. Zobacz [literały](../cpp/numeric-boolean-and-pointer-literals-cpp.md) Aby uzyskać pełne informacje na temat określania literałów.  
  
 **To** — słowo kluczowe jest wskaźnikiem do obiektu klasy. Jest on dostępny w ramach niestatycznych funkcji składowych i wskazuje na wystąpienie klasy, dla której wywołano funkcję. **To** — słowo kluczowe nie można użyć poza ciałem funkcji składowej klasy.  
  
 Typ **to** wskaźnik jest `type`  **\*const** (gdzie `type` jest nazwą klasy) w obrębie funkcji, które nie modyfikują szczególnie **to** wskaźnika. W poniższym przykładzie pokazano element członkowski w deklaracji funkcji i typów **to**:  
  
```cpp 
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
  
 Zobacz [this, wskaźnik](this-pointer.md) uzyskać więcej informacji o modyfikowaniu typu **to** wskaźnika.  
  
 Operator rozpoznawania zakresu (`::`) następuje nazwa, stanowi wyrażenie podstawowe.  Nazwy te muszą być nazwami w zakresie globalnym, a nie nazwami elementów członkowskich.  Typ tego wyrażenia zależy od deklaracji nazwy. Jest to wartość l (to znaczy, że może być wyświetlany na lewej stronie wyrażenia operatora przypisania), jeśli nazwa deklarująca to wartość l. Operator rozpoznawania zakresu umożliwia odwoływanie się do globalnej nazwy, nawet jeśli ta nazwa jest ukryta w bieżącym zakresie. Zobacz [zakres](../cpp/scope-visual-cpp.md) przykład sposobu użycia operatora rozpoznawania zakresu.  
  
 Wyrażenie w nawiasach jest wyrażeniem podstawowym, którego typ i wartość są identyczne jak wyrażenia bez nawiasów. Jest to wartość l, jeśli wyrażenie bez nawiasów jest wartością l.  
  
 Przykłady wyrażeń podstawowych:  
  
```cpp 
100 // literal  
'c' // literal  
this // in a member function, a pointer to the class instance  
::func // a global function  
::operator + // a global operator function  
::A::B // a global qualified name  
( i + 1 ) // a parenthesized expression  
```  
  
 Poniższe przykłady są wszystkie uważane za *nazwy*, a więc wyrażenia podstawowe, w różnych formach:  
  
```cpp 
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