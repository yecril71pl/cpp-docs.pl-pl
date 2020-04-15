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
ms.openlocfilehash: e074eb30d31c316411dd43f9a7a019defb64e9fe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376762"
---
# <a name="basic_ostream-class"></a>basic_ostream — Klasa

Ten szablon klasy opisuje obiekt, który steruje wstawianiem elementów i `Elem`zakodowanych obiektów do buforu strumienia z elementami typu , znanymi również jako [char_type](../standard-library/basic-ios-class.md#char_type), których cechy charakteru są określane przez klasę, `Tr`znany również jako [traits_type](../standard-library/basic-ios-class.md#traits_type).

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ostream : virtual public basic_ios<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem*\
Klasa `char_type`.

*Tr*\
Znak `traits_type`.

## <a name="remarks"></a>Uwagi

Większość funkcji elementów członkowskich, które [<<operatora](#basic_ostream_operator_lt_lt) przeciążenia są sformatowane funkcje wyjściowe. Podążają za wzorem:

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

Dwie inne funkcje członkowskie są niesformatowane funkcje wyjściowe. Podążają za wzorem:

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

Obie grupy funkcji wywołać [setstate](../standard-library/basic-ios-class.md#setstate)**(badbit),** jeśli napotkają błąd podczas wstawiania elementów.

Obiekt\< klasy basic_istream **Elem**, **Tr**> przechowuje tylko wirtualny publiczny obiekt podstawowy klasy [basic_ios](../standard-library/basic-ios-class.md)**\<Elem**, **Tr>**.

## <a name="example"></a>Przykład

Zobacz przykład [basic_ofstream Class,](../standard-library/basic-ofstream-class.md) aby dowiedzieć się więcej o strumieniach danych wyjściowych.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Basic_ostream](#basic_ostream)|Konstruuje `basic_ostream` obiekt.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[opróżnianie](#flush)|Opróżnia bufor.|
|[Umieścić](#put)|Umieszcza znak w strumieniu.|
|[seekp](#seekp)|Resetuje pozycję w strumieniu wyjściowym.|
|[Sentry](#sentry)|Klasa zagnieżdżona opisuje obiekt, którego deklaracja struktury sformatowanych funkcji wyjściowych i niesformatowanych funkcji wyjściowych.|
|[Wymiany](#swap)|Wymienia wartości tego `basic_ostream` obiektu na wartości `basic_ostream` podanego obiektu.|
|[tellp (tellp)](#tellp)|Raportuje pozycję w strumieniu wyjściowym.|
|[Napisz](#write)|Umieszcza znaki w strumieniu.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Przypisuje wartość podanego `basic_ostream` parametru obiektu do tego obiektu.|
|[<<operatora](#basic_ostream_operator_lt_lt)|Zapisuje do strumienia.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> ostream

**Przestrzeń nazw:** std

## <a name="basic_ostreambasic_ostream"></a><a name="basic_ostream"></a>basic_ostream::basic_ostream

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
**true,** jeśli jest to standardowy strumień; w przeciwnym razie **false**.

*Prawo*\
Odwołanie do rvalue do `basic_ostream`obiektu typu .

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor inicjuje klasę podstawową, wywołując [init](../standard-library/basic-ios-class.md#init)(`strbuf`). Drugi konstruktor inicjuje klasę podstawową, wywołując [basic_ios::move](../standard-library/basic-ios-class.md#move)`(right)`.

### <a name="example"></a>Przykład

Zobacz przykład [basic_ofstream::basic_ofstream,](../standard-library/basic-ofstream-class.md#basic_ofstream) aby dowiedzieć się więcej o strumieniach danych wyjściowych.

## <a name="basic_ostreamflush"></a><a name="flush"></a>basic_ostream::flush

Opróżnia bufor.

```cpp
basic_ostream<Elem, Tr>& flush();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu basic_ostream.

### <a name="remarks"></a>Uwagi

Jeśli [rdbuf](../standard-library/basic-ios-class.md#rdbuf) nie jest wskaźnikiem null, funkcja wywołuje **rdbuf->** [pubsync](../standard-library/basic-streambuf-class.md#pubsync). Jeśli zwraca wartość -1, funkcja wywołuje [setstate](../standard-library/basic-ios-class.md#setstate)(**badbit**). Zwraca ** \*to**.

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

## <a name="basic_ostreamoperatorltlt"></a><a name="basic_ostream_operator_lt_lt"></a>basic_ostream::operator&lt;&lt;

Zapisuje do strumienia.

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
Wskaźnik do `stream_buf` obiektu.

*Val*\
Element do zapisu w strumieniu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu basic_ostream.

### <a name="remarks"></a>Uwagi

Nagłówek \<> ostream definiuje również kilka globalnych operatorów wstawiania. Aby uzyskać więcej informacji, zobacz [<<operatora ](../standard-library/ostream-operators.md#op_lt_lt).

Funkcja pierwszego elementu członkowskiego zapewnia, że `ostr << endl` wyrażenie formularza wywołuje [endl](../standard-library/ostream-functions.md#endl)**(ostr),** a następnie zwraca ** \*to**. Druga i trzecia funkcja zapewniają, że inne manipulatory, takie jak [hex,](../standard-library/ios-functions.md#hex)zachowują się podobnie. Pozostałe funkcje to wszystkie sformatowane funkcje wyjściowe.

Funkcja

```cpp
basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
```

wyodrębnia elementy z *strbuf*, jeśli *strbuf* nie jest wskaźnikiem null i wstawia je. Wyodrębnianie zatrzymuje się na końcu pliku lub jeśli wyodrębnianie zgłasza wyjątek (który jest rethrown). Zatrzymuje się również, bez wyodrębniania danego elementu, jeśli wstawienie nie powiedzie się. Jeśli funkcja nie wstawia żadnych elementów lub jeśli wyodrębnianie zgłasza wyjątek, funkcja wywołuje [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**). W każdym przypadku funkcja ** \*** zwraca to .

Funkcja

```cpp
basic_ostream<Elem, Tr>& operator<<(bool val);
```

konwertuje na pole `_Val` logiczne i wstawia je, wywołując [use_facet](../standard-library/basic-filebuf-class.md#open)<num_put** \<Elem, OutIt>** `(` [getloc](../standard-library/ios-base-class.md#getloc)). [put](#put)(**OutIt**( ** \***[rdbuf](../standard-library/basic-ios-class.md#rdbuf)), to , `getloc` **val**). Tutaj, `OutIt` jest zdefiniowany jako [ostreambuf_iterator](../standard-library/ostreambuf-iterator-class.md)**\<Elem, Tr>**. Funkcja zwraca ** \*tę**wartość .

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

każdy konwertować *val* do pola liczbowego i wstawić go, wywołując **use_facet<num_put\<Elem, OutIt>**(`getloc`). **put**(**OutIt**`rdbuf`( `getloc`), ** \*to**, **val**). Tutaj, **OutIt** jest zdefiniowany jako **ostreambuf_iterator\<Elem, Tr>**. Funkcja zwraca ** \*tę**wartość .

Funkcje

```cpp
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
```

każdy przekonwertować *val* do pola numerycznego i wstawić go, wywołując **use_facet<num_put\<Elem, OutIt>**( ** \***`getloc`) `getloc`.**put**(**OutIt**(`rdbuf`), to , **val**). Tutaj, **OutIt** jest zdefiniowany jako **ostreambuf_iterator\<Elem, Tr>**. Funkcja zwraca ** \*tę**wartość .

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

## <a name="basic_ostreamoperator"></a><a name="op_eq"></a>basic_ostream::operator=

Przypisuje wartości podanego `basic_ostream` parametru obiektu do tego obiektu.

```cpp
basic_ostream& operator=(basic_ostream&& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Odwołanie `rvalue` do `basic_ostream` obiektu.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego `(right)`wywołuje swap .

## <a name="basic_ostreamput"></a><a name="put"></a>basic_ostream::put

Umieszcza znak w strumieniu.

```cpp
basic_ostream<Elem, Tr>& put(char_type _Ch);
```

### <a name="parameters"></a>Parametry

*_ch*\
Znak.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu basic_ostream.

### <a name="remarks"></a>Uwagi

Niesformatowana funkcja wyjściowa wstawia element *_Ch*. Zwraca ** \*to**.

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

## <a name="basic_ostreamseekp"></a><a name="seekp"></a>basic_ostream::seekp

Zresetuj pozycję w strumieniu wyjściowym.

```cpp
basic_ostream<Elem, Tr>& seekp(pos_type _Pos);

basic_ostream<Elem, Tr>& seekp(off_type _Off, ios_base::seekdir _Way);
```

### <a name="parameters"></a>Parametry

*_Pos*\
Pozycja w strumieniu.

*_off*\
Przesunięcie względem *_Way*.

*_way*\
Jednym z [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) wyliczenia.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu basic_ostream.

### <a name="remarks"></a>Uwagi

Jeśli [niepowodzenie](../standard-library/basic-ios-class.md#fail) jest **fałszywe,** pierwsza funkcja elementu członkowskiego wywołuje **newpos =** [rdbuf](../standard-library/basic-ios-class.md#rdbuf) **->** [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos)(*_Pos*), dla niektórych obiektów `pos_type` `newpos`tymczasowych . Jeśli `fail` jest false, druga funkcja wywołuje **newpos = rdbuf->** [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(*_Off, _Way*). W obu przypadkach,`off_type`jeśli ( )`off_type`**newpos ==** ( )(-1) (operacja pozycjonowania kończy się niepowodzeniem), funkcja wywołuje **istr.** [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**). Obie funkcje zwracają ** \*to**.

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

## <a name="basic_ostreamsentry"></a><a name="sentry"></a>basic_ostream::działko

Klasa zagnieżdżona opisuje obiekt, którego deklaracja struktury sformatowanych funkcji wyjściowych i niesformatowanych funkcji wyjściowych.

class sentry { public: explicit sentry(basic_ostream\<Elem, Tr>& _Ostr); operator bool() const; ~działko(); };

### <a name="remarks"></a>Uwagi

Klasa zagnieżdżona opisuje obiekt, którego deklaracja struktury sformatowanych funkcji wyjściowych i niesformatowanych funkcji wyjściowych. Jeśli **ostr.** [dobra](../standard-library/basic-ios-class.md#good) jest **prawdziwa** i **ostr.** [tie](../standard-library/basic-ios-class.md#tie) nie jest wskaźnikiem zerowym, konstruktor wywołuje **ostr.tie->** [flush](#flush). Konstruktor następnie przechowuje `ostr.good` wartość `status`zwróconą przez w . Późniejsze wywołanie, aby `operator bool` dostarczyć tę przechowywaną wartość.

Jeśli `uncaught_exception` zwraca **false** i [flagi](../standard-library/ios-base-class.md#flags) **&** [unitbuf](../standard-library/ios-functions.md#unitbuf) jest niezerowy, destruktor wywołuje [flush](#flush).

## <a name="basic_ostreamswap"></a><a name="swap"></a>basic_ostream::swap

Wymienia wartości tego `basic_ostream` obiektu dla wartości `basic_ostream`podanych .

```cpp
void swap(basic_ostream& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Odwołanie do `basic_ostream` obiektu.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego wywołuje [basic_ios::swap,](../standard-library/basic-ios-class.md#swap) `(right)` aby wymienić zawartość tego obiektu na zawartość *praw .*

## <a name="basic_ostreamtellp"></a><a name="tellp"></a>basic_ostream::tellp

Pozycja raportu w strumieniu wyjściowym.

```cpp
pos_type tellp();
```

### <a name="return-value"></a>Wartość zwracana

Położenie w strumieniu wyjściowym.

### <a name="remarks"></a>Uwagi

Jeśli [niepowodzenie](../standard-library/basic-ios-class.md#fail) jest **false**, funkcja elementu członkowskiego zwraca [rdbuf](../standard-library/basic-ios-class.md#rdbuf) **->** [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(0, `cur`, **w**). W przeciwnym `pos_type`razie zwraca (-1).

### <a name="example"></a>Przykład

Zobacz [szukaj](#seekp) przykładu `tellp`przy użyciu .

## <a name="basic_ostreamwrite"></a><a name="write"></a>basic_ostream::zapis

Umieść znaki w strumieniu.

```cpp
basic_ostream<Elem, Tr>& write(const char_type* str, streamsize count);
```

### <a name="parameters"></a>Parametry

*Liczba*\
Liczba znaków do umieszczenia w strumieniu.

*Str*\
Znaki, które można umieścić w strumieniu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu basic_ostream.

### <a name="remarks"></a>Uwagi

[Niesformatowana funkcja wyjściowa](../standard-library/basic-ostream-class.md) wstawia sekwencję elementów *zliczania* rozpoczynających się od *ul.*

### <a name="example"></a>Przykład

Zobacz [streamsize](../standard-library/ios-typedefs.md#streamsize) na `write`przykład przy użyciu .

## <a name="see-also"></a>Zobacz też

[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
