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
ms.openlocfilehash: 8715ae4816be9c8f1453b243d1c8d3574d8c97cf
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457866"
---
# <a name="basicostream-class"></a>basic_ostream — Klasa

Ta klasa szablonu opisuje obiekt, który kontroluje Wstawianie elementów i zakodowanych obiektów do buforu strumienia z elementami typu `Elem`, znanym również jako [char_type](../standard-library/basic-ios-class.md#char_type), których cechy znaku są określane przez klasę `Tr`, również znana jako [traits_type](../standard-library/basic-ios-class.md#traits_type).

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ostream : virtual public basic_ios<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem*\
A `char_type`.

*Zdawczy*\
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

Zobacz przykład dla [klasy basic_ofstream](../standard-library/basic-ofstream-class.md) , aby dowiedzieć się więcej o strumieniach wyjściowych.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_ostream](#basic_ostream)|Konstruuje `basic_ostream` obiekt.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[flush](#flush)|Opróżnia bufor.|
|[put](#put)|Umieszcza znak w strumieniu.|
|[seekp](#seekp)|Resetuje pozycję w strumieniu wyjściowym.|
|[WartownikDźwięków](#sentry)|Klasa zagnieżdżona opisuje obiekt, którego struktura deklaracji ma sformatowane funkcje wyjściowe i niesformatowane funkcje wyjściowe.|
|[swap](#swap)|Wymienia wartości tego `basic_ostream` obiektu dla podanego `basic_ostream` obiektu.|
|[tellp](#tellp)|Pozycja raportów w strumieniu wyjściowym.|
|[write](#write)|Umieszcza znaki w strumieniu.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Przypisuje wartość podanego `basic_ostream` parametru obiektu do tego obiektu.|
|[< operatora <](#basic_ostream_operator_lt_lt)|Zapisuje dane w strumieniu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ostream >

**Przestrzeń nazw:** std

## <a name="basic_ostream"></a>basic_ostream::basic_ostream

Konstruuje `basic_ostream` obiekt.

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

*Kliknij*\
Odwołanie rvalue do obiektu typu `basic_ostream`.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje klasę bazową, wywołując metodę [init](../standard-library/basic-ios-class.md#init)(`strbuf`). Drugi Konstruktor inicjuje klasę bazową przez wywołanie [basic_ios:: Move](../standard-library/basic-ios-class.md#move)`(right)`.

### <a name="example"></a>Przykład

Zobacz przykład dla [basic_ofstream:: basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream) , aby dowiedzieć się więcej o strumieniach wyjściowych.

## <a name="flush"></a>basic_ostream:: Flush

Opróżnia bufor.

```cpp
basic_ostream<Elem, Tr>& flush();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu basic_ostream.

### <a name="remarks"></a>Uwagi

Jeśli [rdbuf](../standard-library/basic-ios-class.md#rdbuf) nie jest pustym wskaźnikiem, funkcja wywołuje **rdbuf->** [pubsync](../standard-library/basic-streambuf-class.md#pubsync). Jeśli zwraca wartość-1, funkcja wywołuje metodę [setstate](../standard-library/basic-ios-class.md#setstate)(**badbit**). **Zwraca\*to**.

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

*PFN*\
Wskaźnik funkcji.

*strbuf*\
Wskaźnik do `stream_buf` obiektu.

*użyte*\
Element do zapisu w strumieniu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu basic_ostream.

### <a name="remarks"></a>Uwagi

Nagłówek \<> ostream definiuje także kilka globalnych operatorów wstawiania. Aby uzyskać więcej informacji, zobacz [operator < <](../standard-library/ostream-operators.md#op_lt_lt).

`ostr << endl` Pierwsza funkcja członkowska gwarantuje, że wyrażenie formularza wywołuje [endl](../standard-library/ostream-functions.md#endl) **(ostr)** , a następnie zwraca  **\*to**. Drugie i trzecie funkcje zapewniają, że inne manipulowania, takie jak [szesnastkowo](../standard-library/ios-functions.md#hex), zachowują się podobnie. Pozostałe funkcje to wszystkie sformatowane funkcje wyjściowe.

Funkcja

```cpp
basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
```

wyodrębnia elementy z *strbuf*, jeśli *strbuf* nie jest wskaźnikiem null i wstawia je. Wyodrębnianie kończy się na końcu pliku lub jeśli wyodrębnianie zgłasza wyjątek (który jest ponownie zgłaszany). Zatrzymuje również, bez wyodrębniania elementu, w przypadku niepowodzenia wstawiania. Jeśli funkcja nie wstawia żadnych elementów lub jeśli wyodrębnianie zgłasza wyjątek, funkcja wywołuje metodę setstate [](../standard-library/basic-ios-class.md#setstate)(**failbit**). W każdym przypadku funkcja zwraca  **\*ten**wynik.

Funkcja

```cpp
basic_ostream<Elem, Tr>& operator<<(bool val);
```

Konwertuje `_Val` do pola Boolean i wstawia je przez wywołanie [use_facet](../standard-library/basic-filebuf-class.md#open) **< num_put\<elem, OutIt >** [](../standard-library/ios-base-class.md#getloc)`(`getloc). [Umieść](#put) (**OutIt**([rdbuf](../standard-library/basic-ios-class.md#rdbuf) )`getloc`,  **\*this**,, **Val**). W tym miejscu definiuje [](../standard-library/ostreambuf-iterator-class.md) sięjakoostreambuf_iteratorelem,TR`OutIt` **\<>** . Funkcja zwraca  **\*ten**wynik.

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

Każda Konwertuj wartość *Val* do pola liczbowego i Wstaw ją przez wywołanie **use_facet <\<num_put elem, OutIt >** (`getloc`). **Umieść** (**OutIt**(`rdbuf` **), \*this** , Val) `getloc`. Tutaj **OutIt** został zdefiniowany jako **ostreambuf_iterator\<elem, TR >** . Funkcja zwraca  **\*ten**wynik.

Funkcje

```cpp
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
```

Każda Konwertuj wartość *Val* do pola liczbowego i Wstaw ją przez wywołanie **use_facet <\<num_put elem, OutIt >** (`getloc`) **. Put**(**OutIt**(`rdbuf`),  **\*this**, `getloc`, **Val**). Tutaj **OutIt** został zdefiniowany jako **ostreambuf_iterator\<elem, TR >** . Funkcja zwraca  **\*ten**wynik.

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

Przypisuje wartości dla podanego `basic_ostream` parametru obiektu do tego obiektu.

```cpp
basic_ostream& operator=(basic_ostream&& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
`rvalue` Odwołanie`basic_ostream` do obiektu.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego wywołuje `(right)`zamianę.

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

Niesformatowana funkcja wyjściowa wstawia element *_Ch*. **Zwraca\*to**.

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

## <a name="seekp"></a>basic_ostream::seekp

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
Jedno z [ios_base:: seekdir](../standard-library/ios-base-class.md#seekdir) .

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu basic_ostream.

### <a name="remarks"></a>Uwagi

Jeśli [błąd](../standard-library/basic-ios-class.md#fail) ma **wartość false**, Pierwsza funkcja członkowska **wywołuje newpos =** [rdbuf](../standard-library/basic-ios-class.md#rdbuf) **->** [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos)( *_Pos*), dla `pos_type` pewnego obiektu `newpos`tymczasowego. Jeśli `fail` ma wartość false, druga funkcja wywołuje **newpos = rdbuf->** [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)( *_Off, _Way*). W obu przypadkach, jeśli (`off_type`)**newpos = =** (`off_type`) (-1) (operacja pozycjonowania zakończy się niepowodzeniem), funkcja wywołuje **ISTR.** [setstate](../standard-library/basic-ios-class.md#setstate) (**failbit**). Obie funkcje zwracają  **\*ten**.

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

Klasa zagnieżdżona opisuje obiekt, którego struktura deklaracji ma sformatowane funkcje wyjściowe i niesformatowane funkcje wyjściowe. Jeśli **ostr.** [dobre](../standard-library/basic-ios-class.md#good) jest **prawdziwe** i **ostr.** [powiązanie](../standard-library/basic-ios-class.md#tie) nie jest wskaźnikiem o wartości null, Konstruktor wywołuje **ostr. krawat->** [Flush](#flush). Następnie Konstruktor przechowuje wartość zwracaną przez `ostr.good`. `status` Późniejsze wywołanie w celu `operator bool` dostarczenia tej przechowywanej wartości.

Jeśli `uncaught_exception` zwraca **wartość false** , a [flagi](../standard-library/ios-base-class.md#flags) **&** [unitbuf](../standard-library/ios-functions.md#unitbuf) mają wartość różną od zera, [](#flush)destruktor wywołuje opróżnianie.

## <a name="swap"></a>basic_ostream:: swap

Wymienia wartości tego `basic_ostream` obiektu dla wartości podanej `basic_ostream`.

```cpp
void swap(basic_ostream& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Odwołanie do `basic_ostream` obiektu.

### <a name="remarks"></a>Uwagi

Funkcja członkowska wywołuje [basic_ios:: swap](../standard-library/basic-ios-class.md#swap) `(right)` , aby wymienić zawartość tego obiektu na zawartość z *prawej strony*.

## <a name="tellp"></a>basic_ostream::tellp

Pozycja raportu w strumieniu wyjściowym.

```cpp
pos_type tellp();
```

### <a name="return-value"></a>Wartość zwracana

Pozycja w strumieniu wyjściowym.

### <a name="remarks"></a>Uwagi

Jeśli [błąd](../standard-library/basic-ios-class.md#fail) ma **wartość false**, funkcja członkowska zwraca [rdbuf](../standard-library/basic-ios-class.md#rdbuf) **->** [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(0 `cur`,, **in**). W przeciwnym razie zwraca `pos_type`(-1).

### <a name="example"></a>Przykład

Zobacz [seekp](#seekp) , aby zapoznać się `tellp`z przykładem.

## <a name="write"></a>basic_ostream:: Write

Umieszczanie znaków w strumieniu.

```cpp
basic_ostream<Elem, Tr>& write(const char_type* str, streamsize count);
```

### <a name="parameters"></a>Parametry

*liczbą*\
Liczba znaków, które mają zostać umieszczone w strumieniu.

*str*\
Znaki, które mają zostać umieszczone w strumieniu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu basic_ostream.

### <a name="remarks"></a>Uwagi

Niesformatowana [funkcja wyjściowa](../standard-library/basic-ostream-class.md) wstawia sekwencję elementów *Count* , zaczynając od *str*.

### <a name="example"></a>Przykład

Zobacz [dane StreamSize](../standard-library/ios-typedefs.md#streamsize) , aby zapoznać się `write`z przykładem.

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
