---
title: '&lt;Tablica&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- array/std::array::get
- array/std::get
- array/std::swap
dev_langs: C++
ms.assetid: e0700a33-a833-4655-8735-16e71175efc8
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::array [C++], get
- std::get [C++]
- std::swap [C++]
ms.openlocfilehash: be5128d8a5a8d3b6d60395633122fa3dd697435e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltarraygt-functions"></a>&lt;Tablica&gt; funkcji
\<Tablicy > Nagłówek zawiera dwie funkcje niebędący elementem członkowskim, `get` i `swap`, które działają na `array` obiektów.  
  
|||  
|-|-|  
|[Pobierz](#get)|[swap](#swap)|  
  
##  <a name="get"></a>Pobierz  
Zwraca odwołanie do określonego elementu tablicy.  
  
```  
template <int Index, class T, size_t N>  
constexpr T& get(array<T, N>& arr) noexcept;  
 
template <int Index, class T, size_t N>  
constexpr const T& get(const array<T, N>& arr) noexcept;  
 
template <int Index, class T, size_t N>  
constexpr T&& get(array<T, N>&& arr) noexcept;  
```  
  
### <a name="parameters"></a>Parametry  
 `Index`  
 Przesunięcie elementu.  
  
 `T`  
 Typ elementu.  
  
 `N`  
 Liczba elementów w tablicy.  
  
 `arr`  
 Aby dokonać wyboru spośród tablicy.  
  
### <a name="example"></a>Przykład  
  
```cpp  
#include <array>   
#include <iostream>   
  
using namespace std;  
  
typedef array<int, 4> MyArray;  
  
int main()  
{  
    MyArray c0 { 0, 1, 2, 3 };  
  
    // display contents " 0 1 2 3"   
    for (const auto& e : c0)  
    {  
        cout << " " << e;  
    }  
    cout << endl;  
  
    // display odd elements " 1 3"   
    cout << " " << get<1>(c0);  
    cout << " " << get<3>(c0) << endl;  
}  
```  
  
```Output  
0 1 2 3  
1 3  
```  
  
##  <a name="swap"></a>swap  
Specjalizacja szablonu niebędący elementem członkowskim `std::swap` który zamienia dwa `array` obiektów.  
  
```  
template <class Ty, std::size_t N>  
void swap(array<Ty, N>& left, array<Ty, N>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ elementu.  
  
 `N`  
 Rozmiar tablicy.  
  
 `left`  
 Pierwszy tablicy można zamienić.  
  
 `right`  
 Drugi tablicy można zamienić.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu wykonuje `left.swap(right)`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// std__array__swap.cpp   
// compile with: /EHsc   
#include <array>   
#include <iostream>   
  
typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1 = { 4, 5, 6, 7 };
    c0.swap(c1);

    // display swapped contents " 4 5 6 7"   
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    swap(c0, c1);

    // display swapped contents " 0 1 2 3"   
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    return (0);
}
```  
  
```Output  
0 1 2 3  
4 5 6 7  
0 1 2 3  
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<Tablica >](../standard-library/array.md)

