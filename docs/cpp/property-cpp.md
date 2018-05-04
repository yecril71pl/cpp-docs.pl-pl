---
title: właściwości (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- property_cpp
dev_langs:
- C++
helpviewer_keywords:
- property __declspec keyword
- __declspec keyword [C++], property
ms.assetid: f3b850ba-bf48-4df7-a1d6-8259d97309ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a791615f7fd91a7ccfcda45b23fc524ebd9b6400
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="property-c"></a>właściwość (C++)
**Microsoft Specific**  
  
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
  
 Powyższe stwierdzenie wskazuje, że `x[]` może być używany z co najmniej jeden indeksy tablicy. W takim przypadku `i=p->x[a][b]` przekonwertowany `i=p->GetX(a, b)`, i `p->x[a][b] = i` są konwertowane `p->PutX(a, b, i);`  
  
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