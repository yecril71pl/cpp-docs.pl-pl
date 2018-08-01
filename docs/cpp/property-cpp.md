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
ms.openlocfilehash: c4673101d41b896ed3fc19aa1998aa9329064b41
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408609"
---
# <a name="property-c"></a>właściwość (C++)
**Microsoft Specific**  
  
 Ten atrybut można stosować do niestatycznych "elementy członkowskie danych wirtualnej" w definicji klasy lub struktury. Kompilator traktuje te "wirtualnych elementów członkowskich danych" jako elementy członkowskie danych, zmieniając ich odwołań do wywołania funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
   __declspec( property( get=get_func_name ) ) declarator  
   __declspec( property( put=put_func_name ) ) declarator  
   __declspec( property( get=get_func_name, put=put_func_name ) ) declarator  
```  
  
## <a name="remarks"></a>Uwagi  
 Gdy kompilator będzie widział element członkowski danych zadeklarowana za pomocą tego atrybutu po prawej stronie operatora wyboru składowej ("**.**"or"**->**"), konwertuje operacji `get` lub `put` funkcji, w zależności od tego, czy takie wyrażenie jest wartością l i r-wartości. Bardziej skomplikowane kontekstach, takich jak "`+=`", nadpisania odbywa się przez zastosowanie obu podejść `get` i `put`.  
  
 Ten atrybut umożliwia także w deklaracji pustą tablicę w definicji klasy lub struktury. Na przykład:  
  
```cpp 
__declspec(property(get=GetX, put=PutX)) int x[];  
```  
  
 Powyższe stwierdzenie wskazuje, że `x[]` mogą być używane z co najmniej jeden indeksy tablicy. W tym przypadku `i=p->x[a][b]` będą przekształcane w `i=p->GetX(a, b)`, i `p->x[a][b] = i` będą przekształcane w `p->PutX(a, b, i);`  
  
 **END specyficzny dla Microsoft**  
  
## <a name="example"></a>Przykład  
  
```cpp 
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
  
## <a name="see-also"></a>Zobacz także  
 [__declspec](../cpp/declspec.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)