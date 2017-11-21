---
title: "&lt;IOS&gt; definicje typów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- iosfwd/std::ios
- iosfwd/std::streamoff
- iosfwd/std::streampos
- iosfwd/std::streamsize
- iosfwd/std::wios
- iosfwd/std::wstreampos
ms.assetid: 0b962632-3439-44de-bf26-20c67a7f0ff3
caps.latest.revision: "13"
manager: ghogen
ms.openlocfilehash: 493850d78e72e6b95408964a5e28d090a1dc58f1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ltiosgt-typedefs"></a>&lt;IOS&gt; definicje typów
||||  
|-|-|-|  
|[dla systemu IOS](#ios)|[streamoff](#streamoff)|[streampos](#streampos)|  
|[streamsize](#streamsize)|[wios](#wios)|[wstreampos](#wstreampos)|  
  
##  <a name="ios"></a>dla systemu IOS  
 Obsługuje klasy systemu ios z biblioteki iostream stary.  
  
```  
typedef basic_ios<char, char_traits<char>> ios;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem dla szablonu klasy [basic_ios —](../standard-library/basic-ios-class.md), wyspecjalizowany dla elementów typu `char` z domyślnego cech znaków.  
  
##  <a name="streamoff"></a>streamoff  
 Obsługuje operacje wewnętrzne.  
  
```  
#ifdef _WIN64  
    typedef __int64 streamoff;  
#else  
    typedef long streamoff;  
#endif  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest całkowita opisujący obiekt, który może przechowywać Przesunięcie bajtów, zaangażowane w strumieniu różnych operacji rozmieszczania. Reprezentacja ma przynajmniej 32 bity wartość. Nie jest zawsze wystarczająco duże, aby reprezentować pozycję dowolnego typu byte w strumieniu. Wartość **streamoff(-1)** zwykle wskazuje błędne przesunięcia.  
  
##  <a name="streampos"></a>streampos  
 Przechowuje bieżącą pozycję wskaźnika buforu lub wskaźnika pliku.  
  
```  
typedef fpos<mbstate_t> streampos;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem [fpos —](../standard-library/fpos-class.md)< `mbstate_t`>.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// ios_streampos.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main( )   
{  
   using namespace std;  
  
   ofstream x( "iostream.txt" );  
   x << "testing";  
   streampos y = x.tellp( );  
   cout << y << endl;  
}  
```  
  
```Output  
7  
```  
  
##  <a name="streamsize"></a>streamsize  
 Określa rozmiar strumienia.  
  
```  
#ifdef _WIN64  
    typedef __int64 streamsize;  
#else  
    typedef int streamsize;  
#endif  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest całkowita opisujący obiekt, który może przechowywać licznik elementy związane z różnych operacji strumienia. Reprezentacja ma co najmniej 16 bitów. Nie jest zawsze wystarczająco duże, aby reprezentować pozycję dowolnego typu byte w strumieniu.  
  
### <a name="example"></a>Przykład  
  Po kompilowania i uruchamiania programu następujące przyjrzeć się test.txt pliku, aby zobaczyć efekt ustawienie `streamsize`.  
  
```  
// ios_streamsize.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main( )   
{  
   using namespace std;  
   char a[16] = "any such text";  
   ofstream x( "test.txt" );  
   streamsize y = 6;  
   x.write( a, y );  
}  
```  
  
##  <a name="wios"></a>wios  
 Obsługuje wios klasy z biblioteki iostream stary.  
  
```  
typedef basic_ios<wchar_t, char_traits<wchar_t>> wios;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem dla szablonu klasy [basic_ios —](../standard-library/basic-ios-class.md), wyspecjalizowany dla elementów typu `wchar_t` z domyślnego cech znaków.  
  
##  <a name="wstreampos"></a>wstreampos  
 Przechowuje bieżącą pozycję wskaźnika buforu lub wskaźnika pliku.  
  
```  
typedef fpos<mbstate_t> wstreampos;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem [fpos —](../standard-library/fpos-class.md)< `mbstate_t`>.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// ios_wstreampos.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main( )   
{  
   using namespace std;  
   wofstream xw( "wiostream.txt" );  
   xw << L"testing";  
   wstreampos y = xw.tellp( );  
   cout << y << endl;  
}  
```  
  
```Output  
7  
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<IOS >](../standard-library/ios.md)

