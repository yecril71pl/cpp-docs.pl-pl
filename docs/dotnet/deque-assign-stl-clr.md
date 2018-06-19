---
title: deque::ASSIGN (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::deque::assign
dev_langs:
- C++
helpviewer_keywords:
- assign member [STL/CLR]
ms.assetid: 03fafdbb-6b10-4464-b3dc-0cc5cb8ac980
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e53bb976b854716799ced11367cf799f7ccb5cce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33108465"
---
# <a name="dequeassign-stlclr"></a>deque::assign (STL/CLR)
Zamienia wszystkie elementy.  
  
## <a name="syntax"></a>Składnia  
  
```  
void assign(size_type count, value_type val);  
template<typename InIt>  
    void assign(InIt first, InIt last);  
void assign(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Parametry  
 `count`  
 Liczba elementów do wstawienia.  
  
 `first`  
 Początek zakresu do wstawienia.  
  
 `last`  
 Koniec zakresu do wstawienia.  
  
 `right`  
 Wyliczenie do wstawienia.  
  
 `val`  
 Wartość elementu do wstawienia.  
  
## <a name="remarks"></a>Uwagi  
 Zamienia pierwszy funkcji członkowskiej kontrolowanej sekwencji powtórzenia `count` elementy wartości `val`. Umożliwia ona wypełnienie elementów kontenera wszystkich mających taką samą wartość.  
  
 Jeśli `InIt` jest typu integer, drugi funkcji członkowskiej działa tak samo jak `assign((size_type)first, (value_type)last)`. W przeciwnym razie zastępuje kontrolowanej sekwencji z sekwencją [`first`, `last`). Umożliwia ona upewnij kontrolowanej sekwencji kopii w innej sekwencji.  
  
 Trzeci funkcji członkowskiej zastępuje kontrolowanej sekwencji sekwencji wskazywany przez moduł wyliczający `right`. Umożliwia ona utworzyć kopię sekwencji opisanego przez moduł wyliczający kontrolowanej sekwencji.  
  
## <a name="example"></a>Przykład  
  
```cpp  
// cliext_deque_assign.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// assign a repetition of values   
    cliext::deque<wchar_t> c2;   
    c2.assign(6, L'x');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an iterator range   
    c2.assign(c1.begin(), c1.end() - 1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an enumeration   
    c2.assign(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
x x x x x x  
a b  
a b c  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/deque — >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [deque — (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [operator= (deque) (STL/CLR)](../dotnet/operator-assign-deque-stl-clr.md)