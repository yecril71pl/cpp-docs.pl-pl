---
title: basic_istream — Klasa
ms.date: 11/04/2016
f1_keywords:
- istream/std::basic_istream
- istream/std::basic_istream::gcount
- istream/std::basic_istream::get
- istream/std::basic_istream::getline
- 'istream/std::basic_istream::'
- istream/std::basic_istream::peek
- istream/std::basic_istream::putback
- istream/std::basic_istream::read
- istream/std::basic_istream::readsome
- istream/std::basic_istream::seekg
- istream/std::basic_istream::sentry
- istream/std::basic_istream::swap
- istream/std::basic_istream::sync
- istream/std::basic_istream::tellg
- istream/std::basic_istream::unget
helpviewer_keywords:
- std::basic_istream [C++]
- std::basic_istream [C++], gcount
- std::basic_istream [C++], get
- std::basic_istream [C++], getline
- std::basic_istream [C++], OVERWRITE
- std::basic_istream [C++], peek
- std::basic_istream [C++], putback
- std::basic_istream [C++], read
- std::basic_istream [C++], readsome
- std::basic_istream [C++], seekg
- std::basic_istream [C++], sentry
- std::basic_istream [C++], swap
- std::basic_istream [C++], sync
- std::basic_istream [C++], tellg
- std::basic_istream [C++], unget
ms.assetid: c7c27111-de6d-42b4-95a3-a7e65259bf17
ms.openlocfilehash: 03a6e3a65d6dc8c2fa896949855bd23a01578e5a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376826"
---
# <a name="basic_istream-class"></a>basic_istream — Klasa

