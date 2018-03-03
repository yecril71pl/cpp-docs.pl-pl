---
title: "__if_exists — instrukcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __if_exists_cpp
dev_langs:
- C++
helpviewer_keywords:
- identifiers, testing for existence
- symbols, testing for existence
- __if_exists keyword [C++]
ms.assetid: d3eb34b6-f3a9-4063-a286-b62a28c0c7fa
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c7950e2fcd933bd4748c06adf93f5ce1c271b162
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ifexists-statement"></a>__if_exists — Instrukcja
`__if_exists` Instrukcji sprawdza, czy istnieje określony identyfikator. Jeśli identyfikator istnieje, jest wykonywany bloku instrukcję.  
  
## <a name="syntax"></a>Składnia  
  
```  
__if_exists ( identifier ) {   
statements  
};  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`identifier`|Identyfikator istnienia, którego chcesz przetestować.|  
|`statements`|Co najmniej jeden instrukcje do wykonania, gdy `identifier` istnieje.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!CAUTION]
>  Aby osiągnąć najbardziej niezawodnym wyniki, należy użyć `__if_exists` zgodnie z następującymi ograniczeniami.  
  
-   Zastosuj `__if_exists` oświadczenie tylko proste typy, nie szablonów.  
  
-   Zastosuj `__if_exists` instrukcji do identyfikatorów wewnątrz lub na zewnątrz klasy. Nie stosuj `__if_exists` instrukcji do zmiennych lokalnych.  
  
-   Użyj `__if_exists` oświadczenie tylko w treści funkcji. Poza treści funkcji `__if_exists` instrukcji można przetestować tylko w pełni zdefiniowanych typów.  
  
-   Podczas testowania dla przeciążonej funkcji nie można przetestować wykonania określonej formy przeciążenia.  
  
 Uzupełnienie `__if_exists` instrukcja jest [__if_not_exists](../cpp/if-not-exists-statement.md) instrukcji.  
  
## <a name="example"></a>Przykład  
 Zwróć uwagę, że w tym przykładzie użyto szablonów, które nie jest zalecana.  
  
```  
// the__if_exists_statement.cpp  
// compile with: /EHsc  
#include <iostream>  
  
template<typename T>  
class X : public T {  
public:  
   void Dump() {  
      std::cout << "In X<T>::Dump()" << std::endl;  
  
      __if_exists(T::Dump) {  
         T::Dump();  
      }  
  
      __if_not_exists(T::Dump) {  
         std::cout << "T::Dump does not exist" << std::endl;  
      }  
   }     
};  
  
class A {  
public:  
   void Dump() {  
      std::cout << "In A::Dump()" << std::endl;  
   }  
};  
  
class B {};  
  
bool g_bFlag = true;  
  
class C {  
public:  
   void f(int);  
   void f(double);  
};  
  
int main() {   
   X<A> x1;  
   X<B> x2;  
  
   x1.Dump();  
   x2.Dump();  
  
   __if_exists(::g_bFlag) {  
      std::cout << "g_bFlag = " << g_bFlag << std::endl;  
   }  
  
   __if_exists(C::f) {  
      std::cout << "C::f exists" << std::endl;  
   }  
  
   return 0;  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
In X<T>::Dump()  
In A::Dump()  
In X<T>::Dump()  
T::Dump does not exist  
g_bFlag = 1  
C::f exists  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zaznaczenie — instrukcje](../cpp/selection-statements-cpp.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 [__if_not_exists, instrukcja](../cpp/if-not-exists-statement.md)