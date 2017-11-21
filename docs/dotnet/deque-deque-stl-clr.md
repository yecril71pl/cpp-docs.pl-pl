---
title: deque::deque (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::deque::deque
dev_langs: C++
helpviewer_keywords: deque member [STL/CLR]
ms.assetid: e5bc9511-619e-469c-b50a-e06858e7fce7
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fc08403d0d8cf7875700ca539a3e68a0ed788104
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="dequedeque-stlclr"></a>deque::deque (STL/CLR)
Konstruuje obiekt kontenera.  
  
## <a name="syntax"></a>Składnia  
  
```  
deque();  
deque(deque<Value>% right);  
deque(deque<Value>^ right);  
explicit deque(size_type count);  
deque(size_type count, value_type val);  
template<typename InIt>  
    deque(InIt first, InIt last);  
deque(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Parametry  
 `count`  
 Liczba elementów do wstawienia.  
  
 `first`  
 Początek zakresu do wstawienia.  
  
 `last`  
 Koniec zakresu do wstawienia.  
  
 `right`  
 Obiekt lub zakresu do wstawienia.  
  
 `val`  
 Wartość elementu do wstawienia.  
  
## <a name="remarks"></a>Uwagi  
 Konstruktor:  
  
 `deque();`  
  
 Inicjuje kontrolowanej sekwencji z żadnych elementów. Umożliwia ona Określ pusty początkowej kontrolowanej sekwencji.  
  
 Konstruktor:  
  
 `deque(deque<Value>% right);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją [`right.begin()`, `right.end()`). Należy użyć do określenia początkowej kontrolowanej sekwencji, który jest kopią sekwencji kontrolowane przez obiekt deque — `right`. Aby uzyskać więcej informacji dotyczących Iteratory, zobacz [deque::begin (STL/CLR)](../dotnet/deque-begin-stl-clr.md) i [deque::end (STL/CLR)](../dotnet/deque-end-stl-clr.md).  
  
 Konstruktor:  
  
 `deque(deque<Value>^ right);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją [`right->begin()`, `right->end()`). Należy użyć do określenia początkowej kontrolowanej sekwencji, który jest kopią sekwencji kontrolowane przez obiekt deque —, których obsługa jest `right`.  
  
 Konstruktor:  
  
 `explicit deque(size_type count);`  
  
 Inicjuje kontrolowanej sekwencji z `count` elementy o wartości `value_type()`. Umożliwia ona wypełnienie elementów kontenera wszystkich mających wartość domyślną.  
  
 Konstruktor:  
  
 `deque(size_type count, value_type val);`  
  
 Inicjuje kontrolowanej sekwencji z `count` elementy o wartości `val`. Umożliwia ona wypełnienie elementów kontenera wszystkich mających taką samą wartość.  
  
 Konstruktor:  
  
 `template<typename InIt>`  
  
 `deque(InIt first, InIt last);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją [`first`, `last`). Umożliwia ona kopię kontrolowanej sekwencji innej sekwencji.  
  
 Konstruktor:  
  
 `deque(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją wskazywany przez moduł wyliczający `right`. Umożliwia ona kopię kontrolowanej sekwencji innej sekwencji opisanego przez moduł wyliczający.  
  
## <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_construct.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
// construct an empty container   
    cliext::deque<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::deque<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::deque<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::deque<wchar_t>::iterator it = c3.end();   
    cliext::deque<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::deque<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::deque<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::deque<wchar_t> c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 0 0 0  
 x x x x x x  
 x x x x x  
 x x x x x x  
 x x x x x x  
 x x x x x x  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/deque — >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [deque — (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque::ASSIGN (STL/CLR)](../dotnet/deque-assign-stl-clr.md)   
 [deque::generic_container (STL/CLR)](../dotnet/deque-generic-container-stl-clr.md)   
 [Operator = (deque —) (STL/CLR)](../dotnet/operator-assign-deque-stl-clr.md)