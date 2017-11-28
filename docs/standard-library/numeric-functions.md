---
title: '&lt;liczbowa&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- numeric/std::accumulate
- numeric/std::adjacent_difference
- numeric/std::inner_product
- numeric/std::iota
- numeric/std::partial_sum
ms.assetid: a4b0449a-c80c-4a1d-8d9f-d7fcd0058f8b
caps.latest.revision: "13"
manager: ghogen
helpviewer_keywords:
- std::accumulate [C++]
- std::adjacent_difference [C++]
- std::inner_product [C++]
- std::iota [C++]
- std::partial_sum [C++]
ms.openlocfilehash: 9b1c992930fb6b35498f04357e783d01db3a229c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltnumericgt-functions"></a>&lt;liczbowa&gt; funkcji
||||  
|-|-|-|  
|[accumulate](#accumulate)|[adjacent_difference](#adjacent_difference)|[inner_product](#inner_product)|  
|[iota](#iota)|[partial_sum](#partial_sum)|  
  
##  <a name="accumulate"></a>accumulate  
 Oblicza sumę wszystkich elementów w określonym zakresie m.in. niektóre wartości początkowej przez obliczanie sum częściowych kolejnych lub oblicza wynik kolejne wyniki częściowe podobnie uzyskany przy użyciu określonej operacji binarnych sumą.  
  
```  
template <class InputIterator, class Type>  
Type accumulate(InputIterator first, InputIterator last, Type val);

template <class InputIterator, class Type, class BinaryOperation>  
Type accumulate(
    InputIterator first, 
    InputIterator last, 
    Type val, 
    BinaryOperation binary_op);
```  
  
### <a name="parameters"></a>Parametry   
 `first`  
 Iteratora wejściowych adresowania pierwszym elementem w zakresie sumowane lub łączone zgodnie z określonym operację binarną.  
  
 `last`  
 Wejściowy iteratora adresowania ostatnim elementem w zakresie można sumowane lub łączone zgodnie z określonym operację binarną, która jest poza ostatniego elementu faktycznie częścią gromadzenia iterated o jedną pozycję.  
  
 `val`  
 Wartość początkowa, do której każdy element jest z kolei dodane lub łączyć z zgodnie z określonym operację binarną.  
  
 `binary_op`  
 Operacja pliku binarnego, która ma zostać zastosowany do każdego elementu w określony zakres oraz wynik jego poprzedniej aplikacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Suma `val` i wszystkie elementy w określonym zakresie pierwszej funkcji szablonu lub drugiej funkcji szablonu wynik zastosowania operację binarną, zamiast operacji sum, aby określić ( *PartialResult, \* ITER*), gdzie *PartialResult* jest wynikiem aplikacji poprzedniej operacji i `Iter` jest iteratora wskazuje element w zakresie.  
  
### <a name="remarks"></a>Uwagi  
 Wartość początkowa temu, że będzie wynik dobrze zdefiniowany podczas zakres jest pusta, w którym to przypadku `val` jest zwracany. Operację binarną nie musi być asocjacyjnej lub Przemienne. Wynik jest ustawiana na wartość początkową `val` , a następnie *wynik*  =  `binary_op` ( *wynik*,  **\***  `Iter`) oblicza się wielokrotnie powtarzane za pomocą zakresu, gdzie `Iter` jest iteratora wskazuje element kolejnych w zakresie. Zakres musi być prawidłowy, i złożoność jest liniowa o rozmiarze z zakresu. Typ zwracany operatora binarnego musi być możliwe do przekonwertowania na **typu** do zapewnienia podczas iteracji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// numeric_accum.cpp  
// compile with: /EHsc  
#include <vector>  
#include <numeric>  
#include <functional>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   vector <int> v1, v2(20);  
   vector <int>::iterator iter1, iter2;  
  
   int i;  
   for (i = 1; i < 21; i++)  
   {  
      v1.push_back(i);  
   }  
  
   cout << "The original vector v1 is:\n ( " ;  
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)  
      cout << *iter1 << " ";  
   cout << ")." << endl;  
  
   // The first member function for the accumulated sum  
   int total;  
   total = accumulate(v1.begin(), v1.end(), 0);  
  
   cout << "The sum of the integers from 1 to 20 is: "  
        << total << "." << endl;  
  
   // Constructing a vector of partial sums  
   int j = 0, partotal;  
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)  
   {  
      partotal = accumulate(v1.begin(), iter1 + 1, 0);  
      v2[j] = partotal;  
      j++;  
   }  
  
   cout << "The vector of partial sums is:\n ( " ;  
   for (iter2 = v2.begin(); iter2 != v2.end(); iter2++)  
      cout << *iter2 << " ";  
   cout << ")." << endl << endl;  
  
   // The second member function for the accumulated product  
   vector <int> v3, v4(10);  
   vector <int>::iterator iter3, iter4;  
  
   int s;  
   for (s = 1; s < 11; s++)  
   {  
      v3.push_back(s);  
   }  
  
   cout << "The original vector v3 is:\n ( " ;  
   for (iter3 = v3.begin(); iter3 != v3.end(); iter3++)  
      cout << *iter3 << " ";  
   cout << ")." << endl;  
  
   int ptotal;  
   ptotal = accumulate(v3.begin(), v3.end(), 1, multiplies<int>());  
  
   cout << "The product of the integers from 1 to 10 is: "  
        << ptotal << "." << endl;  
  
   // Constructing a vector of partial products  
   int k = 0, ppartotal;  
   for (iter3 = v3.begin(); iter3 != v3.end(); iter3++) {  
      ppartotal = accumulate(v3.begin(), iter3 + 1, 1, multiplies<int>());  
      v4[k] = ppartotal;  
      k++;  
   }  
  
   cout << "The vector of partial products is:\n ( " ;  
   for (iter4 = v4.begin(); iter4 != v4.end(); iter4++)  
      cout << *iter4 << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
