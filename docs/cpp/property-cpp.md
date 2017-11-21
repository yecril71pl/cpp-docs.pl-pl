---
title: "właściwości (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: property_cpp
dev_langs: C++
helpviewer_keywords:
- property __declspec keyword
- __declspec keyword [C++], property
ms.assetid: f3b850ba-bf48-4df7-a1d6-8259d97309ce
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4c4ec1ed2351b37f88e9cb6b0ce7efd2824e431a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="property-c"></a>właściwość (C++)
**Dotyczące firmy Microsoft**  
  
 Ten atrybut można stosować do niestatycznego "danych wirtualnych elementów członkowskich" w definicji klasy lub struktury. Kompilator traktuje te "wirtualnych elementów członkowskich danych" jako elementy członkowskie danych, zmieniając ich odwołań do wywołania funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      __declspec( property( get=get_func_name ) ) declarator  
__declspec( property( put=put_func_name ) ) declarator  
__declspec( property( get=get_func_name, put=put_func_name ) ) declarator  
```  
  
## <a name="remarks"></a>Uwagi  
 Gdy kompilator widzi zadeklarowany z tym atrybutem po prawej stronie operatora wyboru elementu członkowskiego elementu członkowskiego danych ("**.**"lub"**->**"), są konwertowane na operacji **uzyskać** lub **put** funkcji, w zależności od tego, czy takie wyrażenie jest wartością l i r. Bardziej skomplikowane kontekstów, takie jak "`+=`", napisz ponownie jest wykonywane przez zastosowanie obu **uzyskać** i **put**.  
  
 Ten atrybut można także w deklaracji pustą tablicę w definicji klasy lub struktury. Na przykład:  
  
```  
__declspec(property(get=GetX, put=PutX)) int x[];  
```  
  
 Powyższe stwierdzenie wskazuje, że `x[]` może być używany z co najmniej jeden indeksy tablicy. W takim przypadku `i=p->x[a][b]` przekonwertowany `i=p->GetX(a, b)`, i `p->x[a][b] = i` są konwertowane`p->PutX(a, b, i);`  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="example"></a>Przykład  
  
```  
// declspec_property.cpp  
struct S {  
   int i;  
   void putprop(int j) {   
      i = j;  
   }  
  
   int getprop() {  
      return i;  
   }  
  
   __declspec(property(get = getprop, put = putprop)) int the_prop;  
};  
  
int main() {  
   S s;  
   s.the_prop = 5;  
   return s.the_prop;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [__declspec](../cpp/declspec.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)