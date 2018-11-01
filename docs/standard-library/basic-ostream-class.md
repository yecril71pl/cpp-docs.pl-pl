---
title: basic_ostream — Klasa
ms.date: 11/04/2016
f1_keywords:
- ostream/std::basic_ostream
- ostream/std::basic_ostream::flush
- ostream/std::basic_ostream::put
- ostream/std::basic_ostream::seekp
- ostream/std::basic_ostream::sentry
- ostream/std::basic_ostream::swap
- ostream/std::basic_ostream::tellp
- ostream/std::basic_ostream::write
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
ms.openlocfilehash: dce4911bd4b7abe6c73551d6a0b178d9b2700dbb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543640"
---
# <a name="basicostream-class"></a>basic_ostream — Klasa

Ta klasa szablonu opisuje obiekt, który kontroluje wstawiania elementów i obiekty zakodowane do bufora strumienia, elementami typu `Elem`, znane również jako [char_type](../standard-library/basic-ios-class.md#char_type), którego cech są określane przez klasę `Tr`, znane również jako [traits_type](../standard-library/basic-ios-class.md#traits_type).

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ostream : virtual public basic_ios<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem*<br/>
A `char_type`.

*TR*<br/>
Znak `traits_type`.

## <a name="remarks"></a>Uwagi

Większość elementu członkowskiego funkcje tego przeciążenia [operator <<](#op_lt_lt) sformatowane wyniki funkcji. Są zgodne ze wzorcem:

```cpp
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

Dwie funkcje Członkowskie są funkcje niesformatowany danych wyjściowych. Są zgodne ze wzorcem:

```cpp
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

Obie grupy wywołanie funkcji [setstate](../standard-library/basic-ios-class.md#setstate)(**badbit**) w momencie napotkania błędu podczas wstawiania elementów.

Obiekt klasy basic_istream\< **Elem**, **Tr**> przechowuje tylko publiczny podstawowy obiekt wirtualnych klasy [basic_ios —](../standard-library/basic-ios-class.md)  **\<Elem**, **Tr >**.

## <a name="example"></a>Przykład

Zobacz przykład [basic_ofstream — klasa](../standard-library/basic-ofstream-class.md) Aby dowiedzieć się więcej na temat strumieni wyjściowych.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_ostream](#basic_ostream)|Konstruuje `basic_ostream` obiektu.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[flush](#flush)|Opróżnia bufor.|
|[put](#put)|Umieszcza znak w strumieniu.|
|[seekp](#seekp)|Resetuje pozycji w strumieniu wyjściowym.|
|[Sentry](#sentry)|Zagnieżdżona klasa opisująca obiekt, którego deklaracji struktury, funkcje sformatowane wyniki i funkcje niesformatowany danych wyjściowych.|
|[swap](#op_eq)|Wymienia wartości to `basic_ostream` obiektu dla osób z dostarczonych `basic_ostream` obiektu.|
|[tellp —](#tellp)|Raporty pozycji w strumieniu wyjściowym.|
|[write](#write)|Umieszcza znaków w strumieniu.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#basic_ostream_operator_eq)|Przypisuje wartość podane `basic_ostream` obiektu parametr do tego obiektu.|
|[Operator <<](#basic_ostream_operator_lt_lt)|Operacje zapisu do strumienia.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ostream >

**Namespace:** standardowe

## <a name="basic_ostream"></a>  basic_ostream::basic_ostream

Konstruuje `basic_ostream` obiektu.

```cpp
explicit basic_ostream(
    basic_streambuf<Elem, Tr>* strbuf,
    bool _Isstd = false);

basic_ostream(basic_ostream&& right);
```

### <a name="parameters"></a>Parametry

*strbuf*<br/>
Obiekt typu [basic_streambuf](../standard-library/basic-streambuf-class.md).

*_Isstd*<br/>
**wartość true,** Jeśli jest to Standardowy strumień; w przeciwnym razie **false**.

*right*<br/>
Odwołania rvalue do obiektu typu `basic_ostream`.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje klasę bazową, wywołując [init](../standard-library/basic-ios-class.md#init)(`strbuf`). Drugi Konstruktor inicjuje klasę bazową, wywołując [basic_ios::move](../standard-library/basic-ios-class.md#move)`(right)`.

### <a name="example"></a>Przykład

Zobacz przykład [basic_ofstream::basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream) Aby dowiedzieć się więcej na temat strumieni wyjściowych.

## <a name="flush"></a>  basic_ostream::Flush

Opróżnia bufor.

```cpp
basic_ostream<Elem, Tr>& flush();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu basic_ostream.

### <a name="remarks"></a>Uwagi

Jeśli [rdbuf —](../standard-library/basic-ios-class.md#rdbuf) nie jest wskaźnikiem typu null, wywołania funkcji **-> rdbuf —**[pubsync —](../standard-library/basic-streambuf-class.md#pubsync). Jeśli, zwraca wartość -1, funkcja wywołuje [setstate](../standard-library/basic-ios-class.md#setstate)(**badbit**). Zwraca  **\*to**.

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

## <a name="basic_ostream_operator_lt_lt"></a>  basic_ostream::operator&lt;&lt;

Operacje zapisu do strumienia.

```cpp
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

*nazwy pfn*<br/>
Wskaźnik funkcji.

*strbuf*<br/>
Wskaźnik do `stream_buf` obiektu.

*Val*<br/>
Element do zapisu do strumienia.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu basic_ostream.

### <a name="remarks"></a>Uwagi

\<Ostream > nagłówka definiuje również wiele operatorów globalnych wstawiania. Aby uzyskać więcej informacji, zobacz [operator <<](../standard-library/ostream-operators.md#op_lt_lt).

Pierwsza funkcja elementu członkowskiego zapewnia, że wyrażenie w formie `ostr << endl` wywołania [endl](../standard-library/ostream-functions.md#endl)**(ostr)**, a następnie zwraca  **\*to**. Drugi i trzeci funkcje upewnij się, że inne manipulatory, takich jak [szesnastkowy](../standard-library/ios-functions.md#hex), działają w podobny sposób. Pozostałe funkcje są wszystkie funkcje sformatowane wyniki.

Funkcja

```cpp
basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
```

wyodrębnia elementy z *strbuf*, jeśli *strbuf* nie jest wskaźnikiem typu null, a następnie wstawianie ich. Wyodrębnianie zatrzymuje się na końcu pliku, lub jeśli wyodrębniania zgłasza wyjątek (który jest zgłaszany ponownie). On również nie będzie możliwy, bez wyodrębniania w danym elemencie, jeśli wstawienie zakończy się niepowodzeniem. Jeśli funkcja wstawia żadnych elementów lub jeśli wyodrębniania zgłasza wyjątek, funkcja wywołuje [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**). W każdym przypadku, funkcja zwraca  **\*to**.

Funkcja

```cpp
basic_ostream<Elem, Tr>& operator<<(bool val);
```

Konwertuje `_Val` na wartość logiczną pola i wstawia go przez wywołanie metody [use_facet](../standard-library/basic-filebuf-class.md#open)**< num_put\<Elem, OutIt >**`(`[getloc —](../standard-library/ios-base-class.md#getloc)). [Umieść](#put)(**OutIt**([rdbuf —](../standard-library/basic-ios-class.md#rdbuf)),  **\*to**, `getloc`, **val**). W tym miejscu `OutIt` jest zdefiniowany jako [ostreambuf_iterator](../standard-library/ostreambuf-iterator-class.md)**\<Elem, Tr >**. Funkcja zwraca  **\*to**.

Funkcje

```cpp
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

Każda konwersja *val* na liczbowy pola, a następnie wstaw go przez wywołanie metody **use_facet < num_put\<Elem, OutIt >**(`getloc`). **Umieść**(**OutIt**(`rdbuf`),  **\*to**, `getloc`, **val**). W tym miejscu **OutIt** jest zdefiniowany jako **ostreambuf_iterator\<Elem, Tr >**. Funkcja zwraca  **\*to**.

Funkcje

```cpp
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
```

Każda konwersja *val* na liczbowy pola, a następnie wstaw go przez wywołanie metody **use_facet < num_put\<Elem, OutIt >**(`getloc`)**. Umieść**(**OutIt**(`rdbuf`),  **\*to**, `getloc`, **val**). W tym miejscu **OutIt** jest zdefiniowany jako **ostreambuf_iterator\<Elem, Tr >**. Funkcja zwraca  **\*to**.

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

## <a name="op_eq"></a>  basic_ostream::operator =

Przypisuje wartości dla podanych `basic_ostream` obiektu parametr do tego obiektu.

```cpp
basic_ostream& operator=(basic_ostream&& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
`rvalue` Odwołanie do `basic_ostream` obiektu.

### <a name="remarks"></a>Uwagi

Operator składowy wywołuje wymiany `(right)`.

## <a name="put"></a>  basic_ostream::Put

Umieszcza znak w strumieniu.

```cpp
basic_ostream<Elem, Tr>& put(char_type _Ch);
```

### <a name="parameters"></a>Parametry

*_Ch*<br/>
Znak.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu basic_ostream.

### <a name="remarks"></a>Uwagi

Funkcja niesformatowany dane wyjściowe wstawia element *_Ch*. Zwraca  **\*to**.

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

## <a name="seekp"></a>  basic_ostream::seekp

Zresetuj pozycję w strumieniu wyjściowym.

```cpp
basic_ostream<Elem, Tr>& seekp(pos_type _Pos);

basic_ostream<Elem, Tr>& seekp(off_type _Off, ios_base::seekdir _Way);
```

### <a name="parameters"></a>Parametry

*_Pos*<br/>
Pozycji w strumieniu.

*_Off*<br/>
Przesunięcie względem *_Way*.

*_Way*<br/>
Jedną z [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) wyliczenia.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu basic_ostream.

### <a name="remarks"></a>Uwagi

Jeśli [się nie powieść](../standard-library/basic-ios-class.md#fail) jest **false**, pierwszego wywołania funkcji elementu członkowskiego **newpos =** [rdbuf —](../standard-library/basic-ios-class.md#rdbuf) **->** [pubseekpos —](../standard-library/basic-streambuf-class.md#pubseekpos)(*_Pos*), w przypadku niektórych `pos_type` tymczasowy obiekt `newpos`. Jeśli `fail` ma wartość false, drugi wywołania funkcji **newpos = rdbuf — - >** [pubseekoff —](../standard-library/basic-streambuf-class.md#pubseekoff)(*_Off, _Way*). W obu przypadkach jeśli (`off_type`)**newpos ==** (`off_type`)(-1) (pozycjonowania operacja kończy się niepowodzeniem), a następnie funkcja wywołuje **istr.** [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**). Obie funkcje zwracają  **\*to**.

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

## <a name="sentry"></a>  basic_ostream::Sentry

Zagnieżdżona klasa opisująca obiekt, którego deklaracji struktury, funkcje sformatowane wyniki i funkcje niesformatowany danych wyjściowych.

sentry klasy {publicznej: jawne sentry (basic_ostream\<Elem, Tr > & _Ostr); operator bool() const; ~ sentry();};

### <a name="remarks"></a>Uwagi

Zagnieżdżona klasa opisująca obiekt, którego deklaracji struktury, funkcje sformatowane wyniki i funkcje niesformatowany danych wyjściowych. Jeśli **ostr.** [dobre](../standard-library/basic-ios-class.md#good) jest **true** i **ostr.** [powiązanie](../standard-library/basic-ios-class.md#tie) nie jest wskaźnikiem typu null, Konstruktor wywołuje **-> ostr.tie**[opróżniania](#flush). Konstruktor, następnie przechowuje wartość zwrócona przez obiekt `ostr.good` w `status`. Nowsze wywołanie `operator bool` zapewnia to przechowywanej wartości.

Jeśli `uncaught_exception` zwraca **false** i [flagi](../standard-library/ios-base-class.md#flags) **&** [unitbuf](../standard-library/ios-functions.md#unitbuf) jest różna od zera, wywołania destruktora [opróżniania](#flush).

## <a name="swap"></a>  basic_ostream::swap

Wymienia wartości to `basic_ostream` obiektu dla wartości podanych `basic_ostream`.

```cpp
void swap(basic_ostream& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Odwołanie do `basic_ostream` obiektu.

### <a name="remarks"></a>Uwagi

Wywołania funkcji elementu członkowskiego [basic_ios::swap](../standard-library/basic-ios-class.md#swap) `(right)` do wymiany zawartości obiektu do zawartości *prawo*.

## <a name="tellp"></a>  basic_ostream::tellp

Należy sporządzić raport pozycji w strumieniu wyjściowym.

```cpp
pos_type tellp();
```

### <a name="return-value"></a>Wartość zwracana

Pozycja w strumieniu wyjściowym.

### <a name="remarks"></a>Uwagi

Jeśli [się nie powieść](../standard-library/basic-ios-class.md#fail) jest **false**, funkcja elementu członkowskiego zwraca [rdbuf —](../standard-library/basic-ios-class.md#rdbuf) **->** [pubseekoff —](../standard-library/basic-streambuf-class.md#pubseekoff) (0, `cur`, **w**). W przeciwnym razie zwraca `pos_type`(-1).

### <a name="example"></a>Przykład

Zobacz [seekp —](#seekp) dla przykłady dotyczące używania `tellp`.

## <a name="write"></a>  basic_ostream::Write

Umieść znaków w strumieniu.

```cpp
basic_ostream<Elem, Tr>& write(const char_type* str, streamsize count);
```

### <a name="parameters"></a>Parametry

*Liczba*<br/>
Liczba znaków do umieszczenia w strumieniu.

*str*<br/>
Znaki, które można umieścić w strumieniu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu basic_ostream.

### <a name="remarks"></a>Uwagi

[Funkcji niesformatowany danych wyjściowych](../standard-library/basic-ostream-class.md) wstawia sekwencję *liczba* elementów, poczynając od *str*.

### <a name="example"></a>Przykład

Zobacz [streamsize](../standard-library/ios-typedefs.md#streamsize) dla przykłady dotyczące używania `write`.

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