The original vector v1 is:  
 ( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).  
The sum of the integers from 1 to 20 is: 210.  
The vector of partial sums is:  
 ( 1 3 6 10 15 21 28 36 45 55 66 78 91 105 120 136 153 171 190 210 ).  
  
The original vector v3 is:  
 ( 1 2 3 4 5 6 7 8 9 10 ).  
The product of the integers from 1 to 10 is: 3628800.  
The vector of partial products is:  
 ( 1 2 6 24 120 720 5040 40320 362880 3628800 ).  
```  
  
##  <a name="adjacent_difference"></a>adjacent_difference  
 Oblicza kolejne różnice między każdym elementem i jego poprzednikiem w zakresie wejściowym i generuje wyjściowe wyniki do zakresu docelowego lub oblicza wynik ogólnej procedury, gdzie operacja różnicy zostaje zastąpiona przez inną, określoną operację binarną.  
  
```  
template <class InputIterator, class OutIterator>  
OutputIterator adjacent_difference(
    InputIterator first, 
    InputIterator last, 
    OutputIterator result);

template <class InputIterator, class OutIterator, class BinaryOperation>  
OutputIterator adjacent_difference(
    InputIterator first, 
    InputIterator last, 
    OutputIterator result, 
    BinaryOperation binary_op);
```  
  
### <a name="parameters"></a>Parametry  
 `first`  
 Iterator danych wejściowych odnoszący się do pierwszego elementu z zakresu wejściowego, którego elementy mają być zróżnicowane z ich odpowiednimi poprzednikami lub gdzie na parze wartości ma działać inna określona operacja binarna.  
  
 `last`  
 Iterator danych wejściowych odnoszący się do ostatniego elementu z zakresu wejściowego, którego elementy mają być zróżnicowane z ich odpowiednimi poprzednikami lub gdzie na parze wartości ma działać inna określona operacja binarna.  
  
 `result`  
 Iterator danych wyjściowych odnoszący się do pierwszego elementu zakresu docelowego, gdzie ma być przechowywany szereg różnic lub wyniki określonej operacji.  
  
 `binary_op`  
 Operacja binarna, który ma być stosowana w ogólnej operacji zastępującej operację odejmowania w procedurze różnicującej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora dane wyjściowe adresowania końca zakresu docelowego: `result` + ( `last`  -  `first`).  
  
### <a name="remarks"></a>Uwagi  
 _ Iteratora dane wyjściowe *wynik* może być tego samego iteratora jako wejściowych iteratora * pierwszy, *, aby `adjacent_difference`s może być obliczane w miejscu.  
  
 Sekwencji wartości *a*1, *a*2, *a*3 zakresu wejściowego pierwszej funkcji szablonu przechowuje kolejnych **partial_difference**s *a*1, *a*2 - *a*1, a3 - *a*2, w zakresie docelowym.  
  
 Sekwencji wartości *a*1, *a*2, *a*3 wejściowych zakresu, a drugi funkcji szablonu przechowuje kolejnych **partial_difference**s *a*1, *a*2 `binary_op` *a*1, *a*3 `binary_op` *a*2 w docelowy zakres.  
  
 Operację binarną `binary_op` asocjacyjnej lub Przemienne nie jest wymagane, ponieważ dotyczy kolejność operacji jest całkowicie określony.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// numeric_adj_diff.cpp  
// compile with: /EHsc  
#include <vector>  
#include <list>  
#include <numeric>  
#include <functional>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   vector<int> V1( 10 ), V2( 10 );  
   vector<int>::iterator VIter1, VIter2, VIterend, VIterend2;  
  
   list <int> L1;  
   list <int>::iterator LIter1, LIterend, LIterend2;  
  
   int t;  
   for ( t = 1 ; t <= 10 ; t++ )  
   {  
      L1.push_back( t * t );  
   }  
  
   cout << "The input list L1 is:\n ( " ;  
   for ( LIter1 = L1.begin( ) ; LIter1 != L1.end( ) ; LIter1++ )  
      cout << *LIter1 << " ";  
   cout << ")." << endl;  
  
   // The first member function for the adjacent_differences of  
   // elements in a list output to a vector  
   VIterend = adjacent_difference ( L1.begin ( ) , L1.end ( ) ,   
      V1.begin ( ) );  
  
   cout << "Output vector containing adjacent_differences is:\n ( " ;  
   for ( VIter1 = V1.begin( ) ; VIter1 != VIterend ; VIter1++ )  
      cout << *VIter1 << " ";  
   cout << ")." << endl;  
  
   // The second member function used to compute  
   // the adjacent products of the elements in a list  
   VIterend2 = adjacent_difference ( L1.begin ( ) , L1.end ( ) , V2.begin ( ) ,   
      multiplies<int>( ) );  
  
   cout << "The output vector with the adjacent products is:\n ( " ;  
   for ( VIter2 = V2.begin( ) ; VIter2 != VIterend2 ; VIter2++ )  
      cout << *VIter2 << " ";  
   cout << ")." << endl;  
  
   // Computation of adjacent_differences in place  
   LIterend2 = adjacent_difference ( L1.begin ( ) , L1.end ( ) , L1.begin ( ) );  
   cout << "In place output adjacent_differences in list L1 is:\n ( " ;  
   for ( LIter1 = L1.begin( ) ; LIter1 != LIterend2 ; LIter1++ )  
      cout << *LIter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
##  <a name="inner_product"></a>inner_product  
 Oblicza sumę element-wise iloczyn dwóch zakresów i dodaje go do określonej wartości początkowej lub oblicza wynik uogólniony procedury, których operacji binarnych sum i produktu są zastępowane przez inne operacje określonego pliku binarnego.  
  
```  
template <class InputIterator1, class InputIterator2, class Type>  
Type inner_product(
    InputIterator1   first1, 
    InputIterator1   last1, 
    InputIterator2   first2, 
    Type             val);

