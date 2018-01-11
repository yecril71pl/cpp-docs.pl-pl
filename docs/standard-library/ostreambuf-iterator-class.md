---
title: Klasa ostreambuf_iterator | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- streambuf/std::ostreambuf_iterator
- iterator/std::ostreambuf_iterator::char_type
- iterator/std::ostreambuf_iterator::ostream_type
- iterator/std::ostreambuf_iterator::streambuf_type
- iterator/std::ostreambuf_iterator::traits_type
- iterator/std::ostreambuf_iterator::failed
dev_langs: C++
helpviewer_keywords:
- std::ostreambuf_iterator [C++]
- std::ostreambuf_iterator [C++], char_type
- std::ostreambuf_iterator [C++], ostream_type
- std::ostreambuf_iterator [C++], streambuf_type
- std::ostreambuf_iterator [C++], traits_type
- std::ostreambuf_iterator [C++], failed
ms.assetid: dad1e624-2f45-4e94-8887-a885e95f9071
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c94ed10a0b97820c5a787e4350d39dcf6286fee7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ostreambufiterator-class"></a>Klasa ostreambuf_iterator
Ostreambuf_iterator — klasa szablonu opisuje obiekt iteratora wyjściowy, który zapisuje elementy kolejnych znaków do strumienia wyjściowego o wyodrębnianiu **operator >>**. `ostreambuf_iterator`s różnią się od [ostream_iterator — klasa](../standard-library/ostream-iterator-class.md) w mających znaków, a nie typu ogólnego typu obiektu wstawiana do strumienia wyjściowego.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class CharType = char class Traits = char_traits <CharType>>
```  
  
#### <a name="parameters"></a>Parametry  
 `CharType`  
 Typ, który reprezentuje typ znaków dla ostreambuf_iterator. Ten argument jest opcjonalny, a wartość domyślna to `char`.  
  
 `Traits`  
 Typ, który reprezentuje typ znaków dla ostreambuf_iterator. Ten argument jest opcjonalny, a wartość domyślna to `char_traits` \< *CharType >.*  
  
## <a name="remarks"></a>Uwagi  
 Klasa ostreambuf_iterator musi spełniać wymagania dla iteratora wyjściowego. Algorytmy mogą być zapisywane dane bezpośrednio do danych wyjściowych strumieni przy użyciu `ostreambuf_iterator`. Klasa oferuje iterator strumienia niskiego poziomu, który umożliwia dostęp do surowego (niesformatowanego) strumienia we/wy w postaci znaków, a także możliwość ominięcia etapu buforowania i tłumaczenia znaków związanych z iteratorami strumienia wysokiego poziomu.  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator)|Konstruuje `ostreambuf_iterator` którego zainicjowano można zapisać do strumienia wyjściowego znaków.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#char_type)|Typ, który zawiera znak typu `ostreambuf_iterator`.|  
|[ostream_type](#ostreambuf_iterator_ostream_type)|Typ, który udostępnia dla typu strumienia `ostream_iterator`.|  
|[streambuf_type](#streambuf_type)|Typ, który udostępnia dla typu strumienia `ostreambuf_iterator`.|  
|[traits_type](#traits_type)|Typ, który zawiera typ cech znaków `ostream_iterator`.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[nie powiodło się](#failed)|Testuje pod kątem błędu wstawiania do bufora strumienia wyjściowego.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator *](#op_star)|Operator usuwania odwołań używaną do zaimplementowania wyrażenia iteratora dane wyjściowe * `i`  =  `x`.|  
|[operator ++](#op_add_add)|Operator inkrementacji prawidłowo, który zwraca `ostreambuf_iterator` do tego samego obiektu adresowane, zanim została wywołana w operacji.|  
|[operator =](#op_eq)|Operator wstawia znak do bufora skojarzonego strumienia.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<iteratora >  
  
 **Namespace:** Standard  
  
##  <a name="char_type"></a>ostreambuf_iterator::char_type  
 Typ, który zawiera znak typu `ostreambuf_iterator`.  
  
```
typedef CharType char_type;
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem parametru szablonu **CharType**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// ostreambuf_iterator_char_type.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   typedef ostreambuf_iterator<char>::char_type CHT1;  
   typedef ostreambuf_iterator<char>::traits_type CHTR1;  
  
   // ostreambuf_iterator for stream cout  
   // with new line delimiter:  
    ostreambuf_iterator< CHT1, CHTR1> charOutBuf ( cout );  
  
   // Standard iterator interface for writing  
   // elements to the output streambuf:  
   cout << "The characters written to the output stream\n"  
        << " by charOutBuf are: ";  
 *charOutBuf = 'O';  
   charOutBuf++;  
 *charOutBuf = 'U';  
   charOutBuf++;  
 *charOutBuf = 'T';  
   charOutBuf++;  
   cout << "." << endl;  
}  
\* Output:   
The characters written to the output stream  
 by charOutBuf are: OUT.  
