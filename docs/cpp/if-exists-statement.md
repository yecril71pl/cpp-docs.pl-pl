---
title: __if_exists — instrukcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1ac866487c25ee4ce75abbebe9b9f9c2a5e97828
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405947"
---
# <a name="ifexists-statement"></a>__if_exists — Instrukcja
**__If_exists** instrukcji sprawdza, czy istnieje określony identyfikator. Jeśli istnieje identyfikator, jest wykonywany blok instrukcji określony.  
  
## <a name="syntax"></a>Składnia  
  
```  
__if_exists ( identifier ) {   
statements  
};  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|*Identyfikator*|Identyfikator, którego istnienie, którą chcesz przetestować.|  
|*Instrukcje*|Jedna lub więcej instrukcji do wykonania, jeśli *identyfikator* istnieje.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!CAUTION]
>  Aby uzyskać najbardziej niezawodnym wyniki, użyj **__if_exists** instrukcji w następujące ograniczenia.  
  
-   Zastosuj **__if_exists** instrukcję, aby tylko proste typy, nie szablonów.  
  
-   Zastosuj **__if_exists** instrukcję, aby identyfikatory wewnątrz lub na zewnątrz klasy. Nie stosuj **__if_exists** instrukcji do zmiennych lokalnych.  
  
-   Użyj **__if_exists** oświadczenie tylko w treści funkcji. Poza treści funkcji **__if_exists** instrukcji można przetestować tylko do typów w pełni zdefiniowana.  
  
-   Podczas testowania dla przeciążonych funkcji nie można przetestować określonej formy przeciążenia.  
  
 To uzupełnienie **__if_exists** instrukcja jest [__if_not_exists](../cpp/if-not-exists-statement.md) instrukcji.  
  
## <a name="example"></a>Przykład  
 Należy zauważyć, że w tym przykładzie użyto szablonów, który nie jest zalecane.  
  
```cpp 
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
  
```Output  
In X<T>::Dump()  
In A::Dump()  
In X<T>::Dump()  
T::Dump does not exist  
g_bFlag = 1  
C::f exists  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje wyboru](../cpp/selection-statements-cpp.md)   
 [Keywords](../cpp/keywords-cpp.md)   
 [__if_not_exists, instrukcja](../cpp/if-not-exists-statement.md)