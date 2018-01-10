---
title: "basic_ostream — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ostream/std::basic_ostream
- ostream/std::basic_ostream::flush
- ostream/std::basic_ostream::put
- ostream/std::basic_ostream::seekp
- ostream/std::basic_ostream::sentry
- ostream/std::basic_ostream::swap
- ostream/std::basic_ostream::tellp
- ostream/std::basic_ostream::write
dev_langs: C++
helpviewer_keywords:
- std::basic_ostream [C++]
- std::basic_ostream [C++], flush
- std::basic_ostream [C++], put
- std::basic_ostream [C++], seekp
- std::basic_ostream [C++], sentry
- std::basic_ostream [C++], swap
- std::basic_ostream [C++], tellp
- std::basic_ostream [C++], write
ms.assetid: 5baadc65-b662-4fab-8c9f-94457c58cda1
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d08410c68a2cff5a1c85733c4a2a2ed1775754b0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="basicostream-class"></a>basic_ostream — Klasa
Ta klasa szablonu opisuje obiekt, który kontroluje wstawiania elementów i obiektów zakodowanych w buforze strumienia, elementami typu **elementu**, znanej także jako [char_type](../standard-library/basic-ios-class.md#char_type), są którego cech znaków Określona klasa **Tr**, znanej także jako [traits_type](../standard-library/basic-ios-class.md#traits_type).  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Elem, class Tr = char_traits<Elem>>  
class basic_ostream : virtual public basic_ios<Elem, Tr>  
```  
  
#### <a name="parameters"></a>Parametry  
 `Elem`  
 A `char_type`.  
  
 `Tr`  
 Znak `traits_type`.  
  
## <a name="remarks"></a>Uwagi  
 Większość elementu członkowskiego funkcje tego przeciążenia [operator <<](#op_lt_lt) są funkcje sformatowanych danych wyjściowych. One zgodne ze wzorcem:  
  
```  
iostate state = goodbit;  
const sentry ok(*this);

if (ok)  
 {try  
 {<convert and insert elements  
    accumulate flags in state> }  
    catch (...)  
 {try  
 {setstate(badbit);

}  
    catch (...)  
 {}  
    if ((exceptions()& badbit) != 0)  
    throw; }}  
width(0);
// Except for operator<<(Elem)  
setstate(state);

return (*this);
```  
  
 Dwóch innych funkcji elementów członkowskich są funkcje niesformatowanych danych wyjściowych. One zgodne ze wzorcem:  
  
```  
iostate state = goodbit;  
const sentry ok(*this);

if (!ok)  
    state |= badbit;  
else  
 {try  
 {<obtain and insert elements  
    accumulate flags in state> }  
    catch (...)  
 {try  
 {setstate(badbit);

}  
    catch (...)  
 {}  
    if ((exceptions()& badbit) != 0)  
    throw; }}  
setstate(state);

return (*this);
```  
  
 Obie grupy wywołania funkcji [metoda setstate](../standard-library/basic-ios-class.md#setstate)**(badbit)** ich wystąpienia awarii podczas wstawiania elementów.  
  
 Obiekt basic_istream — klasa\< **elementu**, **Tr**> są przechowywane tylko wirtualny publicznego podstawowy obiekt klasy [basic_ios —](../standard-library/basic-ios-class.md)  **\<Elementu**, **Tr >**.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [basic_ofstream — klasa](../standard-library/basic-ofstream-class.md) Aby dowiedzieć się więcej na temat strumienie wyjściowe.  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[basic_ostream —](#basic_ostream)|Konstruuje `basic_ostream` obiektu.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[Flush](#flush)|Opróżnia bufor.|  
|[Umieść](#put)|Umieszcza znak w strumieniu.|  
|[seekp](#seekp)|Resetuje pozycja w strumieniu wyjściowym.|  
|[Sentry](#sentry)|Zagnieżdżona klasa opisuje obiekt, którego deklaracji struktury sformatowane dane wyjściowe funkcji i funkcji niesformatowanych danych wyjściowych.|  
|[swap](#op_eq)|Zamienia wartości to `basic_ostream` obiektu dla osób z dostarczonych `basic_ostream` obiektu.|  
|[tellp](#tellp)|Raporty pozycja w strumieniu wyjściowym.|  
|[write](#write)|Umieszcza znaków w strumieniu.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator =](#basic_ostream_operator_eq)|Przypisuje wartość dostarczonych `basic_ostream` obiekt parametru do tego obiektu.|  
|[Operator <<](#basic_ostream_operator_lt_lt)|Zapisuje w strumieniu.|  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<ostream >  
  
 **Namespace:** Standard  
  
##  <a name="basic_ostream"></a>basic_ostream::basic_ostream  
 Konstruuje `basic_ostream` obiektu.  
  
```  
explicit basic_ostream(
    basic_streambuf<Elem, Tr>* strbuf,  
    bool _Isstd = false);

basic_ostream(basic_ostream&& right);
```  
  
### <a name="parameters"></a>Parametry  
 `strbuf`  
 Obiekt typu [basic_streambuf —](../standard-library/basic-streambuf-class.md).  
  
 `_Isstd`  
 `true`Jeśli jest to Standardowy strumień; w przeciwnym razie `false`.  
  
 `right`  
 Odwołania do r-wartości do obiektu typu `basic_ostream`.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy Konstruktor inicjuje klasy podstawowej, przez wywołanie metody [init](../standard-library/basic-ios-class.md#init)(`strbuf`). Drugi Konstruktor inicjuje klasy podstawowej, przez wywołanie metody [basic_ios::move](../standard-library/basic-ios-class.md#move)`(right)`.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [basic_ofstream::basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream) Aby dowiedzieć się więcej na temat strumienie wyjściowe.  
  
##  <a name="flush"></a>basic_ostream::Flush  
 Opróżnia bufor.  
  
```  
basic_ostream<Elem, Tr>& flush();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do obiektu basic_ostream —.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli [rdbuf](../standard-library/basic-ios-class.md#rdbuf) nie jest wskaźnika o wartości null, wywołania funkcji **-> rdbuf**[pubsync](../standard-library/basic-streambuf-class.md#pubsync). Jeśli która zwraca wartość -1, wywołuje funkcję [metoda setstate](../standard-library/basic-ios-class.md#setstate)(**badbit**). Zwraca  **\*to**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_ostream_flush.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   cout << "test";  
   cout.flush();  
}  
```  
  
```Output  
test  
```  
  
##  <a name="basic_ostream_operator_lt_lt"></a>basic_ostream::operator&lt;&lt;  
 Zapisuje w strumieniu.  
  
```  
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& (* Pfn)(basic_ostream<Elem, Tr>&));

