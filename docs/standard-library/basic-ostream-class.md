---
title: basic_ostream — Klasa
ms.date: 03/27/2019
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
ms.openlocfilehash: 9025d595e79eed9f81aff77b931a2585359a8c3a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78874837"
---
# <a name="basic_ostream-class"></a>basic_ostream — Klasa

Ten szablon klasy opisuje obiekt, który kontroluje Wstawianie elementów i zakodowanych obiektów do buforu strumienia z elementami typu `Elem`, znanym również jako [char_type](../standard-library/basic-ios-class.md#char_type), których cechy znaków są określane przez `Tr`klasy, znane także jako [traits_type](../standard-library/basic-ios-class.md#traits_type).

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ostream : virtual public basic_ios<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem*\
Klasa `char_type`.

\ *TR*
Znak `traits_type`.

## <a name="remarks"></a>Uwagi

Większość funkcji Członkowskich, które [< operator](#basic_ostream_operator_lt_lt) przeciążania < są sformatowanymi funkcjami wyjściowymi. Są one zgodne ze wzorcem:

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

Dwie inne funkcje członkowskie są niesformatowanymi funkcjami wyjściowymi. Są one zgodne ze wzorcem:

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

Obie grupy funkcji wywołuje metodę [setstate](../standard-library/basic-ios-class.md#setstate)(**badbit**), Jeśli napotkają błąd podczas wstawiania elementów.

Obiekt klasy basic_istream\< **elem**, **TR**> przechowuje tylko wirtualny publiczny obiekt podstawowy klasy [basic_ios](../standard-library/basic-ios-class.md) **\<elem**, **TR >** .

## <a name="example"></a>Przykład

Zapoznaj się z przykładem [klasy basic_ofstream](../standard-library/basic-ofstream-class.md) , aby dowiedzieć się więcej o strumieniach wyjściowych.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_ostream](#basic_ostream)|Konstruuje obiekt `basic_ostream`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[płukan](#flush)|Opróżnia bufor.|
|[Ubrani](#put)|Umieszcza znak w strumieniu.|
|[seekp](#seekp)|Resetuje pozycję w strumieniu wyjściowym.|
|[WartownikDźwięków](#sentry)|Klasa zagnieżdżona opisuje obiekt, którego struktura deklaracji ma sformatowane funkcje wyjściowe i niesformatowane funkcje wyjściowe.|
|[wymiany](#swap)|Wymienia wartości tego obiektu `basic_ostream` dla tych z podanego `basic_ostream` obiektu.|
|[tellp](#tellp)|Pozycja raportów w strumieniu wyjściowym.|
|[write](#write)|Umieszcza znaki w strumieniu.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator =](#op_eq)|Przypisuje do tego obiektu wartość podanego parametru obiektu `basic_ostream`.|
|[< operatora <](#basic_ostream_operator_lt_lt)|Zapisuje dane w strumieniu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ostream >

**Przestrzeń nazw:** std

## <a name="basic_ostream"></a>basic_ostream:: basic_ostream

Konstruuje obiekt `basic_ostream`.

```cpp
explicit basic_ostream(
    basic_streambuf<Elem, Tr>* strbuf,
    bool _Isstd = false);

basic_ostream(basic_ostream&& right);
```

### <a name="parameters"></a>Parametry

*strbuf*\
Obiekt typu [basic_streambuf](../standard-library/basic-streambuf-class.md).

*_Isstd*\
**prawda** , jeśli jest to strumień standardowy; w przeciwnym razie **false**.

*prawa*\
Odwołanie rvalue do obiektu typu `basic_ostream`.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje klasę bazową, wywołując metodę [init](../standard-library/basic-ios-class.md#init)(`strbuf`). Drugi Konstruktor inicjuje klasę bazową, wywołując [basic_ios:: move](../standard-library/basic-ios-class.md#move)`(right)`.

### <a name="example"></a>Przykład

Aby dowiedzieć się więcej o strumieniach wyjściowych, zobacz przykład dla [basic_ofstream:: basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream) .

## <a name="flush"></a>basic_ostream:: Flush

Opróżnia bufor.

```cpp
basic_ostream<Elem, Tr>& flush();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu basic_ostream.

### <a name="remarks"></a>Uwagi

Jeśli [rdbuf](../standard-library/basic-ios-class.md#rdbuf) nie jest pustym wskaźnikiem, funkcja wywołuje **rdbuf->** [pubsync](../standard-library/basic-streambuf-class.md#pubsync). Jeśli zwraca wartość-1, funkcja wywołuje metodę [setstate](../standard-library/basic-ios-class.md#setstate)(**badbit**). Zwraca **\*to**.

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

## <a name="basic_ostream_operator_lt_lt"></a>basic_ostream:: operator&lt;&lt;

Zapisuje dane w strumieniu.

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

*Pfn*\
Wskaźnik funkcji.

*strbuf*\
Wskaźnik do obiektu `stream_buf`.

*val*\
Element do zapisu w strumieniu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu basic_ostream.

### <a name="remarks"></a>Uwagi

Nagłówek \<ostream > definiuje także kilka globalnych operatorów wstawiania. Aby uzyskać więcej informacji, zobacz [operator < <](../standard-library/ostream-operators.md#op_lt_lt).

Pierwsza funkcja członkowska gwarantuje, że wyrażenie formularza `ostr << endl` wywołuje [endl](../standard-library/ostream-functions.md#endl) **(ostr)** , a następnie zwraca **\*to**. Drugie i trzecie funkcje zapewniają, że inne manipulowania, takie jak [szesnastkowo](../standard-library/ios-functions.md#hex), zachowują się podobnie. Pozostałe funkcje to wszystkie sformatowane funkcje wyjściowe.

Funkcja

```cpp
basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
```

wyodrębnia elementy z *strbuf*, jeśli *strbuf* nie jest wskaźnikiem null i wstawia je. Wyodrębnianie kończy się na końcu pliku lub jeśli wyodrębnianie zgłasza wyjątek (który jest ponownie zgłaszany). Zatrzymuje również, bez wyodrębniania elementu, w przypadku niepowodzenia wstawiania. Jeśli funkcja nie wstawia żadnych elementów lub jeśli wyodrębnianie zgłasza wyjątek, funkcja wywołuje metodę [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**). W każdym przypadku funkcja zwraca **\*to**.

Funkcja

```cpp
basic_ostream<Elem, Tr>& operator<<(bool val);
```

Konwertuje `_Val` do pola logicznego i wstawia je przez wywołanie [use_facet](../standard-library/basic-filebuf-class.md#open) **< num_put\<Elem, OutIt >** `(`[getloc](../standard-library/ios-base-class.md#getloc)). [Put](#put)(**OutIt**([rdbuf](../standard-library/basic-ios-class.md#rdbuf)), **\*this**, `getloc`, **Val**). W tym miejscu `OutIt` jest definiowana [ostreambuf_iterator](../standard-library/ostreambuf-iterator-class.md) **\<Elem, TR >** . Funkcja zwraca **\*** .

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

Każda Konwertuj wartość *Val* do pola liczbowego i Wstaw ją, wywołując **use_facet < num_put\<Elem, OutIt >** (`getloc`). **Put**(`rdbuf`**OutIt**), **\*to**, `getloc`, **Val**). W tym miejscu **OutIt** jest zdefiniowany jako **ostreambuf_iterator\<Elem, TR >** . Funkcja zwraca **\*** .

Funkcje

```cpp
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
```

Każda Konwertuj wartość *Val* do pola liczbowego i Wstaw ją, **wywołując use_facet < num_put\<Elem, OutIt >** (`getloc`) **. Put**(**OutIt**(`rdbuf`), **\*to**, `getloc`, **Val**). W tym miejscu **OutIt** jest zdefiniowany jako **ostreambuf_iterator\<Elem, TR >** . Funkcja zwraca **\*** .

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

## <a name="op_eq"></a>basic_ostream:: operator =

Przypisuje do tego obiektu wartości dla podanego parametru obiektu `basic_ostream`.

```cpp
basic_ostream& operator=(basic_ostream&& right);
```

### <a name="parameters"></a>Parametry

*prawa*\
Odwołanie `rvalue` do obiektu `basic_ostream`.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego wywołuje zamianę `(right)`.

## <a name="put"></a>basic_ostream::p UT

Umieszcza znak w strumieniu.

```cpp
basic_ostream<Elem, Tr>& put(char_type _Ch);
```

### <a name="parameters"></a>Parametry

*_Ch*\
Znak.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu basic_ostream.

### <a name="remarks"></a>Uwagi

Niesformatowana funkcja wyjściowa wstawia element *_Ch*. Zwraca **\*to**.

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

## <a name="seekp"></a>basic_ostream:: seekp

Resetowanie pozycji w strumieniu wyjściowym.

```cpp
basic_ostream<Elem, Tr>& seekp(pos_type _Pos);

basic_ostream<Elem, Tr>& seekp(off_type _Off, ios_base::seekdir _Way);
```

### <a name="parameters"></a>Parametry

*_Pos*\
Pozycja w strumieniu.

*_Off*\
Przesunięcie względem *_Way*.

*_Way*\
Jeden z [ios_base:: seekdir](../standard-library/ios-base-class.md#seekdir) Enumerations.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu basic_ostream.

### <a name="remarks"></a>Uwagi

W przypadku [niepowodzenia](../standard-library/basic-ios-class.md#fail) ma **wartość false**, Pierwsza funkcja członkowska wywołuje **newpos =** [rdbuf](../standard-library/basic-ios-class.md#rdbuf) **->** [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos)( *_Pos*) dla niektórych `pos_type` tymczasowych obiektów `newpos`. Jeśli `fail` ma wartość false, druga funkcja wywołuje **newpos = rdbuf->** [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)( *_Off, _Way*). W obu przypadkach, jeśli (`off_type`)**newpos = =** (`off_type`) (-1) (operacja pozycjonowania zakończy się niepowodzeniem), funkcja wywołuje **ISTR.** [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**). Obie funkcje zwracają **\*to**.

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

## <a name="sentry"></a>basic_ostream:: Sentry

Klasa zagnieżdżona opisuje obiekt, którego struktura deklaracji ma sformatowane funkcje wyjściowe i niesformatowane funkcje wyjściowe.

Klasa Sentry {Public: Explicit Sentry (basic_ostream\<elem, TR > & _Ostr); operator bool () const; ~ Sentry ();};

### <a name="remarks"></a>Uwagi

Klasa zagnieżdżona opisuje obiekt, którego struktura deklaracji ma sformatowane funkcje wyjściowe i niesformatowane funkcje wyjściowe. Jeśli **ostr.** [dobre](../standard-library/basic-ios-class.md#good) jest **prawdziwe** i **ostr.** [powiązanie](../standard-library/basic-ios-class.md#tie) nie jest wskaźnikiem o wartości null, Konstruktor wywołuje **ostr. krawat->** [Flush](#flush). Konstruktor zapisuje wartość zwracaną przez `ostr.good` w `status`. Późniejsze wywołanie `operator bool` dostarcza tę wartość przechowywaną.

Jeśli `uncaught_exception` zwraca **wartość false** , a [flagi](../standard-library/ios-base-class.md#flags) **&** [unitbuf](../standard-library/ios-functions.md#unitbuf) mają wartość różną od zera, destruktor wywołuje [opróżnianie](#flush).

## <a name="swap"></a>basic_ostream:: swap

Wymienia wartości tego obiektu `basic_ostream` dla wartości podanej `basic_ostream`.

```cpp
void swap(basic_ostream& right);
```

### <a name="parameters"></a>Parametry

*prawa*\
Odwołanie do obiektu `basic_ostream`.

### <a name="remarks"></a>Uwagi

Funkcja członkowska wywołuje [basic_ios:: swap](../standard-library/basic-ios-class.md#swap)`(right)`, aby wymienić zawartość tego obiektu na zawartość z *prawej strony*.

## <a name="tellp"></a>basic_ostream:: tellp

Pozycja raportu w strumieniu wyjściowym.

```cpp
pos_type tellp();
```

### <a name="return-value"></a>Wartość zwracana

Pozycja w strumieniu wyjściowym.

### <a name="remarks"></a>Uwagi

Jeśli [błąd](../standard-library/basic-ios-class.md#fail) ma **wartość false**, funkcja członkowska zwraca [rdbuf](../standard-library/basic-ios-class.md#rdbuf) **->** [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(0, `cur`, **in**). W przeciwnym razie zwraca `pos_type`(-1).

### <a name="example"></a>Przykład

Zobacz [seekp](#seekp) , aby zapoznać się z przykładem przy użyciu `tellp`.

## <a name="write"></a>basic_ostream:: Write

Umieszczanie znaków w strumieniu.

```cpp
basic_ostream<Elem, Tr>& write(const char_type* str, streamsize count);
```

### <a name="parameters"></a>Parametry

*liczba*\
Liczba znaków, które mają zostać umieszczone w strumieniu.

*str*\
Znaki, które mają zostać umieszczone w strumieniu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu basic_ostream.

### <a name="remarks"></a>Uwagi

[Niesformatowana funkcja wyjściowa](../standard-library/basic-ostream-class.md) wstawia sekwencję elementów *Count* , zaczynając od *str*.

### <a name="example"></a>Przykład

Zobacz [dane StreamSize](../standard-library/ios-typedefs.md#streamsize) , aby zapoznać się z przykładem przy użyciu `write`.

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
\ [programowania iostream](../standard-library/iostream-programming.md)
[Konwencje iostream](../standard-library/iostreams-conventions.md)