*\  
```  
  
##  <a name="failed"></a>ostreambuf_iterator::failed  
 Testuje pod kątem błędu wstawiania do bufora strumienia wyjściowego.  
  
```
bool failed() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli nie w buforze strumienia wyjściowego nie powiodło się wstawienie wcześniej; w przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca **true** , gdy w jakimkolwiek użyciem poprzedniego elementu członkowskiego `operator=`, wywołanie **subf**-> _ `sputc` zwrócił **eof**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// ostreambuf_iterator_failed.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // ostreambuf_iterator for stream cout  
   ostreambuf_iterator<char> charOut ( cout );  
  
 *charOut = 'a';  
   charOut ++;  
 *charOut  = 'b';  
   charOut ++;     
 *charOut = 'c';  
   cout << " are characters output individually." << endl;  
  
   bool b1 = charOut.failed ( );  
   if (b1)   
       cout << "At least one insertion failed." << endl;  
   else  
       cout << "No insertions failed." << endl;  
}  
\* Output:   
abc are characters output individually.  
No insertions failed.  
*\  
```  
  
##  <a name="op_star"></a>ostreambuf_iterator::operator *  
 Operator usuwania odwołań prawidłowo używaną do zaimplementowania wyrażenia iteratora dane wyjściowe \* *i* = *x*.  
  
```
ostreambuf_iterator<CharType, Traits>& operator*();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Obiekt ostreambuf iteratora.  
  
### <a name="remarks"></a>Uwagi  
 Ten operator działa tylko w wyrażeniu iteratora dane wyjściowe \* *i* = *x* znaków dane wyjściowe do strumienia buforu. Stosowane do iteratora ostreambuf, zwraca iteratora;  **\*iter** zwraca **iter**,  
  
### <a name="example"></a>Przykład  
  
```cpp  
// ostreambuf_iterator_op_deref.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // ostreambuf_iterator for stream cout  
   // with new line delimiter  
   ostreambuf_iterator<char> charOutBuf ( cout );  
  
   // Standard iterator interface for writing  
   // elements to the output stream  
   cout << "Elements written to output stream:" << endl;  
 *charOutBuf = 'O';  
   charOutBuf++;   // no effect on iterator position  
 *charOutBuf = 'U';  
 *charOutBuf = 'T';  
}  
\* Output:   
Elements written to output stream:  
OUT  
*\  
```  
  
##  <a name="op_add_add"></a>ostreambuf_iterator::operator ++  
 Operator inkrementacji prawidłowo, który zwraca iteratora ostream do tego samego znaku, który zwrócono przed operacją została wywołana.  
  
```
ostreambuf_iterator<CharType, Traits>& operator++();
ostreambuf_iterator<CharType, Traits>& operator++(int);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do znaku pierwotnie skierowana lub zdefiniowane w implementacji obiektu, który można przekonwertować na typ `ostreambuf_iterator` \< **CharType**, **cech**>.  
  
### <a name="remarks"></a>Uwagi  
 Operator jest używane do implementowania wyrażenia iteratora dane wyjściowe \* *i* = *x*.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// ostreambuf_iterator_op_incr.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // ostreambuf_iterator for stream cout  
   // with new line delimiter  
   ostreambuf_iterator<char> charOutBuf ( cout );  
  
   // Standard iterator interface for writing  
   // elements to the output stream  
   cout << "Elements written to output stream:" << endl;  
 *charOutBuf = 'O';  
   charOutBuf++;      // No effect on iterator position  
 *charOutBuf = 'U';  
 *charOutBuf = 'T';     
}  
\* Output:   
Elements written to output stream:  
OUT  
*\  
```  
  
##  <a name="op_eq"></a>ostreambuf_iterator::operator =  
 Operator wstawia znak do bufora skojarzonego strumienia.  
  
```
ostreambuf_iterator<CharType, Traits>& operator=(CharType _Char);
```  
  
### <a name="parameters"></a>Parametry  
 `_Char`  
 Znak, który ma zostać wstawiony do buforu strumienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do znaku wstawione do buforu strumienia.  
  
