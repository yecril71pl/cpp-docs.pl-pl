---
title: "unary_negate — (STL/CLR) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::unary_negate
dev_langs: C++
helpviewer_keywords: unary_negate function [STL/CLR]
ms.assetid: 83bbdd86-199c-4451-9f70-72f9ade2264a
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 530a75cdebd5799e8c46fd6f8ae1f40d4f785ba6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="unarynegate-stlclr"></a>unary_negate (STL/CLR)
Klasa szablonu opisuje obiekt, który po wywołaniu zwraca logicznym nie pochodzi z jego przechowywanych argumentu jeden obiekt. Można go użyć Określ obiekt funkcja pod względem jego przechowywanych obiekt.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Fun>  
    ref class unary_negate  
    { // wrap operator()  
public:  
    typedef Fun stored_function_type;  
    typedef typename Fun::argument_type argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        argument_type, result_type>  
        delegate_type;  
  
    unary_negate(Fun% functor);  
    unary_negate(unary_negate<Fun>% right);  
  
    result_type operator()(argument_type left);  
    operator delegate_type^();  
    };  
```  
  
#### <a name="parameters"></a>Parametry  
 Fun  
 Typ przechowywanych obiekt.  
  
## <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|argument_type|Typ argumentu obiekt.|  
|delegate_type|Typ ogólny delegata.|  
|result_type|Typ wyniku obiekt.|  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|unary_negate|Tworzy obiekt.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|Operator()|Oblicza odpowiednią funkcję.|  
|delegate_type ^|Rzutuje obiekt do delegata.|  
  
## <a name="remarks"></a>Uwagi  
 Klasa szablonu opisuje obiekt jeden argument, który przechowuje inny obiekt jeden argument. Definiuje operator członkowski `operator()` tak, aby, gdy obiekt jest wywoływana w funkcji, zwraca logicznym nie pochodzi z przechowywanych obiekt wywołane z argumentem.  
  
 Można również przekazać obiekt jako argumentu funkcji, których typ jest `delegate_type^` i zostanie on przekonwertowany odpowiednio.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_unary_negate.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(0);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 0"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::logical_not<int> not_op;   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        cliext::unary_negate<cliext::logical_not<int> >(not_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        cliext::not1(not_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
4 0  
1 0  
1 0  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/funkcjonalności >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [not1 — (STL/CLR)](../dotnet/not1-stl-clr.md)