---
title: list::merge (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::merge
dev_langs: C++
helpviewer_keywords: merge member [STL/CLR]
ms.assetid: f8e93cd3-bd08-4086-859b-08a2899cc9a6
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0fdf7ee26bdb465e8a86109a4450353c4dc642a0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="listmerge-stlclr"></a>list::merge (STL/CLR)
Scala dwie uporządkowane kontrolowanej sekwencji.  
  
## <a name="syntax"></a>Składnia  
  
```  
void merge(list<Value>% right);  
template<typename Pred2>  
    void merge(list<Value>% right, Pred2 pred);  
```  
  
#### <a name="parameters"></a>Parametry  
 pred  
 Moduł porównujący dla elementu pary.  
  
 w prawo  
 Kontener do scalenia w.  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy funkcji członkowskiej usuwa wszystkie elementy z sekwencji kontrolowane przez `right` i umieść je w kontrolowanej sekwencji. Zarówno sekwencji musi zostać wcześniej określona przez `operator<` — elementy nie mogą maleć wartości w czasie za pośrednictwem albo sekwencji. Wynikowa sekwencja jest również uporządkowanych według `operator<`. Ta funkcja członkowska umożliwia scalić dwóch sekwencji, które zwiększają wartość w kolejności, która zwiększa się również w wartości.  
  
 Drugi funkcji członkowskiej działa tak samo jako pierwszy, z wyjątkiem tego, że sekwencje są uporządkowane według `pred`  --  `pred(X, Y)` musi mieć wartość false dla każdego elementu `X` następujący element `Y` w sekwencji. Umożliwia ona scalić dwóch sekwencji uporządkowanych według funkcji predykatu lub delegata, który określisz.  
  
 Zarówno funkcje wykonywać stabilna scalania — nie pary elementów w jednym z oryginalnej sekwencji kontrolowane została odwrócona w wynikowej kontrolowanej sekwencji. Ponadto jeśli dwa elementy `X` i `Y` w kontrolowanej sekwencji wynikowy ma równoważne porządkowanie — `!(X < Y) && !(X < Y)` — z oryginalnego kontrolowanej sekwencji jest wyświetlany element przed elementem z sekwencji kontrolowane przez `right`.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_list_merge.cpp   
// compile with: /clr   
#include <cliext/list>   
  
typedef cliext::list<wchar_t> Mylist;   
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'c');   
    c1.push_back(L'e');   
  
// display initial contents " a c e"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    cliext::list<wchar_t> c2;   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
    c2.push_back(L'f');   
  
// display initial contents " b d f"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// merge and display   
    cliext::list<wchar_t> c3(c1);   
    c3.merge(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c2.size() = {0}", c2.size());   
  
// sort descending, merge descending, and redisplay   
    c1.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    c3.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    c3.merge(c1, cliext::greater<wchar_t>());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c1.size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a c e  
 b d f  
 a b c d e f  
c2.size() = 0  
 e c a  
 f e d c b a  
 f e e d c c b a a  
c1.size() = 0  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/listy >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [Lista (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list::sort (STL/CLR)](../dotnet/list-sort-stl-clr.md)   
 [list::splice (STL/CLR)](../dotnet/list-splice-stl-clr.md)