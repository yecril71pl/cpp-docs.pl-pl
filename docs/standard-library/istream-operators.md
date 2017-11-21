---
title: '&lt;IStream&gt; operatory | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: istream/std::operator&gt;&gt;
dev_langs: C++
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 30cb2b182d8047eb1b2a5eaa384b01c719799043
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltistreamgt-operators"></a>&lt;IStream&gt; operatory
 
##  <a name="op_gt_gt"></a>operator&gt;&gt;  
 Wyodrębnia znaki i ciągi ze strumienia.  
  
```  
template <class Elem, class Tr>  
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr,   
    Elem* str);

template <class Elem, class Tr>  
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr,   
    Elem& Ch);

template <class Tr>  
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,   
    signed char* str);

template <class Tr>  
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,   
    signed char& Ch);

template <class Tr>  
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,   
    unsigned char* str);

template <class Tr>  
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,   
    unsigned char& Ch);

template <class Elem, class Tr, class Type>  
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,  
    Type& val);
```  
  
### <a name="parameters"></a>Parametry  
 `Ch`  
 Znak.  
  
 `Istr`  
 Strumień.  
  
 `str`  
 Ciąg.  
  
 `val`  
 Typ.  
  
### <a name="return-value"></a>Wartość zwracana  
 Strumień  
  
### <a name="remarks"></a>Uwagi  
 `basic_istream` Klasa definiuje również kilka operatorów wyodrębniania. Aby uzyskać więcej informacji, zobacz [basic_istream::operator >>](../standard-library/basic-istream-class.md#op_gt_gt).  
  
 Funkcja szablonu:  
  
```cpp  
template <class Elem, class Tr>  
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem* str);
```  
  
 wyodrębnia do *N* - 1 elementów i zapisuje je w tablicy, zaczynając od _ *Str*. Jeśli `Istr`. [szerokość](../standard-library/ios-base-class.md#width) jest większa od zera, *N* jest `Istr`. **szerokość**; w przeciwnym razie jest rozmiar największego tablica **elementu** mogą być deklarowane. Funkcja zawsze przechowuje wartość **Elem()** po wyodrębnieniu dowolne elementy są przechowywane. Wyodrębnianie wczesne zatrzymuje się na końcu pliku, na znak o wartości **elementu**(0) (który jest nie wyodrębnić), lub w dowolnym elemencie (który nie jest wyodrębniany), który będzie odrzucany przez [ws](../standard-library/istream-functions.md#ws). Jeśli funkcja wyodrębnia żadnych elementów, wywołuje metodę `Istr`. [Metoda setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**). W każdym przypadku wywołuje `Istr`. **szerokość**(0) i zwraca `Istr`.  
  
 **Uwaga dotycząca zabezpieczeń** ciąg znaków zakończony znakiem null, wyodrębniania ze strumienia wejściowego nie może przekraczać rozmiar buforu docelowego `str`. Aby uzyskać więcej informacji, zobacz [unikanie Overruns buforu](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
 Funkcja szablonu:  
  
```cpp  
template <class Elem, class Tr>  
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem& Ch);
```  
  
 wyodrębnia element, jeśli jest to możliwe i przechowuje ją w `Ch`. W przeciwnym razie wywołuje **jest**. [Metoda setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**). W każdym przypadku zwraca `Istr`.  
  
 Funkcja szablonu:  
  
```cpp  
template <class Tr>  
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char* str);
```  
  
 Zwraca `Istr` >> ( `char`  **\*** ) `str`.  
  
 Funkcja szablonu:  
  
```cpp  
template <class Tr>  
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char& Ch);
```  
  
 Zwraca `Istr` >> ( **char &**) `Ch`.  
  
 Funkcja szablonu:  
  
```cpp  
template <class Tr>  
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char* str);
```  
  
 Zwraca `Istr` >> ( **char \*** ) `str`.  
  
 Funkcja szablonu:  
  
```cpp  
template <class Tr>  
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char& Ch);
```  
  
 Zwraca `Istr` >> ( **char &**) `Ch`.  
  
 Funkcja szablonu:  
  
```cpp  
template <class Elem, class Tr, class Type>  
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,  
    Type& val);
```  
  
 Zwraca `Istr` `>>` `val` (i konwertuje `rvalue reference` do `Istr` do `lvalue` w procesie).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// istream_op_extract.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main( )   
{  
   ws( cin );  
   char c[10];  
  
   cin.width( 9 );  
   cin >> c;  
   cout << c << endl;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<IStream >](../standard-library/istream.md)

