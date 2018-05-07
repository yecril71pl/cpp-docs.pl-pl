---
title: Vector::Vector (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::vector::vector
dev_langs:
- C++
helpviewer_keywords:
- vector member [STL/CLR]
ms.assetid: a0b5e807-1ef2-422b-b772-1f96cd62fb51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f6921428c43ccc46b28b14523f8b17fff9185453
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="vectorvector-stlclr"></a>vector::vector (STL/CLR)
Konstruuje obiekt kontenera.  
  
## <a name="syntax"></a>Składnia  
  
```  
vector();  
vector(vector<Value>% right);  
vector(vector<Value>^ right);  
explicit vector(size_type count);  
vector(size_type count, value_type val);  
template<typename InIt>  
    vector(InIt first, InIt last);  
vector(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Parametry  
 count  
 Liczba elementów do wstawienia.  
  
 pierwszy  
 Początek zakresu do wstawienia.  
  
 ostatni  
 Koniec zakresu do wstawienia.  
  
 w prawo  
 Obiekt lub zakresu do wstawienia.  
  
 Val  
 Wartość elementu do wstawienia.  
  
## <a name="remarks"></a>Uwagi  
 Konstruktor:  
  
 `vector();`  
  
 Inicjuje kontrolowanej sekwencji z żadnych elementów. Umożliwia ona Określ pusty początkowej kontrolowanej sekwencji.  
  
 Konstruktor:  
  
 `vector(vector<Value>% right);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją [`right.begin()`, `right.end()`). Należy użyć do określenia początkowej kontrolowanej sekwencji, który jest kopią sekwencji kontrolowane przez obiekt wektora `right`.  
  
 Konstruktor:  
  
 `vector(vector<Value>^ right);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją [`right->begin()`, `right->end()`). Należy użyć do określenia początkowej kontrolowanej sekwencji, który jest kopią sekwencji kontrolowane przez obiekt wektora, którego dojście jest `right`.  
  
 Konstruktor:  
  
 `explicit vector(size_type count);`  
  
 Inicjuje kontrolowanej sekwencji z `count` elementy o wartości `value_type()`. Umożliwia ona wypełnienie elementów kontenera wszystkich mających wartość domyślną.  
  
 Konstruktor:  
  
 `vector(size_type count, value_type val);`  
  
 Inicjuje kontrolowanej sekwencji z `count` elementy o wartości `val`. Umożliwia ona wypełnienie elementów kontenera wszystkich mających taką samą wartość.  
  
 Konstruktor:  
  
 `template<typename InIt>`  
  
 `vector(InIt first, InIt last);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją [`first`, `last`). Umożliwia ona kopię kontrolowanej sekwencji innej sekwencji.  
  
 Konstruktor:  
  
 `vector(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 Inicjuje kontrolowanej sekwencji z sekwencją wskazywany przez moduł wyliczający `right`. Umożliwia ona kopię kontrolowanej sekwencji innej sekwencji opisanego przez moduł wyliczający.  
  
## <a name="example"></a>Przykład  
  
```  
// cliext_vector_construct.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
// construct an empty container   
    cliext::vector<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::vector<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::vector<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::vector<wchar_t>::iterator it = c3.end();   
    cliext::vector<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::vector<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::vector<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::vector<wchar_t> c8(%c3);   
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
 **Nagłówek:** \<cliext/wektor >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [Wektor (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Vector::ASSIGN (STL/CLR)](../dotnet/vector-assign-stl-clr.md)   
 [Vector::generic_container (STL/CLR)](../dotnet/vector-generic-container-stl-clr.md)   
 [vector::operator= (STL/CLR)](../dotnet/vector-operator-assign-stl-clr.md)