template <class InputIterator1, class InputIterator2, class Type, class BinaryOperation1, class BinaryOperation2>  
Type inner_product(
    InputIterator1   first1, 
    InputIterator1   last1, 
    InputIterator2   first2, 
    Type             val, 
    BinaryOperation1  binary_op1, 
    BinaryOperation2  binary_op2);
```  
  
### <a name="parameters"></a>Parametry  
 `first1`  
 Adresowanie pierwszym elementem w pierwszego zakresu, w których wewnętrzny produktu lub uogólniony produktu wewnętrzny z drugiego zakresu jest ma zostać obliczony iteratora wejściowego.  
  
 `last1`  
 Adresowanie ostatnim elementem w pierwszego zakresu, w których wewnętrzny produktu lub uogólniony produktu wewnętrzny z drugiego zakresu jest ma zostać obliczony iteratora wejściowego.  
  
 `first2`  
 Adresowanie pierwszym elementem w drugiego zakresu, w których wewnętrzny produktu lub uogólniony produktu wewnętrzny z pierwszego zakresu jest ma zostać obliczony iteratora wejściowego.  
  
 `val`  
 Wartość początkowa, do której ma zostać dodany produktu wewnętrzny lub uogólniony produktu wewnętrzny między zakresów.  
  
 *binary_op1*  
 Operacja pliku binarnego, która zastępuje operację produktu wewnętrzny sum w stosunku do element-wise produktów w generalizacji produktu wewnętrzny.  
  
 *binary_op2*  
 Operację binarną, zastępujący produktu wewnętrzny element-wise działania należy pomnożyć w generalizacji produktu wewnętrzny.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pierwszy funkcji członkowskiej zwraca sumę element-wise produktów i dodaje do niej określona wartość początkowa. Tak dla zakresów wartości *a*i i *b*i zwraca:  
  
 `val`+ ( *a*1 \* *b*1) + ( *a*2 \* *b*2) +... + ( *a* n  \* *b*n) 
  
 Wielokrotnie powtarzane zastępując `val` z `val` + ( *a*i \* *b*i).  
  
 Zwraca funkcję drugiego elementu członkowskiego:  
  
 `val`*binary_op1* ( *a*1 *binary_op2* *b*1) *binary_op1* ( *a*2 *binary_op2* *b*2) *binary_op1* ... *binary_op1* ( *a*n *binary_op2* *b*n)  
  
 Wielokrotnie powtarzane zastępując `val` z `val` *binary_op1* ( *a*i *binary_op2* *b*i).  
  
### <a name="remarks"></a>Uwagi  
 Zapewnia to wartość początkowa będzie dobrze zdefiniowany wynik przypadku zakres jest pusta, w którym to przypadku `val` jest zwracany. Operacje danych binarnych nie trzeba asocjacyjnej lub Przemienne. Zakres musi być prawidłowy, i złożoność jest liniowa o rozmiarze z zakresu. Typ zwracany operatora binarnego musi być możliwe do przekonwertowania na **typu** do zapewnienia podczas iteracji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// numeric_inner_prod.cpp  
// compile with: /EHsc  
#include <vector>  
#include <list>  
#include <numeric>  
#include <functional>  
#include <iostream>  
  
int main()  
{  
   using namespace std;  
  
   vector <int> v1, v2(7), v3(7);  
   vector <int>::iterator iter1, iter2, iter3;  
  
   int i;  
   for (i = 1; i <= 7; i++)  
   {  
      v1.push_back(i);  
   }  
  
   cout << "The original vector v1 is:\n ( " ;  
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)  
      cout << *iter1 << " ";  
   cout << ")." << endl;  
  
   list <int> l1, l2(7);  
   list <int>::iterator lIter1, lIter2;  
  
   int t;  
   for (t = 1; t <= 7; t++)  
   {  
      l1.push_back(t);  
   }  
  
   cout << "The original list l1 is:\n ( " ;  
   for (lIter1 = l1.begin(); lIter1 != l1.end(); lIter1++)  
      cout << *lIter1 << " ";  
   cout << ")." << endl;  
  
   // The first member function for the inner product  
   int inprod;  
   inprod = inner_product(v1.begin(), v1.end(), l1.begin(), 0);  
  
   cout << "The inner_product of the vector v1 and the list l1 is: "  
        << inprod << "." << endl;  
  
   // Constructing a vector of partial inner_products between v1 & l1  
   int j = 0, parinprod;  
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++) {  
      parinprod = inner_product(v1.begin(), iter1 + 1, l1.begin(), 0);  
      v2[j] = parinprod;  
      j++;  
   }  
  
   cout << "Vector of partial inner_products between v1 & l1 is:\n ( " ;  
   for (iter2 = v2.begin(); iter2 != v2.end(); iter2++)  
      cout << *iter2 << " ";  
   cout << ")." << endl << endl;  
  
   // The second member function used to compute  
   // the product of the element-wise sums  
   int inprod2;  
   inprod2 = inner_product (v1.begin(), v1.end(),  
      l1.begin(), 1, multiplies<int>(), plus<int>());  
  
   cout << "The sum of the element-wise products of v1 and l1 is: "  
        << inprod2 << "." << endl;  
  
   // Constructing a vector of partial sums of element-wise products  
   int k = 0, parinprod2;  
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)  
   {  
      parinprod2 =  
         inner_product(v1.begin(), iter1 + 1, l1.begin(), 1,  
         multiplies<int>(), plus<int>());  
      v3[k] = parinprod2;  
      k++;  
   }  
  
   cout << "Vector of partial sums of element-wise products is:\n ( " ;  
   for (iter3 = v3.begin(); iter3 != v3.end(); iter3++)  
      cout << *iter3 << " ";  
   cout << ")." << endl << endl;  
}  
```  
  