basic_ostream<Elem, Tr>& operator<<(
    ios_base& (* Pfn)(ios_base&));

basic_ostream<Elem, Tr>& operator<<(
    basic_ios<Elem, Tr>& (* Pfn)(basic_ios<Elem, Tr>&));

basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
basic_ostream<Elem, Tr>& operator<<(bool val);
basic_ostream<Elem, Tr>& operator<<(short val);
basic_ostream<Elem, Tr>& operator<<(unsigned short val);
basic_ostream<Elem, Tr>& operator<<(int __w64  val);
basic_ostream<Elem, Tr>& operator<<(unsigned int __w64  val);
basic_ostream<Elem, Tr>& operator<<(long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long __w64  val);
basic_ostream<Elem, Tr>& operator<<(long long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long long val);
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
basic_ostream<Elem, Tr>& operator<<(const void* val);
```  
  
### <a name="parameters"></a>Parametry  
 `Pfn`  
 Wskaźnik funkcji.  
  
 `strbuf`  
 Wskaźnik do **stream_buf** obiektu.  
  
 `val`  
 Element do zapisu do strumienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do obiektu basic_ostream —.  
  
### <a name="remarks"></a>Uwagi  
 `<ostream>` Nagłówka definiuje również kilka operatorów globalnych wstawiania. Aby uzyskać więcej informacji, zobacz [operator <<](../standard-library/ostream-operators.md#op_lt_lt).  
  
 Pierwszy funkcji członkowskiej zapewnia, że wyrażenie w postaci **ostr << endl** wywołania [endl](../standard-library/ostream-functions.md#endl)**(ostr)**, a następnie zwraca  **\*to** . Drugi i trzeci funkcje upewnij się, że inne manipulatory, takich jak [szesnastkowych](../standard-library/ios-functions.md#hex), zachowują się podobnie. Pozostałe funkcje są wszystkie funkcje sformatowane dane wyjściowe.  
  
 Funkcja  
  
```  
basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
```  
  
 wyodrębnia elementy z `strbuf`, jeśli `strbuf` nie jest wskaźnika o wartości null i wstawia je. Wyodrębnianie zatrzymuje się na końcu pliku, lub jeśli wyodrębniania zgłasza wyjątek (która jest zgłoszony). Powoduje także zatrzymanie, bez wyodrębniania w danym elementu, jeśli wstawiania nie powiedzie się. Jeśli funkcja wstawia żadnych elementów lub jeśli wyodrębniania zgłasza wyjątek, wywołuje funkcję [metoda setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**). W każdym przypadku, funkcja zwraca  **\*to**.  
  
 Funkcja  
  
```  
basic_ostream<Elem, Tr>& operator<<(bool val);
```  
  
 Konwertuje `_Val` na wartość logiczną pól i wstawia go przez wywołanie metody [use_facet](../standard-library/basic-filebuf-class.md#open)**< num_put —\<elementu, OutIt >**`(`[getloc](../standard-library/ios-base-class.md#getloc)). [Umieść](#put)(**OutIt**([rdbuf](../standard-library/basic-ios-class.md#rdbuf)),  **\*to**, `getloc`, **val**). W tym miejscu **OutIt** jest zdefiniowany jako [ostreambuf_iterator](../standard-library/ostreambuf-iterator-class.md)**\<elementu, Tr >**. Funkcja zwraca  **\*to**.  
  
 Funkcje  
  
```  
basic_ostream<Elem, Tr>& operator<<(short val);
basic_ostream<Elem, Tr>& operator<<(unsigned short val);
basic_ostream<Elem, Tr>& operator<<(int val);
basic_ostream<Elem, Tr>& operator<<(unsigned int __w64  val);
basic_ostream<Elem, Tr>& operator<<(long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long val);
basic_ostream<Elem, Tr>& operator<<(long long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long long val);
basic_ostream<Elem, Tr>& operator<<(const void* val);
```  
  
 Konwertuj każdego `val` do liczbową pól i wstaw go przez wywołanie metody **use_facet < num_put —\<elementu, OutIt >**(`getloc`). **Umieść**(**OutIt**(`rdbuf`),  **\*to**, `getloc`, **val**). W tym miejscu **OutIt** jest zdefiniowany jako **ostreambuf_iterator\<elementu, Tr >**. Funkcja zwraca  **\*to**.  
  
 Funkcje  
  
```  
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
```  
  
 Konwertuj każdego `val` do liczbową pól i wstaw go przez wywołanie metody **use_facet < num_put —\<elementu, OutIt >**(`getloc`)**. Umieść**(**OutIt**(`rdbuf`),  **\*to**, `getloc`, **val**). W tym miejscu **OutIt** jest zdefiniowany jako **ostreambuf_iterator\<elementu, Tr >**. Funkcja zwraca  **\*to**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_ostream_op_write.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <string.h>  
  
using namespace std;  
  
ios_base& hex2( ios_base& ib )  
{  
   ib.unsetf( ios_base::dec );  
   ib.setf( ios_base::hex );  
   return ib;  
}  
  
basic_ostream<char, char_traits<char> >& somefunc(basic_ostream<char, char_traits<char> > &i)
{
    if (i == cout)
    {
        i << "i is cout" << endl;
    }
    return i;
}

class CTxtStreambuf : public basic_streambuf< char, char_traits< char > >
{
public:
    CTxtStreambuf(char *_pszText)
    {
        pszText = _pszText;
        setg(pszText, pszText, pszText + strlen(pszText));
    };
    char *pszText;
};

int main()
{
    cout << somefunc;
    cout << 21 << endl;

    hex2(cout);
    cout << 21 << endl;

    CTxtStreambuf f("text in streambuf");
    cout << &f << endl;
}
```  
  
##  <a name="op_eq"></a>basic_ostream::operator =  
 Przypisuje wartości dla udostępnionych `basic_ostream` obiekt parametru do tego obiektu.  
  
```  
basic_ostream& operator=(basic_ostream&& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 `rvalue` Odwołanie do `basic_ostream` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Operator członkowski wywołuje wymiany `(right)`.  
  
##  <a name="put"></a>basic_ostream::Put  
 Umieszcza znak w strumieniu.  
  
```  
basic_ostream<Elem, Tr>& put(char_type _Ch);
```  
  
### <a name="parameters"></a>Parametry  
 `_Ch`  
 Znak.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do obiektu basic_ostream —.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja niesformatowanych danych wyjściowych wstawia element `_Ch`. Zwraca  **\*to**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_ostream_put.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   cout.put( 'v' );  
   cout << endl;  
   wcout.put( L'l' );  
}  
```  
  
```Output  
v  
l  
```  
  
##  <a name="seekp"></a>basic_ostream::seekp  
 Zresetuj pozycję w strumieniu wyjściowym.  
  
```  
basic_ostream<Elem, Tr>& seekp(pos_type _Pos);

basic_ostream<Elem, Tr>& seekp(off_type _Off, ios_base::seekdir _Way);
```  
  
### <a name="parameters"></a>Parametry  
 `_Pos`  
 Pozycja w strumieniu.  
  
 `_Off`  
 Przesunięcie względem `_Way`.  
  
 `_Way`  
 Jeden z [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) wyliczenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do obiektu basic_ostream —.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli [niepowodzenie](../standard-library/basic-ios-class.md#fail) jest **false**, pierwszego wywołania funkcji Członkowskich **newpos =** [rdbuf](../standard-library/basic-ios-class.md#rdbuf)  **->**  [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos)(*_Pos*), w przypadku niektórych `pos_type` tymczasowy obiekt **newpos**. Jeśli **niepowodzenie** ma wartość false, drugi wywołania funkcji **newpos = rdbuf - >** [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(*_Off, _Way*). W obu przypadkach jeśli (`off_type`)**newpos ==** (`off_type`)(-1) (pozycjonowania niepowodzenia operacji), a następnie funkcja wywołuje **istr.** [metoda setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**). Obie funkcje zwracają  **\*to**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_ostream_seekp.cpp  
// compile with: /EHsc  
#include <fstream>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    ofstream x("basic_ostream_seekp.txt");  
    streamoff i = x.tellp();  
    cout << i << endl;  
    x << "testing";  
    i = x.tellp();  
    cout << i << endl;  
    x.seekp(2);   // Put char in third char position in file  
    x << " ";  
  
    x.seekp(2, ios::end);   // Put char two after end of file  
    x << "z";  
}  
```  
  
```Output  
0  
7  
```  
  
##  <a name="sentry"></a>basic_ostream::Sentry  
 Zagnieżdżona klasa opisuje obiekt, którego deklaracji struktury sformatowane dane wyjściowe funkcji i funkcji niesformatowanych danych wyjściowych.  
  
{sentry — klasa  
   publiczny:  
   jawne sentry (basic_ostream —\<elementu, Tr > & _Ostr); Stała; bool() operator ~ sentry();};  
  
### <a name="remarks"></a>Uwagi  
 Zagnieżdżona klasa opisuje obiekt, którego deklaracji struktury sformatowane dane wyjściowe funkcji i funkcji niesformatowanych danych wyjściowych. Jeśli **ostr.** [dobrej](../standard-library/basic-ios-class.md#good) jest **true** i **ostr.** [tie](../standard-library/basic-ios-class.md#tie) nie jest wskaźnika o wartości null, Konstruktor wywołuje **-> ostr.tie**[opróżnić](#flush). Konstruktor następnie przechowuje wartość zwrócona przez **ostr.good** w **stan**. Wywołanie nowsze **bool — operator** zapewnia to przechowywanej wartości.  
  
 Jeśli `uncaught_exception` zwraca **false** i [flagi](../standard-library/ios-base-class.md#flags)  **&**  [unitbuf](../standard-library/ios-functions.md#unitbuf) jest różna od zera, wywołania destruktora [opróżnić](#flush).  
  
##  <a name="swap"></a>basic_ostream::swap  
 Zamienia wartości to `basic_ostream` obiektu dla udostępnionych wartości `basic_ostream`.  
  
```  
void swap(basic_ostream& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Odwołanie do `basic_ostream` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania funkcji Członkowskich [basic_ios::swap](../standard-library/basic-ios-class.md#swap) `(right)` do wymiany zawartości obiektu zawartość `right`.  
  
##  <a name="tellp"></a>basic_ostream::tellp  
 Raport pozycja w strumieniu wyjściowym.  
  
```  
pos_type tellp();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pozycja w strumieniu wyjściowym.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli [niepowodzenie](../standard-library/basic-ios-class.md#fail) jest **false**, zwraca funkcja członkowska [rdbuf](../standard-library/basic-ios-class.md#rdbuf)  **->**  [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff) (0, `cur`, **w**). W przeciwnym razie zwraca `pos_type`(-1).  
  
### <a name="example"></a>Przykład  
  Zobacz [seekp](#seekp) na przykład za pomocą `tellp`.  
  
##  <a name="write"></a>basic_ostream::Write  
 Umieść znaków w strumieniu.  
  
```  
basic_ostream<Elem, Tr>& write(const char_type* str, streamsize count);
```  
  
### <a name="parameters"></a>Parametry  
 `count`  
 Liczba znaków w celu uruchomienia strumienia.  
  
 `str`  
 Znaki, które można umieścić w strumieniu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do obiektu basic_ostream —.  
  
### <a name="remarks"></a>Uwagi  
 [Niesformatowany dane wyjściowe funkcji](../standard-library/basic-ostream-class.md) wstawia sekwencji `count` elementów, rozpoczynając od `str`.  
  
### <a name="example"></a>Przykład  
  Zobacz [streamsize](../standard-library/ios-typedefs.md#streamsize) na przykład za pomocą `write`.  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream — programowanie](../standard-library/iostream-programming.md)   
 [Konwencje iostream](../standard-library/iostreams-conventions.md)

