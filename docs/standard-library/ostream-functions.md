---
title: '&lt;ostream&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ostream/std::swap
- ostream/std::endl
- ostream/std::ends
- ostream/std::flush
ms.assetid: d6e56cc0-c8df-4dbe-be10-98e14c35ed3a
caps.latest.revision: "15"
manager: ghogen
helpviewer_keywords:
- std::swap [C++]
- std::endl [C++]
- std::ends [C++]
- std::flush [C++]
ms.openlocfilehash: 252a178f1ce71c30bdd830811cbce59b22acc791
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltostreamgt-functions"></a>&lt;ostream&gt; funkcji
||||  
|-|-|-|  
|[swap](#swap)|[endl](#endl)|[kończy się](#ends)|  
|[Flush](#flush)|  
  
##  <a name="endl"></a>endl  
 Przerywa wiersza i opróżnia bufor.  
  
```  
template class<Elem, Tr> basic_ostream<Elem, Tr>& endl(basic_ostream<Elem, Tr>& Ostr);
```  
  
### <a name="parameters"></a>Parametry  
 `Elem`  
 Typ elementu.  
  
 `Ostr`  
 Obiekt typu `basic_ostream`.  
  
 `Tr`  
 Cechy znaków.  
  
### <a name="return-value"></a>Wartość zwracana  
 Obiekt typu `basic_ostream`.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania manipulatora `Ostr` **.** [put](../standard-library/basic-ostream-class.md#put)( `Ostr` **.** [widen](../standard-library/basic-ios-class.md#widen)( **"\n"**)), a następnie wywołuje `Ostr` **.** [opróżnić](../standard-library/basic-ostream-class.md#flush). Zwraca `Ostr`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// ostream_endl.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   cout << "testing" << endl;  
}  
```  
  
```Output  
testing  
```  
  
##  <a name="ends"></a>kończy się  
 Kończy się ciągiem.  
  
```  
template class<Elem, Tr> basic_ostream<Elem, Tr>& ends(basic_ostream<Elem, Tr>& Ostr);
```  
  
### <a name="parameters"></a>Parametry  
 `Elem`  
 Typ elementu.  
  
 `Ostr`  
 Obiekt typu `basic_ostream`.  
  
 `Tr`  
 Cechy znaków.  
  
### <a name="return-value"></a>Wartość zwracana  
 Obiekt typu `basic_ostream`.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania manipulatora `Ostr` **.** [put](../standard-library/basic-ostream-class.md#put)( `Elem`( **'\0'**)). Zwraca`Ostr.`  
  
### <a name="example"></a>Przykład  
  
```cpp  
// ostream_ends.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   cout << "a";  
   cout << "b" << ends;  
   cout << "c" << endl;  
}  
```  
  
```Output  
ab c  
```  
  
##  <a name="flush"></a>Flush  
 Opróżnia bufor.  
  
```  
template class<Elem, Tr> basic_ostream<Elem, Tr>& flush(basic_ostream<Elem, Tr>& Ostr);
```  
  
### <a name="parameters"></a>Parametry  
 `Elem`  
 Typ elementu.  
  
 `Ostr`  
 Obiekt typu `basic_ostream`.  
  
 `Tr`  
 Cechy znaków.  
  
### <a name="return-value"></a>Wartość zwracana  
 Obiekt typu `basic_ostream`.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania manipulatora `Ostr` **.** [opróżnić](../standard-library/basic-ostream-class.md#flush). Zwraca `Ostr`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// ostream_flush.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   cout << "testing" << flush;  
}  
```  
  
```Output  
testing  
```  
  
##  <a name="swap"></a>swap  
 Zamienia wartości dwu `basic_ostream` obiektów.  
  
```  
template <class Elem, class Tr>  
void swap(
    basic_ostream<Elem, Tr>& left,  
    basic_ostream<Elem, Tr>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `left`  
 Odwołania do wartości do `basic_ostream` obiektu.  
  
 `right`  
 Odwołania do wartości do `basic_ostream` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu `swap` wykonuje `left.swap(right)`.  
  
## <a name="see-also"></a>Zobacz też  
 [\<ostream >](../standard-library/ostream.md)