##  <a name="iota"></a>iota  
 Przechowuje wartość początkową, zaczynając od pierwszego elementu i wypełnianie kolejne przyrosty wartości ( ` value++`) w każdym z elementów w interwale `[ first,  last)`.  
  
```  
template <class ForwardIterator, class Type>  
void iota(ForwardIterator first, ForwardIterator last, Type value);
```  
  
### <a name="parameters"></a>Parametry  
 `first`  
 Iterator wejściowych, którego dotyczy pierwszym elementem w zakresie zostać wypełnione.  
  
 `last`  
 Iterator wejściowych, którego dotyczy ostatnim elementem w zakresie zostać wypełnione.  
  
 `value`  
 Wartość początkową do przechowywania w pierwszym elementem i kolejno przyrost kolejnych elementów.  
  
### <a name="remarks"></a>Uwagi  
  
### <a name="example"></a>Przykład  
  W poniższym przykładzie pokazano niektóre zastosowania `iota` funkcja wypełniając [listy](../standard-library/list.md) liczb całkowitych i następnie wypełnianie [wektor](../standard-library/vector.md) z `list` , aby [random_ losowo](../standard-library/algorithm-functions.md#random_shuffle) funkcja może być używana.  
  
```cpp  
// compile by using: cl /EHsc /nologo /W4 /MTd  
#include <algorithm>  
#include <numeric>  
#include <list>  
#include <vector>  
#include <iostream>  
  
using namespace std;  
  
int main(void)  
{  
    list <int> intList(10);  
    vector <list<int>::iterator> intVec(intList.size());  
  
    // Fill the list  
    iota(intList.begin(), intList.end(), 0);  
  
    // Fill the vector with the list so we can shuffle it  
    iota(intVec.begin(), intVec.end(), intList.begin());  
  
    random_shuffle(intVec.begin(), intVec.end());  
  
    // Output results  
    cout << "Contents of the integer list: " << endl;  
    for (auto i: intList) {  
        cout << i << ' ';  
    }  
    cout << endl << endl;  
  
    cout << "Contents of the integer list, shuffled by using a vector: " << endl;  
    for (auto i: intVec) {  
        cout << *i << ' ';  
    }  
    cout << endl;  
}  
```  
  
##  <a name="partial_sum"></a>partial_sum  
 Oblicza szereg sum zakresu wejściowego od pierwszego elementu za pomocą *i*th element i zapisuje wynik każdego kwoty w *i*element th zakresu docelowego lub oblicza wynik gdy operacja sum zostało zastąpione przez inną operację binarną określonego uogólniony procedury.  
  
```  
template <class InputIterator, class OutIt>  
OutputIterator partial_sum(
    InputIterator first, 
    InputIterator last, 
    OutputIterator result);

template <class InputIterator, class OutIt, class Fn2>  
OutputIterator partial_sum(
    InputIterator first, 
    InputIterator last, 
    OutputIterator result, 
    BinaryOperation binary_op);
```  
  
### <a name="parameters"></a>Parametry  
 `first`  
 Iterator danych wejściowych odnoszący się do pierwszego elementu w zakresie, który ma być częściowo sumowany lub scalony według określonej operacji binarnej.  
  
 `last`  
 Iterator danych wejściowych odnoszący się do ostatniego elementu w zakresie, który ma być częściowo sumowany lub scalony według określonej operacji binarnej, znajdujący się o jedną pozycję poza ostatnim elementem faktycznie włączonym w iterowaną akumulację.  
  
 `result`  
 Iterator danych wyjściowych odnoszący się do pierwszego elementu zakresu docelowego, gdzie ma być przechowywany szereg częściowych sum lub wyniki określonej operacji.  
  
 `binary_op`  
 Operacja binarna, który ma być stosowana w ogólnej operacji zastępującej operację sumowania w procedurze częściowej sumy.    
  
### <a name="return-value"></a>Wartość zwracana  
 Iteratora dane wyjściowe adresowania końca zakresu docelowego: `result` + ( `last`  -  `first`),  
  
### <a name="remarks"></a>Uwagi  
 Dane wyjściowe iteratora `result` może być tego samego iteratora jako wejściowych iteratora `first`, dzięki czemu może można obliczyć sumy częściowe w miejscu.  
  
 Sekwencji wartości *a*1, *a*2, *a*3, zakresu wejściowego pierwszej funkcji szablonu przechowuje kolejnych sum częściowych w zakresie docelowym gdzie *i*th element jest określany przez ((( *a*1 + *a*2) + *a*3) *a*i).  
  
 Sekwencji wartości *a*1, *a*2, *a*3, zakresu wejściowego drugi funkcji szablonu przechowuje kolejnych sum częściowych w zakresie docelowym, gdzie jest wskazującego element podana przez ((( *a*1 `binary_op` *a*2) `binary_op` *a*3) *a*i).  
  
 Operację binarną `binary_op` asocjacyjnej lub Przemienne nie jest wymagane, ponieważ dotyczy kolejność operacji jest całkowicie określony.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// numeric_partial_sum.cpp  
// compile with: /EHsc  
#include <vector>  
#include <list>  
#include <numeric>  
#include <functional>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;     
   vector<int> V1( 10 ), V2( 10 );  
   vector<int>::iterator VIter1, VIter2, VIterend, VIterend2;  
  
   list <int> L1;  
   list <int>::iterator LIter1, LIterend;  
  
   int t;  
   for ( t = 1 ; t <= 10 ; t++ )  
   {  
      L1.push_back( t );  
   }  
  
   cout << "The input list L1 is:\n ( " ;  
   for ( LIter1 = L1.begin( ) ; LIter1 != L1.end( ) ; LIter1++ )  
      cout << *LIter1 << " ";  
   cout << ")." << endl;  
  
   // The first member function for the partial sums of  
   // elements in a list output to a vector  
   VIterend = partial_sum ( L1.begin ( ) , L1.end ( ) ,   
      V1.begin ( ) );  
  
   cout << "The output vector containing the partial sums is:\n ( " ;  
   for ( VIter1 = V1.begin( ) ; VIter1 != VIterend ; VIter1++ )  
      cout << *VIter1 << " ";  
   cout << ")." << endl;  
  
   // The second member function used to compute  
   // the partial product of the elements in a list  
   VIterend2 = partial_sum ( L1.begin ( ) , L1.end ( ) , V2.begin ( ) ,   
      multiplies<int>( ) );  
  
   cout << "The output vector with the partial products is:\n ( " ;  
   for ( VIter2 = V2.begin( ) ; VIter2 != VIterend2 ; VIter2++ )  
      cout << *VIter2 << " ";  
   cout << ")." << endl;  
  
   // Computation of partial sums in place  
   LIterend = partial_sum ( L1.begin ( ) , L1.end ( ) , L1.begin ( ) );  
   cout << "The in place output partial_sum list L1 is:\n ( " ;  
   for ( LIter1 = L1.begin( ) ; LIter1 != LIterend ; LIter1++ )  
      cout << *LIter1 << " ";  
   cout << ")." << endl;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<liczbowa >](../standard-library/numeric.md)