Opisuje `Char_T`obiekt, który steruje wyodrębnianiem elementów i zakodowanych obiektów z buforu strumienia z elementami typu , znanymi również jako [char_type](../standard-library/basic-ios-class.md#char_type), których cechy charakteru są określane przez klasę *Tr*, zwymowaną również jako [traits_type](../standard-library/basic-ios-class.md#traits_type).

## <a name="syntax"></a>Składnia

```cpp
template <class Char_T, class Tr = char_traits<Char_T>>
class basic_istream : virtual public basic_ios<Char_T, Tr>
```

## <a name="remarks"></a>Uwagi

Większość funkcji elementów członkowskich, które [>>operatora](#op_gt_gt) przeciążenia są sformatowane funkcje wejściowe. Podążają za wzorem:

```cpp
iostate state = goodbit;
const sentry ok(*this);

if (ok)
{
    try
    {
        /*extract elements and convert
            accumulate flags in state.
            store a successful conversion*/
    }
    catch (...)
    {
        try
        {
            setstate(badbit);

        }
        catch (...)
        {
        }
        if ((exceptions()& badbit) != 0)
            throw;
    }
}
setstate(state);

return (*this);
```

Wiele innych funkcji członkowskich są niesformatowane funkcje wejściowe. Podążają za wzorem:

```cpp
iostate state = goodbit;
count = 0;    // the value returned by gcount
const sentry ok(*this, true);

if (ok)
{
    try
    {
        /* extract elements and deliver
            count extracted elements in count
            accumulate flags in state */
    }
    catch (...)
    {
        try
        {
            setstate(badbit);

        }
        catch (...)
        {
        }
        if ((exceptions()& badbit) != 0)
            throw;
    }
}
setstate(state);
```

Obie grupy funkcji [`setstate`](../standard-library/basic-ios-class.md#setstate) `(eofbit)` wywołać, jeśli napotkają koniec pliku podczas wyodrębniania elementów.

Obiekt `basic_istream<Char_T, Tr>` klasy przechowuje:

- Wirtualny publiczny obiekt [`basic_ios`](../standard-library/basic-ios-class.md) `<Char_T, Tr>`podstawowy klasy .

- Liczba ekstrakcji dla ostatniej operacji niesformatowanych danych wejściowych (wywoływanej `count` w poprzednim kodzie).

## <a name="example"></a>Przykład

Zobacz przykład [basic_ifstream Class,](../standard-library/basic-ifstream-class.md) aby dowiedzieć się więcej o strumieniach wejściowych.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_istream](#basic_istream)|Konstruuje obiekt `basic_istream`typu .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[gcount (liczba gcount)](#gcount)|Zwraca liczbę znaków odczytanych podczas ostatniego niesformatowanego wejścia.|
|[get](#get)|Odczytuje jeden lub więcej znaków ze strumienia wejściowego.|
|[Getline](#getline)|Odczytuje wiersz ze strumienia wejściowego.|
|[Ignoruj](#ignore)|Powoduje, że wiele elementów, które mają być pominięte z bieżącej pozycji odczytu.|
|[Peek](#peek)|Zwraca następny znak do odczytania.|
|[putback](#putback)|Umieszcza określony znak w strumieniu.|
|[Odczytu](#read)|Odczytuje określoną liczbę znaków ze strumienia i przechowuje je w tablicy.|
|[readsome](#readsome)|Odczyt tylko z bufora.|
|[seekg (poszukiwani)](#seekg)|Przesuwa pozycję odczytu w strumieniu.|
|[Sentry](#sentry)|Klasa zagnieżdżona opisuje obiekt, którego deklaracja struktury sformatowanych funkcji wejściowych i niesformatowanych funkcji wejściowych.|
|[Wymiany](#swap)|Wymienia `basic_istream` ten obiekt `basic_istream` dla podanego parametru obiektu.|
|[synchronizacja](#sync)|Synchronizuje skojarzone urządzenie wejściowe strumienia z buforem strumienia.|
|[tellg ( tellg )](#tellg)|Raportuje bieżącą pozycję odczytu w strumieniu.|
|[unget](#unget)|Umieszcza ostatnio przeczytany znak z powrotem do strumienia.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[>>operatora](#op_gt_gt)|Wywołuje funkcję w strumieniu wejściowym lub odczytuje sformatowane dane ze strumienia wejściowego.|
|[operator=](#op_eq)|Przypisuje po `basic_istream` prawej stronie operatora do tego obiektu. Jest to przypisanie przenoszenia `rvalue` obejmujące odwołanie, które nie pozostawia kopii za sobą.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<istream>

**Przestrzeń nazw:** std

## <a name="basic_istreambasic_istream"></a><a name="basic_istream"></a>basic_istream::basic_istream

Konstruuje obiekt `basic_istream`typu .

```cpp
explicit basic_istream(
    basic_streambuf<Char_T, Tr>* strbuf,
    bool _Isstd = false);

basic_istream(basic_istream&& right);
```

### <a name="parameters"></a>Parametry

*strbuf*\
Obiekt typu [basic_streambuf](../standard-library/basic-streambuf-class.md).

*_Isstd*\
**prawda,** jeśli jest to standardowy strumień; w przeciwnym razie **false**.

*Prawo*\
Obiekt `basic_istream` do skopiowania.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor inicjuje klasę [`init`](../standard-library/basic-ios-class.md#init) `(strbuf)`podstawową, wywołując . Przechowuje również zero w liczniku ekstrakcji. Aby uzyskać więcej informacji na temat tej liczby ekstrakcji, zobacz uwagi sekcji [basic_istream Class](../standard-library/basic-istream-class.md) omówienia.

Drugi konstruktor inicjuje klasę `move(right)`podstawową, wywołując . Przechowuje `right.gcount()` również w liczniku ekstrakcji i przechowuje zero w liczniku ekstrakcji dla *right**.

### <a name="example"></a>Przykład

Zobacz przykład [basic_ifstream::basic_ifstream,](../standard-library/basic-ifstream-class.md#basic_ifstream) aby dowiedzieć się więcej o strumieniach wejściowych.

## <a name="basic_istreamgcount"></a><a name="gcount"></a>basic_istream::gcount

Zwraca liczbę znaków odczytanych podczas ostatniego niesformatowanego wejścia.

```cpp
streamsize gcount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba ekstrakcji.

### <a name="remarks"></a>Uwagi

Użyj [basic_istream::get,](#get) aby odczytać znaki niesformatowane.

### <a name="example"></a>Przykład

```cpp
// basic_istream_gcount.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   cout << "Type the letter 'a': ";

   ws( cin );
   char c[10];

   cin.get( &c[0],9 );
   cout << c << endl;

   cout << cin.gcount( ) << endl;
}
```

```Input
a
```

```Output
Type the letter 'a': a
1
```

## <a name="basic_istreamget"></a><a name="get"></a>basic_istream::get

Odczytuje jeden lub więcej znaków ze strumienia wejściowego.

```cpp
int_type get();

basic_istream<Char_T, Tr>& get(Char_T& Ch);
basic_istream<Char_T, Tr>& get(Char_T* str, streamsize count);
basic_istream<Char_T, Tr>& get(Char_T* str, streamsize count, Char_T delimiter);

basic_istream<Char_T, Tr>& get(basic_streambuf<Char_T, Tr>& strbuf);
basic_istream<Char_T, Tr>& get(basic_streambuf<Char_T, Tr>& strbuf, Char_T delimiter);
```

### <a name="parameters"></a>Parametry

*Liczba*\
Liczba znaków do odczytania z *strbuf*.

*Ogranicznik*\
Znak, który powinien zakończyć odczyt, jeśli napotka przed *zliczanie*.

*Str*\
Ciąg, w którym można pisać.

*Ch*\
Postać do zdobycia.

*strbuf*\
Bufor, w którym można pisać.

### <a name="return-value"></a>Wartość zwracana

Bezwametryczne formy get zwraca element odczytany jako liczba całkowita lub koniec pliku. Pozostałe formularze zwracają strumień `this`(* ).

### <a name="remarks"></a>Uwagi

Pierwsza niesformatowana funkcja wejściowa wyodrębnia element, jeśli `rdbuf->sbumpc`to możliwe, tak jakby zwracał . W przeciwnym `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof)razie zwraca . Jeśli funkcja nie wyodrębnia żadnego elementu, wywołuje [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`.

Druga funkcja wyodrębnia [element](../standard-library/basic-ios-class.md#int_type) `meta` int_type w ten sam sposób. Jeśli `meta` porównuje się `traits_type::eof`równe , `setstate(failbit)`funkcja wywołuje . W przeciwnym `traits_type::` [`to_char_type`](../standard-library/char-traits-struct.md#to_char_type) `(meta)` razie, to sklepy w *Ch*. Funkcja zwraca __*this__.

Trzecia funkcja `get(str, count, widen('\n'))`zwraca .

Czwarta funkcja wyodrębnia `count - 1` się do elementów i przechowuje je w tablicy począwszy od *ul.* Zawsze przechowuje `char_type` po wszelkich wyodrębnionych elementów, które przechowuje. W kolejności badania, ekstrakcja zatrzymuje:

- Na końcu pliku.

- Po funkcji wyodrębnia element, który porównuje równe *ogranicznika*. W takim przypadku element jest odłożony z powrotem do kontrolowanej sekwencji.

- Po funkcja wyodrębnia `count - 1` elementy.

Jeśli funkcja nie wyodrębni żadnych `setstate(failbit)`elementów, wywołuje . W każdym przypadku zwraca __*this__.

Zwraca się `get(strbuf, widen('\n'))`piątą funkcję .

Szósta funkcja wyodrębnia elementy i wstawia je w *strbuf*. Wyodrębnianie zatrzymuje się na końcu pliku lub na elemencie, który porównuje się z *ogranicznikiem*, który nie jest wyodrębniany. Zatrzymuje się również, bez wyodrębniania danego elementu, jeśli wstawienie nie powiedzie się lub zgłasza wyjątek (który jest przechwytywany, ale nie rethrown). Jeśli funkcja nie wyodrębni żadnych `setstate(failbit)`elementów, wywołuje . W każdym przypadku funkcja zwraca __*this__.

### <a name="example"></a>Przykład

```cpp
// basic_istream_get.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10];

   c[0] = cin.get( );
   cin.get( c[1] );
   cin.get( &c[2],3 );
   cin.get( &c[4], 4, '7' );

   cout << c << endl;
}
```

```Output
1111
```

## <a name="basic_istreamgetline"></a><a name="getline"></a>basic_istream::getline

Pobiera wiersz ze strumienia wejściowego.

```cpp
basic_istream<Char_T, Tr>& getline(
    char_type* str,
    streamsize count);

basic_istream<Char_T, Tr>& getline(
    char_type* str,
    streamsize count,
    char_type delimiter);
```

### <a name="parameters"></a>Parametry

*Liczba*\
Liczba znaków do odczytania z *strbuf*.

*Ogranicznik*\
Znak, który powinien zakończyć odczyt, jeśli napotka przed *zliczanie*.

*Str*\
Ciąg, w którym można pisać.

### <a name="return-value"></a>Wartość zwracana

Strumień (__*this__).

### <a name="remarks"></a>Uwagi

Zwraca pierwszą z tych niesformatowanych funkcji wejściowych `getline(str, count, widen('\n'))`.

Druga funkcja wyodrębnia `count - 1` się do elementów i przechowuje je w tablicy począwszy od *ul.* Zawsze przechowuje znak zakończenia ciągu po wyodrębnionych elementów, które przechowuje. W kolejności badania, ekstrakcja zatrzymuje:

- Na końcu pliku.

- Po funkcji wyodrębnia element, który porównuje równe *ogranicznika*. W takim przypadku element nie jest odłożony z powrotem i nie jest dołączany do kontrolowanej sekwencji.

- Po funkcja wyodrębnia `count - 1` elementy.

Jeśli funkcja wyodrębnia żadnych `count - 1` elementów [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`lub elementów, wywołuje . W każdym przypadku zwraca __*this__.

### <a name="example"></a>Przykład

```cpp
// basic_istream_getline.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10];

   cin.getline( &c[0], 5, '2' );
   cout << c << endl;
}
```

```Output
121
```

## <a name="basic_istreamignore"></a><a name="ignore"></a>basic_istream::ignoruj

Powoduje, że wiele elementów, które mają być pominięte z bieżącej pozycji odczytu.

```cpp
basic_istream<Char_T, Tr>& ignore(
    streamsize count = 1,
    int_type delimiter = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*Liczba*\
Liczba elementów do pominięcia z bieżącej pozycji odczytu.

*Ogranicznik*\
Element, który, jeśli napotkane przed count, powoduje, `ignore` aby powrócić i zezwalając na wszystkie elementy po *ogranicznik* do odczytania.

### <a name="return-value"></a>Wartość zwracana

Strumień (__*this__).

### <a name="remarks"></a>Uwagi

Niesformatowana funkcja wprowadzania wyodrębnia się do *zliczania* elementów i odrzuca je. Jeśli *liczyć* `numeric_limits<int>::max`równa się , jednak jest traktowana jako arbitralnie duże. Wyodrębnianie zatrzymuje się na początku `Ch` na `traits_type::` [`to_int_type`](../standard-library/char-traits-struct.md#to_int_type) `(Ch)` końcu pliku lub na elemencie, który porównuje się z *ogranicznikiem* (który jest również wyodrębniany). Funkcja zwraca __*this__.

### <a name="example"></a>Przykład

```cpp
// basic_istream_ignore.cpp
// compile with: /EHsc
#include <iostream>
int main( )
{
   using namespace std;
   char chararray[10];
   cout << "Type 'abcdef': ";
   cin.ignore( 5, 'c' );
   cin >> chararray;
   cout << chararray;
}
```

```Output
Type 'abcdef': abcdef
def
```

## <a name="basic_istreamoperator"></a><a name="op_gt_gt"></a>podstawowy\_istream::operator>>

Wywołuje funkcję w strumieniu wejściowym lub odczytuje sformatowane dane ze strumienia wejściowego.

```cpp
basic_istream& operator>>(basic_istream& (* Pfn)(basic_istream&));
basic_istream& operator>>(ios_base& (* Pfn)(ios_base&));
basic_istream& operator>>(basic_ios<Char_T, Tr>& (* Pfn)(basic_ios<Char_T, Tr>&));
basic_istream& operator>>(basic_streambuf<Char_T, Tr>* strbuf);
basic_istream& operator>>(bool& val);
basic_istream& operator>>(short& val);
basic_istream& operator>>(unsigned short& val);
basic_istream& operator>>(int& val);
basic_istream& operator>>(unsigned int& val);
basic_istream& operator>>(long& val);
basic_istream& operator>>(unsigned long& val);
basic_istream& operator>>(long long& val);
basic_istream& operator>>(unsigned long long& val);
basic_istream& operator>>(void *& val);
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

### <a name="parameters"></a>Parametry

*Pfn*\
Wskaźnik funkcji.

*strbuf*\
Obiekt typu `stream_buf`.

*Val*\
Wartość do odczytu ze strumienia.

### <a name="return-value"></a>Wartość zwracana

Strumień (__*this__).

### <a name="remarks"></a>Uwagi

Nagłówek \<> istream definiuje również kilka globalnych operatorów ekstrakcji. Aby uzyskać więcej informacji, zobacz [>>  operatora(\<istream>).](../standard-library/istream-operators.md#op_gt_gt)

Pierwsza funkcja elementu członkowskiego zapewnia, że `istr >> ws` [`ws`](../standard-library/istream-functions.md#ws) `(istr)`wyrażenie formularza wywołuje , a następnie zwraca __*this__. Druga i trzecia funkcja zapewniają, że [`hex`](../standard-library/ios-functions.md#hex)inne manipulatory, takie jak , zachowują się podobnie. Pozostałe funkcje to sformatowane funkcje wejściowe.

Funkcja:

```cpp
basic_istream& operator>>(
    basic_streambuf<Char_T, Tr>* strbuf);
```

wyodrębnia elementy, jeśli *strbuf* nie jest wskaźnikiem null i wstawia je w *strbuf*. Wyodrębnianie zatrzymuje się na końcu pliku. Zatrzymuje się również bez wyodrębniania danego elementu, jeśli wstawienie nie powiedzie się lub zgłasza wyjątek (który jest przechwytywany, ale nie rethrown). Jeśli funkcja nie wyodrębni żadnych [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`elementów, wywołuje . W każdym przypadku funkcja zwraca __*this__.

Funkcja:

```cpp
basic_istream& operator>>(bool& val);
```

wyodrębnia pole i konwertuje je na [`use_facet`](../standard-library/basic-filebuf-class.md#open) `< num_get<Char_T, InIt>(` [`getloc`](../standard-library/ios-base-class.md#getloc) `).` [`get`](../standard-library/ios-base-class.md#getloc) `( InIt(` [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf)wartość logiczną, wywołując . `), Init(0), *this, getloc, val)` W `InIt` tym miejscu [`istreambuf_iterator`](../standard-library/istreambuf-iterator-class.md) `<Char_T, Tr>`jest zdefiniowany jako . Funkcja zwraca __*this__.

Każda z funkcji:

```cpp
basic_istream& operator>>(short& val);
basic_istream& operator>>(unsigned short& val);
basic_istream& operator>>(int& val);
basic_istream& operator>>(unsigned int& val);
basic_istream& operator>>(long& val);
basic_istream& operator>>(unsigned long& val);
basic_istream& operator>>(long long& val);
basic_istream& operator>>(unsigned long long& val);
basic_istream& operator>>(void *& val);
```

wyodrębnić pole i przekonwertować je `use_facet<num_get<Char_T, InIt>(getloc).` [`get`](#get) `(InIt(rdbuf), Init(0), *this, getloc, val)`na wartość liczbową, wywołując . W `InIt` tym miejscu `istreambuf_iterator<Char_T, Tr>`jest zdefiniowany jako , i *val* ma typu **długi,** **niepodpisany długi**lub **void** <strong>\*</strong> w razie potrzeby.

Jeśli przekonwertowana wartość nie może być reprezentowana jako [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`typ *val,* funkcja wywołuje . W każdym przypadku funkcja zwraca __*this__.

Każda z funkcji:

```cpp
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

wyodrębnić pole i przekonwertować je `use_facet<num_get<Char_T, InIt>(getloc).get(InIt(rdbuf), Init(0), *this, getloc, val)`na wartość liczbową, wywołując . Tutaj, `InIt` jest `istreambuf_iterator<Char_T, Tr>`zdefiniowany jako , i *val* ma typ **double** lub **long double w** razie potrzeby.

Jeśli przekonwertowana wartość nie może być reprezentowana jako `setstate(failbit)`typ *val,* funkcja wywołuje . W każdym przypadku zwraca __*this__.

### <a name="example"></a>Przykład

```cpp
// istream_basic_istream_op_is.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

ios_base& hex2( ios_base& ib )
{
   ib.unsetf( ios_base::dec );
   ib.setf( ios_base::hex );
   return ib;
}

basic_istream<char, char_traits<char> >& somefunc(basic_istream<char, char_traits<char> > &i)
{
   if ( i == cin )
   {
      cerr << "i is cin" << endl;
   }
   return i;
}

int main( )
{
   int i = 0;
   cin >> somefunc;
   cin >> i;
   cout << i << endl;
   cin >> hex2;
   cin >> i;
   cout << i << endl;
}
```

## <a name="basic_istreamoperator"></a><a name="op_eq"></a>basic_istream::operator=

Przypisuje po `basic_istream` prawej stronie operatora do tego obiektu. Jest to przypisanie przenoszenia `rvalue` obejmujące odwołanie, które nie pozostawia kopii za sobą.

```cpp
basic_istream& operator=(basic_istream&& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Odwołanie `rvalue` do `basic_ifstream` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca __*this__.

### <a name="remarks"></a>Uwagi

Operator elementu `swap(right)`członkowskiego wywołuje .

## <a name="basic_istreampeek"></a><a name="peek"></a>basic_istream::peek

Zwraca następny znak do odczytania.

```cpp
int_type peek();
```

### <a name="return-value"></a>Wartość zwracana

Następna postać, która zostanie przeczytana.

### <a name="remarks"></a>Uwagi

Niesformatowana funkcja wprowadzania wyodrębnia element, jeśli to `rdbuf->` [`sgetc`](../standard-library/basic-streambuf-class.md#sgetc)możliwe, tak jakby zwracał . W przeciwnym `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof)razie zwraca .

### <a name="example"></a>Przykład

```cpp
// basic_istream_peek.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2;
   cout << "Type 'abcde': ";

   c2 = cin.peek( );
   cin.getline( &c[0], 9 );

   cout << c2 << " " << c << endl;
}
```

```Input
abcde
```

```Output
Type 'abcde': abcde
a abcde
```

## <a name="basic_istreamputback"></a><a name="putback"></a>basic_istream::putback

Umieszcza określony znak w strumieniu.

```cpp
basic_istream<Char_T, Tr>& putback(
    char_type Ch);
```

### <a name="parameters"></a>Parametry

*Ch*\
Znak, który można umieścić z powrotem w strumieniu.

### <a name="return-value"></a>Wartość zwracana

Strumień (__*this__).

### <a name="remarks"></a>Uwagi

[Funkcja niesformatowanego wejścia](../standard-library/basic-istream-class.md) oddaje *Ch*, jeśli [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->` [`sputbackc`](../standard-library/basic-streambuf-class.md#sputbackc)to możliwe, tak jakby przez wywołanie . Jeśli `rdbuf` wskaźnik zerowy lub wywołanie `sputbackc` `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof)zwraca, funkcja [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)`wywołuje . W każdym przypadku zwraca __*this__.

### <a name="example"></a>Przykład

```cpp
// basic_istream_putback.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2, c3;

   c2 = cin.get( );
   c3 = cin.get( );
   cin.putback( c2 );
   cin.getline( &c[0], 9 );
   cout << c << endl;
}
```

```Output
qwq
```

## <a name="basic_istreamread"></a><a name="read"></a>basic_istream::czytaj

Odczytuje określoną liczbę znaków ze strumienia i przechowuje je w tablicy.

Ta metoda jest potencjalnie niebezpieczne, ponieważ opiera się na wywołującego, aby sprawdzić, czy przekazane wartości są poprawne.

```cpp
basic_istream<Char_T, Tr>& read(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*Str*\
Tablica, w której mają być odczytywane znaki.

*Liczba*\
Liczba znaków do odczytania.

### <a name="return-value"></a>Wartość zwracana

Strumień ( `*this`).

### <a name="remarks"></a>Uwagi

Niesformatowana funkcja wprowadzania wyodrębnia elementy do *zliczania* i przechowuje je w tablicy rozpoczynającej się od *ul.* Ekstrakcja zatrzymuje się na początku na [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`końcu pliku, w którym to przypadku funkcja wywołuje . W każdym przypadku zwraca __*this__.

### <a name="example"></a>Przykład

```cpp
// basic_istream_read.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main()
{
    char c[10];
    int count = 5;

    cout << "Type 'abcde': ";

    // Note: cin::read is potentially unsafe, consider
    // using cin::_Read_s instead.
    cin.read(&c[0], count);
    c[count] = 0;

    cout << c << endl;
}
```

```Input
abcde
```

```Output
Type 'abcde': abcde
abcde
```

## <a name="basic_istreamreadsome"></a><a name="readsome"></a>basic_istream::readsome

Odczytuje określoną liczbę wartości znaków.

Ta metoda jest potencjalnie niebezpieczne, ponieważ opiera się na wywołującego, aby sprawdzić, czy przekazane wartości są poprawne.

```cpp
streamsize readsome(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*Str*\
Tablica, `readsome` w której przechowuje znaki, które odczytuje.

*Liczba*\
Liczba znaków do odczytania.

### <a name="return-value"></a>Wartość zwracana

Liczba znaków faktycznie przeczytanych, [`gcount`](#gcount).

### <a name="remarks"></a>Uwagi

Ta niesformatowana funkcja wprowadzania wyodrębnia elementy z *danych* wejściowych i przechowuje je w tablicy *str*.

Ta funkcja nie czeka na dane wejściowe. Odczytuje wszelkie dostępne dane.

### <a name="example"></a>Przykład

```cpp
// basic_istream_readsome.cpp
// compile with: /EHsc /W3
#include <iostream>
using namespace std;

int main( )
{
   char c[10];
   int count = 5;

   cout << "Type 'abcdefgh': ";

   // cin.read blocks until user types input.
   // Note: cin::read is potentially unsafe, consider
   // using cin::_Read_s instead.
   cin.read(&c[0], 2);

   // Note: cin::readsome is potentially unsafe, consider
   // using cin::_Readsome_s instead.
   int n = cin.readsome(&c[0], count);  // C4996
   c[n] = 0;
   cout << n << " characters read" << endl;
   cout << c << endl;
}
```

## <a name="basic_istreamseekg"></a><a name="seekg"></a>basic_istream::seekg

Przesuwa pozycję odczytu w strumieniu.

```cpp
basic_istream<Char_T, Tr>& seekg(pos_type pos);

basic_istream<Char_T, Tr>& seekg(off_type off, ios_base::seekdir way);
```

### <a name="parameters"></a>Parametry

*Poz*\
Pozycja bezwzględna, w której ma być przesuń wskaźnik odczytu.

*wył.*\
Przesunięcie, aby przenieść odczyt wskaźnik względem *drogi*.

*Sposób*\
Jednym z [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) wyliczenia.

### <a name="return-value"></a>Wartość zwracana

Strumień (__*this__).

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego wykonuje bezwzględny seek, druga funkcja elementu członkowskiego wykonuje względny seek.

> [!NOTE]
> Nie należy używać funkcji drugiego elementu członkowskiego z plikami tekstowymi, ponieważ standard C++ nie obsługuje względnych żądań w plikach tekstowych.

Jeśli [`fail`](../standard-library/basic-ios-class.md#fail) jest false, pierwsza `newpos =` [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->` [`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos) `(pos)`funkcja elementu `pos_type` członkowskiego `newpos`wywołuje , dla niektórych obiektów tymczasowych . Jeśli `fail` jest false, druga `newpos = rdbuf->` [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) `( off, way)`funkcja wywołuje . W obu przypadkach, `(off_type)newpos == (off_type)(-1)` jeśli (operacja pozycjonowania nie powiedzie się), funkcja wywołuje `istr.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`. Obie funkcje zwracają __*this__.

Jeśli [`fail`](../standard-library/basic-ios-class.md#fail) jest true, funkcje członkowskie nic nie robią.

### <a name="example"></a>Przykład

```cpp
// basic_istream_seekg.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
   using namespace std;
   ifstream file;
   char c, c1;

   file.open( "basic_istream_seekg.txt" );
   file.seekg(2);   // seek to position 2
   file >> c;
   cout << c << endl;
}
```

## <a name="basic_istreamsentry"></a><a name="sentry"></a>basic_istream::działko

Klasa zagnieżdżona opisuje obiekt, którego deklaracja struktury sformatowanych i niesformatowanych funkcji wejściowych.

```cpp
class sentry {
   public:
   explicit sentry(
      basic_istream<Char_T, Tr>& _Istr,
      bool _Noskip = false);
   operator bool() const;
   };
```

### <a name="remarks"></a>Uwagi

Jeśli `_Istr.` [`good`](../standard-library/basic-ios-class.md#good) jest true, konstruktor:

- Wywołania, `_Istr.` [`tie`](../standard-library/basic-ios-class.md#tie) `->` [`flush`](../standard-library/basic-ostream-class.md#flush) jeśli `_Istr.tie` nie jest wskaźnik null.

- Skutecznie [`ws`](../standard-library/istream-functions.md#ws) `(_Istr)` wywołuje, `_Istr.` [`flags`](../standard-library/ios-base-class.md#flags) `&` [`skipws`](../standard-library/ios-functions.md#skipws) jeśli jest nonzero.

Jeśli po takim `_Istr.good` przygotowaniu jest fałszywy, `_Istr.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)`konstruktor wywołuje . W każdym przypadku konstruktor przechowuje `_Istr.good` `status`wartość zwróconą przez w . Późniejsze wywołanie, aby `operator bool` dostarczyć tę przechowywaną wartość.

## <a name="basic_istreamswap"></a><a name="swap"></a>basic_istream::swap

Wymienia zawartość dwóch `basic_istream` obiektów.

```cpp
void swap(basic_istream& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Odwołanie lvalue do `basic_istream` obiektu.

### <a name="remarks"></a>Uwagi

Funkcja elementu [`basic_ios::swap`](../standard-library/basic-ios-class.md#swap) `(right)`członkowskiego wywołuje . Wymienia również liczbę ekstrakcji z liczbą ekstrakcji dla *prawej*.

## <a name="basic_istreamsync"></a><a name="sync"></a>basic_istream::synchronizacja

Synchronizuje skojarzone urządzenie wejściowe strumienia z buforem strumienia.

```cpp
int sync();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) jest wskaźnikiem zerowym, funkcja zwraca wartość -1. W przeciwnym `rdbuf->` [`pubsync`](../standard-library/basic-streambuf-class.md#pubsync)razie wywołuje . Jeśli to wywołanie zwraca wartość [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)` -1, funkcja wywołuje i zwraca wartość -1. W przeciwnym razie funkcja zwraca zero.

## <a name="basic_istreamtellg"></a><a name="tellg"></a>basic_istream::tellg

Raportuje bieżącą pozycję odczytu w strumieniu.

```cpp
pos_type tellg();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca pozycja w strumieniu.

### <a name="remarks"></a>Uwagi

Jeśli [`fail`](../standard-library/basic-ios-class.md#fail) jest false, funkcja [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->` [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) `(0, cur, in)`elementu członkowskiego zwraca . W przeciwnym `pos_type(-1)`razie zwraca .

### <a name="example"></a>Przykład

```cpp
// basic_istream_tellg.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main()
{
    using namespace std;
    ifstream file;
    char c;
    streamoff i;

    file.open("basic_istream_tellg.txt");
    i = file.tellg();
    file >> c;
    cout << c << " " << i << endl;

    i = file.tellg();
    file >> c;
    cout << c << " " << i << endl;
}
```

## <a name="basic_istreamunget"></a><a name="unget"></a>basic_istream::unget

Umieszcza ostatnio przeczytany znak z powrotem do strumienia.

```cpp
basic_istream<Char_T, Tr>& unget();
```

### <a name="return-value"></a>Wartość zwracana

Strumień (__*this__).

### <a name="remarks"></a>Uwagi

[Funkcja niesformatowanego wejścia](../standard-library/basic-istream-class.md) oddaje poprzedni element w strumieniu, `rdbuf->` [`sungetc`](../standard-library/basic-streambuf-class.md#sungetc)jeśli to możliwe, tak jakby przez wywołanie . Jeśli [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) wskaźnik zerowy lub wywołanie `sungetc` `traits_type::` [`eof`](../standard-library/basic-ios-class.md#eof)zwraca, funkcja [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)`wywołuje . W każdym przypadku zwraca __*this__.

Aby uzyskać `unget` informacje o [`basic_streambuf::sungetc`](../standard-library/basic-streambuf-class.md#sungetc)tym, jak może się nie powieść, zobacz .

### <a name="example"></a>Przykład

```cpp
// basic_istream_unget.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2;

   cout << "Type 'abc': ";
   c2 = cin.get( );
   cin.unget( );
   cin.getline( &c[0], 9 );
   cout << c << endl;
}
```

```Input
abc
```

```Output
Type 'abc': abc
abc
```

## <a name="see-also"></a>Zobacz też

[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