### <a name="remarks"></a>Uwagi  
 Operator przypisania używaną do zaimplementowania wyrażenia iteratora dane wyjściowe \* *i* = *x* do zapisywania do strumienia wyjściowego.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// ostreambuf_iterator_op_assign.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // ostreambuf_iterator for stream cout  
   // with new line delimiter  
   ostreambuf_iterator<char> charOutBuf ( cout );  
  
   // Standard iterator interface for writing  
   // elements to the output stream  
   cout << "Elements written to output stream:" << endl;  
 *charOutBuf = 'O';  
   charOutBuf++;      // No effect on iterator position  
 *charOutBuf = 'U';  
 *charOutBuf = 'T';     
}  
\* Output:   
Elements written to output stream:  
OUT  
*\  
```  
  
##  <a name="ostreambuf_iterator_ostreambuf_iterator"></a>ostreambuf_iterator::ostreambuf_iterator  
 Konstruuje `ostreambuf_iterator` którego zainicjowano można zapisać do strumienia wyjściowego znaków.  
  
```
ostreambuf_iterator(streambuf_type* strbuf) throw();
ostreambuf_iterator(ostream_type& Ostr) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `strbuf`  
 Dane wyjściowe obiektu streambuf używane w celu zainicjowania wskaźnika buforu strumienia wyjściowego.  
  
 `Ostr`  
 Obiekt strumienia wyjściowego używane w celu zainicjowania wskaźnika buforu strumienia wyjściowego.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy Konstruktor inicjuje wskaźnika buforu strumienia wyjściowego za pomocą `strbuf`.  
  
 Drugi Konstruktor inicjuje wskaźnika buforu strumienia wyjściowego za pomocą `Ostr`. `rdbuf`., Wskaźnik przechowywanych nie może mieć pustego wskaźnika.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// ostreambuf_iteratorOstreambuf_iterator.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // ostreambuf_iterator for stream cout  
   ostreambuf_iterator<char> charOut ( cout );  
  
 *charOut = 'O';  
   charOut ++;  
 *charOut  = 'U';  
   charOut ++;     
 *charOut = 'T';  
   cout << " are characters output individually." << endl;  
  
   ostreambuf_iterator<char> strOut ( cout );  
   string str = "These characters are being written to the output stream.\n ";  
   copy ( str.begin ( ), str. end ( ), strOut );  
}  
\* Output:   
OUT are characters output individually.  
These characters are being written to the output stream.  
*\  
```  
  
##  <a name="ostreambuf_iterator_ostream_type"></a>ostreambuf_iterator::ostream_type  
 Typ, który udostępnia dla typu strumienia `ostream_iterator`.  
  
```
typedef basicOstream<CharType, Traits> ostream_type;
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem `basicOstream` \< **CharType**, **cech**>  
  
### <a name="example"></a>Przykład  
  Zobacz [ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator) przykład sposobu deklarowanie i użycie `ostream_type`.  
  
##  <a name="streambuf_type"></a>ostreambuf_iterator::streambuf_type  
 Typ, który udostępnia dla typu strumienia `ostreambuf_iterator`.  
  
```
typedef basic_streambuf<CharType, Traits> streambuf_type;
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem `basic_streambuf` \< **CharType**, **cech**>, klasa strumienia dla buforów we/wy, które staje się `streambuf` podczas przeznaczone do znaku typu `char`.  
  
### <a name="example"></a>Przykład  
  Zobacz [ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator) przykład sposobu deklarowanie i użycie `streambuf_type`.  
  
##  <a name="traits_type"></a>ostreambuf_iterator::traits_type  
 Typ, który zawiera typ cech znaków `ostream_iterator`.  
  
```
typedef Traits traits_type;
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem parametru szablonu **cech**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// ostreambuf_iterator_traits_type.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   typedef ostreambuf_iterator<char>::char_type CHT1;  
   typedef ostreambuf_iterator<char>::traits_type CHTR1;  
  
   // ostreambuf_iterator for stream cout  
   // with new line delimiter:  
    ostreambuf_iterator< CHT1, CHTR1> charOutBuf ( cout );  
  
   // Standard iterator interface for writing  
   // elements to the output streambuf:  
   cout << "The characters written to the output stream\n"  
        << " by charOutBuf are: ";  
 *charOutBuf = 'O';  
   charOutBuf++;  
 *charOutBuf = 'U';  
   charOutBuf++;  
 *charOutBuf = 'T';  
   charOutBuf++;  
   cout << "." << endl;  
}  
\* Output:   
The characters written to the output stream  
 by charOutBuf are: OUT.  
*\  
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<Iterator >](../standard-library/iterator.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)



