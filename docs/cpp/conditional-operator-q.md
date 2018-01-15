---
title: 'Operator warunkowy:? : | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '?:'
- '?'
dev_langs: C++
helpviewer_keywords:
- conditional operators [C++]
- '? : operator'
ms.assetid: 88643ee8-7100-4f86-880a-705ec22b6271
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 296ced0754dd12017353469845b3bc4b30e0dc11
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="conditional-operator--"></a>Operator warunkowy:? :
## <a name="syntax"></a>Składnia  
  
```  
  
expression ? expression : expression  
```  
  
## <a name="remarks"></a>Uwagi  
 Operator warunkowy (**?:**) jest trójargumentowy (ma trzy operandy). Operator warunkowy działa w następujący sposób:  
  
-   Pierwszy operand jest niejawnie konwertowany na `bool`. Zostaje oceniony i przed kontynuowaniem ukończone zostają wszystkie efekty uboczne.  
  
-   Jeśli pierwszy argument operacji daje w wyniku **true** (1), drugi operand jest obliczane.  
  
-   Jeśli pierwszy argument operacji daje w wyniku **false** (0), trzeci argument jest obliczane.  
  
 Wynik operatora warunkowego jest wynikiem w zależności od ocenianego operandu — drugiego lub trzeciego. Tylko jeden z ostatnich dwóch operandów jest oceniany w wyrażeniu warunkowym.  
  
 Wyrażenia warunkowe mają zespolenie od prawej do lewej. Pierwszy operand musi być typu całkowitego lub typu wskaźnika. Operandy drugi i trzeci mają zastosowanie następujące reguły:  
  
-   Jeśli oba argumenty operacji są tego samego typu, wynik jest tego typu.  
  
-   Jeśli oba argumenty typu arytmetycznego lub wyliczeniowego, popularne konwersje arytmetyczne (objęte [konwersje standardowe](standard-conversions.md)) są wykonywane w celu wykonania konwersji na wspólny typ.  
  
-   Jeśli obydwa argumenty operacji są typów wskaźnika lub jeśli jedna jest typem wskaźnika, a drugi to wyrażenie stałej, którego wartością 0, aby przekonwertować je na wspólny typ są wykonywane konwersje wskaźników.  
  
-   Jeśli oba argumenty typu odwołania, konwersje odwołań są wykonywane ich konwersja na wspólnego typu.  
  
-   Jeśli oba argumenty typu void, jest typu void wspólnego typu.  
  
-   Jeśli obydwa argumenty operacji są tego samego typu zdefiniowanych przez użytkownika, wspólnego typu jest tego typu.  
  
-   Jeśli argumenty mają różne typy i co najmniej jeden z argumentów ma typ zdefiniowany przez użytkownika reguł języka są używane do określenia wspólnego typu. (Zobacz poniżej ostrzeżenie).  
  
 Dowolna kombinacja drugiego i trzeciego operandu nie wymieniona na powyższej liście nie jest dozwolona. Typ wyniku jest popularnym typem i l-wartością, jeśli zarówno drugi jak i trzeci operand są tego samego typu i oba są l-wartościami.  
  
> [!WARNING]
>  Jeśli typy argumentów operacji drugi i trzeci nie są identyczne, reguły konwersji typu złożonego, jak określono w standardowym języku C++ są wywoływane. Te konwersje może prowadzić do nieoczekiwanego zachowania, łącznie z konstrukcji i niszczenie obiekty tymczasowe. Dlatego zdecydowanie zalecamy, można wybrać (1) należy unikać typy danych zdefiniowane przez użytkownika jako argumentów z operator warunkowy lub (2) Jeśli można używać typów zdefiniowanych przez użytkownika, a następnie jawne rzutowanie każdego operandu na wspólny typ.  
  
## <a name="example"></a>Przykład  
  
```  
// expre_Expressions_with_the_Conditional_Operator.cpp  
// compile with: /EHsc  
// Demonstrate conditional operator  
#include <iostream>  
using namespace std;  
int main() {  
   int i = 1, j = 2;  
   cout << ( i > j ? i : j ) << " is greater." << endl;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory C++ wbudowanych, priorytet i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operator wyrażenia warunkowego](../c-language/conditional-expression-operator.md)