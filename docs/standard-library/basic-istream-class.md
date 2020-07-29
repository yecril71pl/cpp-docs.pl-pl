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
ms.openlocfilehash: da53db594e057449f2d227f57c902d26396000b7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219251"
---
# <a name="basic_istream-class"></a>basic_istream — Klasa

Opisuje obiekt, który kontroluje wyodrębnianie elementów i zakodowanych obiektów z bufora strumienia z elementami typu `Char_T` , znanym również jako [char_type](../standard-library/basic-ios-class.md#char_type), których cechy znaku są określane przez klasę *TR*, znaną również jako [traits_type](../standard-library/basic-ios-class.md#traits_type).

## <a name="syntax"></a>Składnia

```cpp
template <class Char_T, class Tr = char_traits<Char_T>>
class basic_istream : virtual public basic_ios<Char_T, Tr>
```

## <a name="remarks"></a>Uwagi

Większość funkcji Członkowskich, które [>>operatora](#op_gt_gt) przeciążenia są sformatowanymi funkcjami wejściowymi. Są one zgodne ze wzorcem:

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

Wiele innych funkcji Członkowskich są niesformatowanymi funkcjami wejściowymi. Są one zgodne ze wzorcem:

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

Obydwa grupy funkcji wywołuje, [`setstate`](../standard-library/basic-ios-class.md#setstate) `(eofbit)` Jeśli napotkają koniec pliku podczas wyodrębniania elementów.

Obiekt obiektów klasy `basic_istream<Char_T, Tr>` :

- Wirtualny, publiczny obiekt podstawowy klasy [`basic_ios`](../standard-library/basic-ios-class.md) `<Char_T, Tr>` .

- Liczba wyodrębniania dla ostatniej niesformatowanej operacji wejściowej (wywoływana `count` w poprzednim kodzie).

## <a name="example"></a>Przykład

Zapoznaj się z przykładem [klasy basic_ifstream](../standard-library/basic-ifstream-class.md) , aby dowiedzieć się więcej o strumieniach wejściowych.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[basic_istream](#basic_istream)|Konstruuje obiekt typu `basic_istream` .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[gcount](#gcount)|Zwraca liczbę znaków odczytywanych podczas ostatniego niesformatowanych danych wejściowych.|
|[Pobierz](#get)|Odczytuje jeden lub więcej znaków ze strumienia wejściowego.|
|[getline](#getline)|Odczytuje wiersz ze strumienia wejściowego.|
|[Ignoruj](#ignore)|Powoduje pominięcie wielu elementów z bieżącej pozycji odczytu.|
|[wybierania](#peek)|Zwraca następny znak, który ma zostać odczytany.|
|[putback](#putback)|Umieszcza określony znak w strumieniu.|
|[Przeczytaj](#read)|Odczytuje określoną liczbę znaków ze strumienia i zapisuje je w tablicy.|
|[readsome](#readsome)|Odczytaj tylko z bufora.|
|[seekg](#seekg)|Przenosi pozycję odczytu w strumieniu.|
|[WartownikDźwięków](#sentry)|Klasa zagnieżdżona opisuje obiekt, którego struktura deklaracji ma sformatowane funkcje wejściowe i niesformatowane funkcje wejściowe.|
|[wymiany](#swap)|Wymienia ten `basic_istream` obiekt dla podanego `basic_istream` parametru obiektu.|
|[synchronizacji](#sync)|Synchronizuje urządzenie wejściowe powiązane ze strumieniem z buforem strumienia.|
|[tellg](#tellg)|Raportuje bieżącą pozycję odczytu w strumieniu.|
|[unget](#unget)|Umieszcza ostatnio odczytywany znak z powrotem do strumienia.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[>>operatora](#op_gt_gt)|Wywołuje funkcję w strumieniu wejściowym lub odczytuje sformatowane dane ze strumienia wejściowego.|
|[operator =](#op_eq)|Przypisuje `basic_istream` po prawej stronie operatora do tego obiektu. Jest to przypisanie przenoszenia obejmujące `rvalue` odwołanie, które nie pozostawia kopii w tle.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<istream>

**Przestrzeń nazw:** std

## <a name="basic_istreambasic_istream"></a><a name="basic_istream"></a>basic_istream:: basic_istream

Konstruuje obiekt typu `basic_istream` .

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
**`true`** Jeśli jest to strumień standardowy; w przeciwnym razie **`false`** .

*Kliknij*\
`basic_istream`Obiekt do skopiowania.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje klasę bazową, wywołując metodę [`init`](../standard-library/basic-ios-class.md#init) `(strbuf)` . Przechowuje również zero w liczniku wyodrębniania. Aby uzyskać więcej informacji na temat tej liczby wyodrębniania, zobacz sekcję Uwagi w temacie Omówienie [klasy basic_istream](../standard-library/basic-istream-class.md) .

Drugi Konstruktor inicjuje klasę bazową, wywołując `move(right)` . Przechowuje także `right.gcount()` w liczniku wyodrębniania i przechowuje zero w liczniku ekstrakcji dla * Right * *.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [basic_ifstream:: basic_ifstream](../standard-library/basic-ifstream-class.md#basic_ifstream) , aby dowiedzieć się więcej o strumieniach wejściowych.

## <a name="basic_istreamgcount"></a><a name="gcount"></a>basic_istream:: gcount

Zwraca liczbę znaków odczytywanych podczas ostatniego niesformatowanych danych wejściowych.

```cpp
streamsize gcount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba wyodrębniania.

### <a name="remarks"></a>Uwagi

Użyj [basic_istream:: Get](#get) , aby odczytać niesformatowane znaki.

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

## <a name="basic_istreamget"></a><a name="get"></a>basic_istream:: Get

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

*liczbą*\
Liczba znaków do odczytania z *strbuf*.

*ogranicznik*\
Znak, który powinien przerwać odczyt, jeśli został napotkany przed *liczbą*.

*str*\
Ciąg, w którym ma zostać zapisany.

*Ch*\
Znak do pobrania.

*strbuf*\
Bufor, który ma zostać zapisany.

### <a name="return-value"></a>Wartość zwracana

Forma get bez parametrów zwraca element odczytaną jako liczbę całkowitą lub koniec pliku. Pozostałe formularze zwracają strumień (* **`this`** ).

### <a name="remarks"></a>Uwagi

Pierwsza niesformatowana funkcja wejściowa Wyodrębnia element, jeśli jest to możliwe, tak jak gdyby przez zwraca `rdbuf->sbumpc` . W przeciwnym razie zwraca `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof) . Jeśli funkcja nie wyodrębni elementu, wywołuje [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` .

Druga funkcja Wyodrębnia element [int_type](../standard-library/basic-ios-class.md#int_type) w ten `meta` sam sposób. Jeśli `meta` porównuje równe `traits_type::eof` , funkcja wywołuje `setstate(failbit)` . W przeciwnym razie przechowuje `traits_type::` [`to_char_type`](../standard-library/char-traits-struct.md#to_char_type) `(meta)` w *ch*. Funkcja zwraca __* this__.

Trzecia funkcja zwraca wartość `get(str, count, widen('\n'))` .

Czwarta funkcja wyodrębnia do `count - 1` elementów i zapisuje je w tablicy, zaczynając od *str*. Zawsze są przechowywane `char_type` po wyodrębnionych elementach, które przechowuje. W kolejności testowania Ekstrakcja zostaje zatrzymana:

- Na końcu pliku.

- Po wyodrębnieniu elementu, który porównuje równe *ogranicznika*. W tym przypadku element jest przywracany do kontrolowanej sekwencji.

- Po wyodrębnieniu elementów przez funkcję `count - 1` .

Jeśli funkcja nie wyodrębni żadnych elementów, wywołuje `setstate(failbit)` . W każdym przypadku zwraca wartość __* this__.

Piąta funkcja zwraca wartość `get(strbuf, widen('\n'))` .

Szósta funkcja wyodrębnia elementy i wstawia je w *strbuf*. Ekstrakcja kończy się na końcu pliku lub w elemencie, który porównuje równe *ogranicznik*, który nie został wyodrębniony. Zatrzymuje również, bez wyodrębniania elementu, w przypadku niepowodzenia wstawiania lub zgłasza wyjątek (który jest przechwytywany, ale nie jest ponownie zgłaszany). Jeśli funkcja nie wyodrębni żadnych elementów, wywołuje `setstate(failbit)` . W każdym przypadku funkcja zwraca __* this__.

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

## <a name="basic_istreamgetline"></a><a name="getline"></a>basic_istream:: getline

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

*liczbą*\
Liczba znaków do odczytania z *strbuf*.

*ogranicznik*\
Znak, który powinien przerwać odczyt, jeśli został napotkany przed *liczbą*.

*str*\
Ciąg, w którym ma zostać zapisany.

### <a name="return-value"></a>Wartość zwracana

Strumień (__* this__).

### <a name="remarks"></a>Uwagi

Pierwszy z tych niesformatowanych funkcji wejściowych zwraca wartość `getline(str, count, widen('\n'))` .

Druga funkcja wyodrębnia do `count - 1` elementów i zapisuje je w tablicy, zaczynając od *str*. Zawsze przechowuje znak zakończenia ciągu po wszystkich wyodrębnionych elementach, które przechowuje. W kolejności testowania Ekstrakcja zostaje zatrzymana:

- Na końcu pliku.

- Po wyodrębnieniu elementu, który porównuje równe *ogranicznika*. W tym przypadku element nie jest odłączony i nie jest dołączany do kontrolowanej sekwencji.

- Po wyodrębnieniu elementów przez funkcję `count - 1` .

Jeśli funkcja nie wyodrębni elementów lub `count - 1` elementów, wywołuje [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` . W każdym przypadku zwraca wartość __* this__.

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

## <a name="basic_istreamignore"></a><a name="ignore"></a>basic_istream:: ignore

Powoduje pominięcie wielu elementów z bieżącej pozycji odczytu.

```cpp
basic_istream<Char_T, Tr>& ignore(
    streamsize count = 1,
    int_type delimiter = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*liczbą*\
Liczba elementów do pominięcia z bieżącej pozycji odczytu.

*ogranicznik*\
Element, który, jeśli napotka przed Count, powoduje `ignore` zwrócenie i umożliwienie wszystkich elementów po odczytaniu przez *ogranicznik* .

### <a name="return-value"></a>Wartość zwracana

Strumień (__* this__).

### <a name="remarks"></a>Uwagi

Niesformatowana funkcja wejściowa wyodrębnia do *liczby* elementów i odrzuca je. Jeśli *Liczba* jest równa `numeric_limits<int>::max` , jednak jest ono pobierane jako arbitralnie duże. Ekstrakcja kończy się wczesne na końcu pliku lub na elemencie `Ch` , który `traits_type::` [`to_int_type`](../standard-library/char-traits-struct.md#to_int_type) `(Ch)` porównuje równe *ogranicznik* (który również jest wyodrębniany). Funkcja zwraca __* this__.

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

## <a name="basic_istreamoperator"></a><a name="op_gt_gt"></a>Basic \_ IStream:: operator>>

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

*PFN*\
Wskaźnik funkcji.

*strbuf*\
Obiekt typu `stream_buf`.

*użyte*\
Wartość, która ma zostać odczytana ze strumienia.

### <a name="return-value"></a>Wartość zwracana

Strumień (__* this__).

### <a name="remarks"></a>Uwagi

\<istream>Nagłówek definiuje również kilka globalnych operatorów wyodrębniania. Aby uzyskać więcej informacji, zobacz [operator>>  ( \<istream> )](../standard-library/istream-operators.md#op_gt_gt).

Pierwsza funkcja członkowska gwarantuje, że wyrażenie `istr >> ws` wywołuje formularz [`ws`](../standard-library/istream-functions.md#ws) `(istr)` , a następnie zwraca __* this__. Drugie i trzecie funkcje zapewniają, że inne manipulowania, takie jak [`hex`](../standard-library/ios-functions.md#hex) , zachowują się podobnie. Pozostałe funkcje są sformatowanymi funkcjami wejściowymi.

Funkcja:

```cpp
basic_istream& operator>>(
    basic_streambuf<Char_T, Tr>* strbuf);
```

wyodrębnia elementy, jeśli *strbuf* nie jest wskaźnikiem o wartości null i wstawia je w *strbuf*. Wyodrębnianie kończy się na końcu pliku. Jest ona także zatrzymywana bez wyodrębniania elementu, jeśli nie powiedzie się lub wygeneruje wyjątek (który jest przechwytywany, ale nie jest ponownie zgłaszany). Jeśli funkcja nie wyodrębni żadnych elementów, wywołuje [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` . W każdym przypadku funkcja zwraca __* this__.

Funkcja:

```cpp
basic_istream& operator>>(bool& val);
```

wyodrębnia pole i konwertuje je na wartość logiczną, wywołując metodę [`use_facet`](../standard-library/basic-filebuf-class.md#open) `< num_get<Char_T, InIt>(` [`getloc`](../standard-library/ios-base-class.md#getloc) `).` [`get`](../standard-library/ios-base-class.md#getloc) `( InIt(` [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `), Init(0), *this, getloc, val)` . Tutaj, `InIt` został zdefiniowany jako [`istreambuf_iterator`](../standard-library/istreambuf-iterator-class.md) `<Char_T, Tr>` . Funkcja zwraca __* this__.

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

Wyodrębnij pole i Przekonwertuj je na wartość liczbową, wywołując metodę `use_facet<num_get<Char_T, InIt>(getloc).` [`get`](#get) `(InIt(rdbuf), Init(0), *this, getloc, val)` . W tym miejscu `InIt` jest zdefiniowane jako `istreambuf_iterator<Char_T, Tr>` , a *Val* ma typ **`long`** , **`unsigned long`** lub **`void`** <strong>\*</strong> w razie konieczności.

Jeśli przekonwertowana wartość nie może być reprezentowana jako typ *Val*, wywołania funkcji [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` . W każdym przypadku funkcja zwraca __* this__.

Każda z funkcji:

```cpp
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

Wyodrębnij pole i Przekonwertuj je na wartość liczbową, wywołując metodę `use_facet<num_get<Char_T, InIt>(getloc).get(InIt(rdbuf), Init(0), *this, getloc, val)` . Tutaj, `InIt` jest zdefiniowane jako `istreambuf_iterator<Char_T, Tr>` , a *Val* ma typ **`double`** lub **`long double`** w razie konieczności.

Jeśli przekonwertowana wartość nie może być reprezentowana jako typ *Val*, wywołania funkcji `setstate(failbit)` . W każdym przypadku zwraca wartość __* this__.

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

## <a name="basic_istreamoperator"></a><a name="op_eq"></a>basic_istream:: operator =

Przypisuje `basic_istream` po prawej stronie operatora do tego obiektu. Jest to przypisanie przenoszenia obejmujące `rvalue` odwołanie, które nie pozostawia kopii w tle.

```cpp
basic_istream& operator=(basic_istream&& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
`rvalue`Odwołanie do `basic_ifstream` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca __* this__.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego wywołuje `swap(right)` .

## <a name="basic_istreampeek"></a><a name="peek"></a>basic_istream::p EEK

Zwraca następny znak, który ma zostać odczytany.

```cpp
int_type peek();
```

### <a name="return-value"></a>Wartość zwracana

Następny znak, który zostanie odczytany.

### <a name="remarks"></a>Uwagi

Niesformatowana funkcja wejściowa Wyodrębnia element, jeśli jest to możliwe, tak jak gdyby przez zwraca `rdbuf->` [`sgetc`](../standard-library/basic-streambuf-class.md#sgetc) . W przeciwnym razie zwraca `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof) .

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

## <a name="basic_istreamputback"></a><a name="putback"></a>basic_istream::p utback

Umieszcza określony znak w strumieniu.

```cpp
basic_istream<Char_T, Tr>& putback(
    char_type Ch);
```

### <a name="parameters"></a>Parametry

*Ch*\
Znak, który ma zostać przywrócony do strumienia.

### <a name="return-value"></a>Wartość zwracana

Strumień (__* this__).

### <a name="remarks"></a>Uwagi

[Niesformatowana funkcja wejściowa](../standard-library/basic-istream-class.md) przywróci wartość *ch*, jeśli to możliwe, tak jak w przypadku wywołania metody [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->` [`sputbackc`](../standard-library/basic-streambuf-class.md#sputbackc) . Jeśli `rdbuf` jest wskaźnikiem typu null lub jeśli wywołanie do `sputbackc` zwraca `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof) , wywołuje funkcję [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)` . W każdym przypadku zwraca wartość __* this__.

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

## <a name="basic_istreamread"></a><a name="read"></a>basic_istream:: Read

Odczytuje określoną liczbę znaków ze strumienia i zapisuje je w tablicy.

Ta metoda jest potencjalnie niebezpieczna, ponieważ polega na wywołującym, aby sprawdzić, czy przeszukane wartości są poprawne.

```cpp
basic_istream<Char_T, Tr>& read(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*str*\
Tablica, w której mają zostać odczytane znaki.

*liczbą*\
Liczba znaków do odczytania.

### <a name="return-value"></a>Wartość zwracana

Strumień ( **`*this`** ).

### <a name="remarks"></a>Uwagi

Niesformatowana funkcja wejściowa wyodrębnia do *liczby* elementów i zapisuje je w tablicy, zaczynając od *str*. Wyodrębnianie kończy się wczesne na końcu pliku, w tym przypadku funkcja wywołuje [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` . W każdym przypadku zwraca wartość __* this__.

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

## <a name="basic_istreamreadsome"></a><a name="readsome"></a>basic_istream:: readsome

Odczytuje określoną liczbę wartości znakowych.

Ta metoda jest potencjalnie niebezpieczna, ponieważ polega na wywołującym, aby sprawdzić, czy przeszukane wartości są poprawne.

```cpp
streamsize readsome(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*str*\
Tablica, w której `readsome` są przechowywane znaki odczytywane przez nią.

*liczbą*\
Liczba znaków do odczytania.

### <a name="return-value"></a>Wartość zwracana

Liczba znaków faktycznie odczytywanych, [`gcount`](#gcount) .

### <a name="remarks"></a>Uwagi

Ta niesformatowana funkcja wejściowa wyodrębnia do *liczby* elementów ze strumienia wejściowego i zapisuje je w tablicy *str*.

Ta funkcja nie czeka na dane wejściowe. Odczytuje dane, które są dostępne.

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

## <a name="basic_istreamseekg"></a><a name="seekg"></a>basic_istream:: seekg

Przenosi pozycję odczytu w strumieniu.

```cpp
basic_istream<Char_T, Tr>& seekg(pos_type pos);

basic_istream<Char_T, Tr>& seekg(off_type off, ios_base::seekdir way);
```

### <a name="parameters"></a>Parametry

*Terminal*\
Pozycja absolutna, w której ma zostać przeniesiony wskaźnik odczytu.

*Logowanie*\
Przesunięcie, aby przenieść wskaźnik odczytu względem *metody*.

*możliwości*\
Jeden z [ios_base:: seekdir](../standard-library/ios-base-class.md#seekdir) Enumerations.

### <a name="return-value"></a>Wartość zwracana

Strumień (__* this__).

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska wykonuje jednokrotne wyszukiwanie, druga funkcja członkowska wykonuje przeszukiwanie względne.

> [!NOTE]
> Nie należy używać drugiej funkcji składowej z plikami tekstowymi, ponieważ standard C++ nie obsługuje wyszukiwania relatywnego w plikach tekstowych.

Jeśli [`fail`](../standard-library/basic-ios-class.md#fail) ma wartość false, Pierwsza funkcja elementu członkowskiego wywołuje `newpos =` [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->` [`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos) `(pos)` dla pewnego `pos_type` obiektu tymczasowego `newpos` . Jeśli `fail` ma wartość false, druga funkcja wywołuje `newpos = rdbuf->` [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) `( off, way)` . W obu przypadkach, jeśli `(off_type)newpos == (off_type)(-1)` (operacja pozycjonowania zakończy się niepowodzeniem), funkcja wywołuje `istr.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` . Obie funkcje zwracają __* this__.

Jeśli [`fail`](../standard-library/basic-ios-class.md#fail) ma wartość true, funkcje składowe nic nie rób.

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

## <a name="basic_istreamsentry"></a><a name="sentry"></a>basic_istream:: Sentry

Klasa zagnieżdżona opisuje obiekt, którego struktura deklaracji ma sformatowane i niesformatowane funkcje wejściowe.

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

Jeśli `_Istr.` [`good`](../standard-library/basic-ios-class.md#good) ma wartość true, Konstruktor:

- Wywołuje `_Istr.` [`tie`](../standard-library/basic-ios-class.md#tie) `->` [`flush`](../standard-library/basic-ostream-class.md#flush) `_Istr.tie` , jeśli nie jest wskaźnikiem wartości null.

- Efektywne wywołania, [`ws`](../standard-library/istream-functions.md#ws) `(_Istr)` Jeśli `_Istr.` [`flags`](../standard-library/ios-base-class.md#flags) `&` [`skipws`](../standard-library/ios-functions.md#skipws) jest różna od zera.

Jeśli po dodaniu takiego przygotowania `_Istr.good` ma wartość FAŁSZ, Konstruktor wywołuje `_Istr.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` . W każdym przypadku Konstruktor przechowuje wartość zwracaną przez `_Istr.good` `status` . Późniejsze wywołanie w celu `operator bool` dostarczenia tej przechowywanej wartości.

## <a name="basic_istreamswap"></a><a name="swap"></a>basic_istream:: swap

Wymienia zawartość dwóch `basic_istream` obiektów.

```cpp
void swap(basic_istream& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Odwołanie lvalue do `basic_istream` obiektu.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego wywołuje [`basic_ios::swap`](../standard-library/basic-ios-class.md#swap) `(right)` . Wymienia również liczbę wyodrębniania z liczbą wyodrębniania dla *prawej*.

## <a name="basic_istreamsync"></a><a name="sync"></a>basic_istream:: Sync

Synchronizuje urządzenie wejściowe powiązane ze strumieniem z buforem strumienia.

```cpp
int sync();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) jest wskaźnikiem typu null, funkcja zwraca wartość-1. W przeciwnym razie wywołuje `rdbuf->` [`pubsync`](../standard-library/basic-streambuf-class.md#pubsync) . Jeśli to wywołanie zwróci wartość-1, funkcja wywołuje [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)` i zwraca wartość-1. W przeciwnym razie funkcja zwraca wartość zero.

## <a name="basic_istreamtellg"></a><a name="tellg"></a>basic_istream:: tellg

Raportuje bieżącą pozycję odczytu w strumieniu.

```cpp
pos_type tellg();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca pozycja w strumieniu.

### <a name="remarks"></a>Uwagi

Jeśli [`fail`](../standard-library/basic-ios-class.md#fail) ma wartość false, funkcja członkowska zwraca [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->` [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) `(0, cur, in)` . W przeciwnym razie zwraca `pos_type(-1)` .

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

## <a name="basic_istreamunget"></a><a name="unget"></a>basic_istream:: unget

Umieszcza ostatnio odczytywany znak z powrotem do strumienia.

```cpp
basic_istream<Char_T, Tr>& unget();
```

### <a name="return-value"></a>Wartość zwracana

Strumień (__* this__).

### <a name="remarks"></a>Uwagi

[Niesformatowana funkcja wejściowa](../standard-library/basic-istream-class.md) umieszcza poprzedni element w strumieniu, jeśli jest to możliwe, tak jak przez wywołanie `rdbuf->` [`sungetc`](../standard-library/basic-streambuf-class.md#sungetc) . Jeśli [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) jest wskaźnikiem typu null lub jeśli wywołanie do `sungetc` zwraca `traits_type::` [`eof`](../standard-library/basic-ios-class.md#eof) , wywołuje funkcję [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)` . W każdym przypadku zwraca wartość __* this__.

Aby uzyskać informacje o tym `unget` , jak może się nie powieść, zobacz [`basic_streambuf::sungetc`](../standard-library/basic-streambuf-class.md#sungetc) .

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

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostreams](../standard-library/iostreams-conventions.md)
