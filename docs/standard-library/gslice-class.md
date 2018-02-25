---
title: "gslice — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- valarray/std::gslice
- valarray/std::gslice::size
- valarray/std::gslice::start
- valarray/std::gslice::stride
dev_langs:
- C++
helpviewer_keywords:
- std::gslice [C++]
- std::gslice [C++], size
- std::gslice [C++], start
- std::gslice [C++], stride
ms.assetid: f47cffd0-ea59-4b13-848b-7a5ce1d7e2a3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 75dd4e6b4745bbf710541ecc423c3a01b46fc119
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="gslice-class"></a>gslice — Klasa
Klasa narzędzia valarray —, który służy do definiowania wielowymiarowe podzbiór valarray —. Jeśli valarray — jest traktowany jako macierz wielowymiarowe z wszystkich elementów w tablicy, wycinka wyodrębnia wektor poza tablicy wielowymiarowej.  
  
## <a name="remarks"></a>Uwagi  
 Klasa przechowuje parametry, charakteryzujące typu obiektu [gslice_array —](../standard-library/gslice-array-class.md). Podzbiór valarray — pośrednio jest tworzony, gdy obiekt gslice — klasa zostanie wyświetlony jako argument dla obiekt klasy [valarray —](../standard-library/valarray-class.md#op_at)**\<typu >**. Przechowywane wartości, które określają podzestawu wybrany z valarray — nadrzędnego obejmują:  
  
-   Indeks początkowy.  
  
-   Długość wektora klasy **valarray — < size_t >**.  
  
-   Wektor stride klasy **valarray — < size_t >**.  
  
 Dwa wektory musi mieć taką samą długość.  
  
 Zestaw zdefiniowanych przez gslice — w przypadku podzbiór stałej valarray —, gslice — to nowy valarray —. Jeśli zestaw zdefiniowanych przez gslice — podzbiór nieunikatowego valarray —, gslice — ma semantykę odwołania do oryginalnego valarray —. Mechanizm oceny nieunikatowego valarrays oszczędza czas i pamięci.  
  
 Operacje na valarrays dotrą tylko wtedy, gdy pliki źródłowe i docelowe zdefiniowane przez gslices są unikatowe i wszystkich indeksów są prawidłowe.  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[gslice](#gslice)|Definiuje ona podzestaw `valarray` składający się z wielu wycinków `valarray` wszystkie rozpoczęli określonego elementu.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[Rozmiar](#size)|Wyszukuje wartości tablicy określenie liczby elementów w ogólne wycinek `valarray`.|  
|[start](#start)|Znajduje indeks początkowy ogólne wycinek `valarray`.|  
|[stride](#stride)|Odległość między elementami w ogólne wycinek `valarray`.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<valarray — >  
  
 **Namespace:** Standard  
  
##  <a name="gslice"></a>  gslice::gslice  
 Klasa narzędzia valarray —, który służy do definiowania wielowymiarowych wycinków valarray —.  
  
```  
gslice();

gslice(
    size_t _StartIndex,  
    const valarray<size_t>& _LenArray,  
    const valarray<size_t>& _IncArray);
```  
  
### <a name="parameters"></a>Parametry  
 `_StartIndex`  
 Valarray — indeks pierwszego elementu w podzbiorze.  
  
 `_LenArray`  
 Tablica określająca liczbę elementów w każdej wycinka.  
  
 `_IncArray`  
 Tablica określania krok na każdy wycinek.  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślny konstruktor przechowuje zera indeks początkowy i wektorów o zerowej długości dla wektory długość i krok. Drugi Konstruktor magazynów `_StartIndex` początkowy indeks `_LenArray` dla tablicy o długości i `_IncArray` dla tablicy krok.  
  
### <a name="remarks"></a>Uwagi  
 **gslice —** definiuje podzbiór valarray —, która składa się z wielu wycinków valarray — czy rozpoczyna w tym samym określony element. Możliwość używania tablic do definiowania wielu wycinków jest jedyną różnicą między `gslice` i [slice::slice](../standard-library/slice-class.md#slice). Pierwszy wycinek jest pierwszym elementem o numerze indeksu `_StartIndex`, liczba elementów określonych przez pierwszy element `_LenArray`i stride przez pierwszy element `_IncArray`. Następny zestaw prostopadły wycinków ma pierwszych elementów przez pierwszego wycinka. Drugi element `_LenArray` określa liczbę elementów. Krok jest określany przez drugiego elementu `_IncArray`. Wymiar innych wycinków może potrwać elementy tablicą dwuwymiarową jako początkowy elementy i kontynuować analogously  
  
### <a name="example"></a>Przykład  
  
```cpp  
// gslice_ctor.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> va ( 20 ), vaResult;  
   for ( i = 0 ; i < 20 ; i+=1 )   
      va [ i ] =  i;  
  
   cout << "The operand valarray va is:" << endl << "(";  
   for ( i = 0 ; i < 20 ; i++ )  
      cout << " " << va [ i ];  
   cout << " )" << endl;  
  
   valarray<size_t> Len ( 2 ), Stride ( 2 );  
   Len [0] = 4;  
   Len [1] = 4;  
   Stride [0] = 7;  
   Stride [1] = 4;  
  
   gslice vaGSlice ( 0, Len, Stride );  
   vaResult = va [ vaGSlice ];  
  
   cout << "The valarray for vaGSlice is vaResult:" << endl  
        << "va[vaGSlice] = (";  
  
   for ( i = 0 ; i < 8 ; i++ )  
      cout << " " << vaResult [ i ];  
   cout << ")" << endl;  
}  
```  
  
```Output  
The operand valarray va is:  
( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 )  
The valarray for vaGSlice is vaResult:  
va[vaGSlice] = ( 0 4 8 12 7 11 15 19)  
```  
  
##  <a name="size"></a>  gslice::size  
 Umożliwia znalezienie określenie liczby elementów w ogólne wycinek valarray — wartości tablicy.  
  
```  
valarray<size_t> size() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Valarray — Określanie liczby elementów w każdej wycinek ogólne wycinek valarray —.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca przechowywanych długości wycinków.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// gslice_size.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   size_t sizeVA;  
  
   valarray<int> va ( 20 ), vaResult;  
   for ( i = 0 ; i < 20 ; i+=1 )  
      va [ i ] =  i;  
  
   cout << "The operand valarray va is:\n ( ";  
      for ( i = 0 ; i < 20 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
  
   sizeVA = va.size ( );  
   cout << "The size of the valarray is: "  
        << sizeVA << "." << endl << endl;  
  
   valarray<size_t> Len ( 2 ), Stride ( 2 );  
   Len [0] = 4;  
   Len [1] = 4;  
   Stride [0] = 7;  
   Stride [1] = 4;  
  
   gslice vaGSlice ( 0, Len, Stride );  
   vaResult = va [ vaGSlice ];  
   const valarray <size_t> sizeGS = vaGSlice.size ( );  
  
   cout << "The valarray for vaGSlice is vaResult:"  
        << "\n va[vaGSlice] = ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaResult [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The size of vaResult is:"  
        << "\n vaGSlice.size ( ) = ( ";  
      for ( i = 0 ; i < 2 ; i++ )  
         cout << sizeGS[ i ] << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
The operand valarray va is:  
 ( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ).  
The size of the valarray is: 20.  
  
The valarray for vaGSlice is vaResult:  
 va[vaGSlice] = ( 0 4 8 12 7 11 15 19 ).  
The size of vaResult is:  
 vaGSlice.size ( ) = ( 4 4 ).  
```  
  
##  <a name="start"></a>  gslice::Start  
 Znajduje indeks początkowy ogólne wycinek valarray —.  
  
```  
size_t start() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks początkowy ogólne wycinek valarray —.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// gslice_start.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> va ( 20 ), vaResult;  
   for (i = 0 ; i < 20 ; i+=1 )  
      va [ i ] =  i;  
  
   cout << "The operand valarray va is:\n ( ";  
      for ( i = 0 ; i < 20 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
  
   valarray<size_t> Len ( 2 ), Stride ( 2 );  
   Len [0] = 4;  
   Len [1] = 4;  
   Stride [0] = 7;  
   Stride [1] = 4;  
  
   gslice vaGSlice ( 0, Len, Stride );  
   vaResult = va [ vaGSlice ];  
   size_t vaGSstart = vaGSlice.start ( );  
  
   cout << "The valarray for vaGSlice is vaResult:"  
        << "\n va[vaGSlice] = ( ";  
      for (i = 0 ; i < 8 ; i++ )  
         cout << vaResult [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The index of the first element of vaResult is: "  
        << vaGSstart << "." << endl;  
}  
```  
  
```Output  
The operand valarray va is:  
 ( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ).  
The valarray for vaGSlice is vaResult:  
 va[vaGSlice] = ( 0 4 8 12 7 11 15 19 ).  
The index of the first element of vaResult is: 0.  
```  
  
##  <a name="stride"></a>  gslice::STRIDE  
 Umożliwia znalezienie odległość między elementami w ogólne wycinek valarray —.  
  
```  
valarray<size_t> stride() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Valarray — Określanie odległości między elementami w każdy wycinek ogólne wycinek valarray —.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// gslice_stride.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> va ( 20 ), vaResult;  
   for (i = 0 ; i < 20 ; i+=1 )  
      va [ i ] =  i;  
  
   cout << "The operand valarray va is:\n ( ";  
      for (i = 0 ; i < 20 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
  
   valarray<size_t> Len ( 2 ), Stride ( 2 );  
   Len [0] = 4;  
   Len [1] = 4;  
   Stride [0] = 7;  
   Stride [1] = 4;  
  
   gslice vaGSlice ( 0, Len, Stride );  
   vaResult = va [ vaGSlice ];  
   const valarray <size_t> strideGS = vaGSlice.stride ( );  
  
   cout << "The valarray for vaGSlice is vaResult:"  
        << "\n va[vaGSlice] = ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaResult [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The strides of vaResult are:"  
        << "\n vaGSlice.stride ( ) = ( ";  
      for ( i = 0 ; i < 2 ; i++ )  
         cout << strideGS[ i ] << " ";  
   cout << ")." << endl;  
  
}  
```  
  
```Output  
The operand valarray va is:  
 ( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ).  
The valarray for vaGSlice is vaResult:  
 va[vaGSlice] = ( 0 4 8 12 7 11 15 19 ).  
The strides of vaResult are:  
 vaGSlice.stride ( ) = ( 7 4 ).  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

