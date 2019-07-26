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
ms.openlocfilehash: d1a76e9c639ac56ca693527543ecff5c597456f0
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452554"
---
# <a name="basicistream-class"></a>basic_istream — Klasa

Opisuje obiekt, który kontroluje wyodrębnianie elementów i zakodowanych obiektów z bufora strumienia z elementami typu `Elem`, znanym również jako [char_type](../standard-library/basic-ios-class.md#char_type), których cechy znaku są określane przez klasę *TR*, znaną również jako [traits_ Typ](../standard-library/basic-ios-class.md#traits_type).

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_istream : virtual public basic_ios<Elem, Tr>
```

## <a name="remarks"></a>Uwagi

Większość funkcji Członkowskich, które [> operator](#op_gt_gt) przeciążania > są sformatowanymi funkcjami wejściowymi. Są one zgodne ze wzorcem:

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

Obie grupy funkcji wywołują [](../standard-library/basic-ios-class.md#setstate)metodę setstate`eofbit`(), Jeśli napotkają koniec pliku podczas wyodrębniania elementów.

`basic_istream`Obiekt klasy <  , magazyn TR >: `Elem`

- Wirtualny, publiczny obiekt podstawowy klasy [basic_ios](../standard-library/basic-ios-class.md)< `Elem`, *TR*> `.`

- Liczba wyodrębniania dla ostatniej niesformatowanej operacji wejściowej ( `count` wywoływana w poprzednim kodzie).

## <a name="example"></a>Przykład

Zobacz przykład dla [klasy basic_ifstream](../standard-library/basic-ifstream-class.md) , aby dowiedzieć się więcej o strumieniach wejściowych.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_istream](#basic_istream)|Konstruuje obiekt typu `basic_istream`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[gcount](#gcount)|Zwraca liczbę znaków odczytywanych podczas ostatniego niesformatowanych danych wejściowych.|
|[get](#get)|Odczytuje jeden lub więcej znaków ze strumienia wejściowego.|
|[getline](#getline)|Odczytuje wiersz ze strumienia wejściowego.|
|[Ignoruj](#ignore)|Powoduje pominięcie wielu elementów z bieżącej pozycji odczytu.|
|[wybierania](#peek)|Zwraca następny znak, który ma zostać odczytany.|
|[putback](#putback)|Umieszcza określony znak w strumieniu.|
|[read](#read)|Odczytuje określoną liczbę znaków ze strumienia i zapisuje je w tablicy.|
|[readsome](#readsome)|Odczytaj tylko z bufora.|
|[seekg](#seekg)|Przenosi pozycję odczytu w strumieniu.|
|[WartownikDźwięków](#sentry)|Klasa zagnieżdżona opisuje obiekt, którego struktura deklaracji ma sformatowane funkcje wejściowe i niesformatowane funkcje wejściowe.|
|[swap](#swap)|Wymienia ten `basic_istream` obiekt dla podanego `basic_istream` parametru obiektu.|
|[sync](#sync)|Synchronizuje urządzenie wejściowe skojarzone ze strumieniem z buforem strumienia.|
|[tellg](#tellg)|Raportuje bieżącą pozycję odczytu w strumieniu.|
|[unget](#unget)|Umieszcza ostatnio odczytywany znak z powrotem do strumienia.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator>>](#op_gt_gt)|Wywołuje funkcję w strumieniu wejściowym lub odczytuje sformatowane dane ze strumienia wejściowego.|
|[operator=](#op_eq)|Przypisuje `basic_istream` po prawej stronie operatora do tego obiektu. Jest to przypisanie przenoszenia obejmujące `rvalue` odwołanie, które nie pozostawia kopii w tle.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<IStream >

**Przestrzeń nazw:** std

## <a name="basic_istream"></a>basic_istream::basic_istream

Konstruuje obiekt typu `basic_istream`.

```cpp
explicit basic_istream(
    basic_streambuf<Elem, Tr>* strbuf,
    bool _Isstd = false);

basic_istream(basic_istream&& right);
```

### <a name="parameters"></a>Parametry

*strbuf*\
Obiekt typu [basic_streambuf](../standard-library/basic-streambuf-class.md).

*_Isstd*\
**prawda** , jeśli jest to strumień standardowy; w przeciwnym razie **false**.

*Kliknij*\
`basic_istream` Obiekt do skopiowania.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje klasę bazową, wywołując metodę [init](../standard-library/basic-ios-class.md#init)(_s `trbuf`). Przechowuje również zero w liczniku wyodrębniania. Aby uzyskać więcej informacji na temat tej liczby wyodrębniania, zobacz sekcję Uwagi w temacie [Basic_istream Class](../standard-library/basic-istream-class.md) Overview.

Drugi Konstruktor inicjuje klasę bazową, wywołując `move( right)`. Przechowuje również _r `ight.gcount()` w liczniku wyodrębniania i przechowuje zero w liczniku ekstrakcji dla `ight`_r.

### <a name="example"></a>Przykład

Zobacz przykład dla [basic_ifstream:: basic_ifstream](../standard-library/basic-ifstream-class.md#basic_ifstream) , aby dowiedzieć się więcej o strumieniach wejściowych.

## <a name="gcount"></a>basic_istream::gcount

Zwraca liczbę znaków odczytywanych podczas ostatniego niesformatowanych danych wejściowych.

```cpp
streamsize gcount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba wyodrębniania.

### <a name="remarks"></a>Uwagi

Użyj [basic_istream:: Get](#get) do odczytu niesformatowanych znaków.

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

## <a name="get"></a>basic_istream:: Get

Odczytuje jeden lub więcej znaków ze strumienia wejściowego.

```cpp
int_type get();

basic_istream<Elem, Tr>& get(Elem& Ch);
basic_istream<Elem, Tr>& get(Elem* str, streamsize count);
basic_istream<Elem, Tr>& get(Elem* str, streamsize count, Elem Delim);

basic_istream<Elem, Tr>& get(basic_streambuf<Elem, Tr>& strbuf);
basic_istream<Elem, Tr>& get(basic_streambuf<Elem, Tr>& strbuf, Elem Delim);
```

### <a name="parameters"></a>Parametry

*liczbą*\
Liczba znaków, z `strbuf`których ma zostać odczytana.

*Delim*\
Znak, który powinien przerwać odczyt, jeśli został napotkany przed *liczbą*.

*str*\
Ciąg, w którym ma zostać zapisany.

*Ch*\
Znak do pobrania.

*strbuf*\
Bufor, który ma zostać zapisany.

### <a name="return-value"></a>Wartość zwracana

Forma get bez parametrów zwraca element odczytaną jako liczbę całkowitą lub koniec pliku. Pozostałe formularze zwracają strumień (* `this`).

### <a name="remarks"></a>Uwagi

Pierwsze z tych niesformatowanych funkcji wejściowych Wyodrębnia element, jeśli jest to możliwe, tak jak gdyby `rdbuf`przez zwraca. ->  `sbumpc` W przeciwnym razie zwraca **traits_type::** [EOF](../standard-library/char-traits-struct.md#eof). Jeśli funkcja nie wyodrębni elementu, wywołuje metodę setstate ( [](../standard-library/basic-ios-class.md#setstate)`failbit`).

Druga funkcja Wyodrębnia element `meta` [int_type](../standard-library/basic-ios-class.md#int_type) w ten sam sposób. Jeśli `meta` porównuje wartość równą **traits_type:: EOF**, wywołania `setstate`funkcji ( **failbit**). W przeciwnym razie przechowuje **traits_type::** [to_char_type](../standard-library/char-traits-struct.md#to_char_type)( `meta`) w `Ch`. Funkcja zwraca  **\*ten**wynik.

Trzecia funkcja zwraca wartość **Get**(_ *str*, `count`, `widen`(' \ **n**')).

Czwarta funkcja wyodrębnia do *liczby* elementów-1 i zapisuje je w tablicy, zaczynając od _ *str*. Zawsze są przechowywane `char_type` po wyodrębnionych elementach, które przechowuje. W kolejności testowania Ekstrakcja zostaje zatrzymana:

- Na końcu pliku.

- Po wyodrębnieniu elementu, który porównuje wartość równą *delim*, w takim przypadku element jest przywracany do kontrolowanej sekwencji.

- Po wyodrębnieniu przez funkcję *liczby elementów liczba* -1.

Jeśli funkcja nie wyodrębni żadnych elementów, wywołuje `setstate`( **failbit**). W każdym przypadku zwraca  **\*to**.

Piąta funkcja zwraca wartość **Get**( **strbuf**, `widen`("\ **n**")).

Szósta funkcja wyodrębnia elementy i wstawia je w `strbuf`. Ekstrakcja jest zatrzymana na końcu pliku lub w elemencie, który porównuje równe _ *delim,* który nie jest wyodrębniony. Zatrzymuje również, bez wyodrębniania elementu, w przypadku niepowodzenia wstawiania lub zgłasza wyjątek (który jest przechwytywany, ale nie jest ponownie zgłaszany). Jeśli funkcja nie wyodrębni żadnych elementów, wywołuje `setstate`( **failbit**). W każdym przypadku funkcja zwraca  **\*ten**wynik.

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

## <a name="getline"></a>basic_istream:: getline

Pobiera wiersz ze strumienia wejściowego.

```cpp
basic_istream<Elem, Tr>& getline(
    char_type* str,
    streamsize count);

basic_istream<Elem, Tr>& getline(
    char_type* str,
    streamsize count,
    char_type Delim);
```

### <a name="parameters"></a>Parametry

*liczbą*\
Liczba znaków, z `strbuf`których ma zostać odczytana.

*Delim*\
Znak, który powinien przerwać odczyt, jeśli został napotkany przed *liczbą*.

*str*\
Ciąg, w którym ma zostać zapisany.

### <a name="return-value"></a>Wartość zwracana

Strumień (  **\*ten**).

### <a name="remarks"></a>Uwagi

Pierwsze z tych niesformatowanych funkcji wejściowych zwraca **getline**(_ *str*, `count`, `widen`(" `\` **n**")).

Druga funkcja wyodrębnia do *liczby* elementów-1 i zapisuje je w tablicy, zaczynając od _ *str*. Zawsze przechowuje znak zakończenia ciągu po wszystkich wyodrębnionych elementach, które przechowuje. W kolejności testowania Ekstrakcja zostaje zatrzymana:

- Na końcu pliku.

- Po wyodrębnieniu elementu, który porównuje wartość równą *delim*, w takim przypadku element nie jest umieszczany ani dołączany do kontrolowanej sekwencji.

- Po wyodrębnieniu przez funkcję *liczby elementów liczba* -1.

Jeśli funkcja nie wyodrębni elementów ani *liczby* elementów 1, wywołuje metodę setstate [](../standard-library/basic-ios-class.md#setstate)(`failbit`). W każdym przypadku zwraca  **\*to**.

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

## <a name="ignore"></a>basic_istream:: ignore

Powoduje pominięcie wielu elementów z bieżącej pozycji odczytu.

```cpp
basic_istream<Elem, Tr>& ignore(
    streamsize count = 1,
    int_type Delim = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*liczbą*\
Liczba elementów do pominięcia z bieżącej pozycji odczytu.

*Delim*\
Element, który, jeśli napotka przed Count, powoduje `ignore` zwrócenie i umożliwienie wszystkich elementów po *delim* .

### <a name="return-value"></a>Wartość zwracana

Strumień (  **\*ten**).

### <a name="remarks"></a>Uwagi

Niesformatowana funkcja wejściowa wyodrębnia do *liczby* elementów i odrzuca je. Jeśli *Liczba* jest równa **numeric_limits\<int >:: Max**, jednak jest traktowany jako arbitralnie duży. Ekstrakcja kończy się wczesne na końcu pliku lub na `Ch` elemencie, takim jak **traits_type::** [to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `Ch`) porównuje się z *delim* (który jest również wyodrębniany). Funkcja zwraca  **\*ten**wynik.

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

## <a name="op_gt_gt"></a>Basic\_IStream:: operator > >

Wywołuje funkcję w strumieniu wejściowym lub odczytuje sformatowane dane ze strumienia wejściowego.

```cpp
basic_istream& operator>>(basic_istream& (* Pfn)(basic_istream&));
basic_istream& operator>>(ios_base& (* Pfn)(ios_base&));
basic_istream& operator>>(basic_ios<Elem, Tr>& (* Pfn)(basic_ios<Elem, Tr>&));
basic_istream& operator>>(basic_streambuf<Elem, Tr>* strbuf);
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

Strumień (  **\*ten**).

### <a name="remarks"></a>Uwagi

Nagłówek \<> IStream definiuje także kilka globalnych operatorów wyodrębniania. Aby uzyskać więcej informacji, zobacz [> operatora >\<(IStream >)](../standard-library/istream-operators.md#op_gt_gt).

Pierwsza funkcja członkowska gwarantuje, że wyrażenie formularza **ISTR**  >>  `ws` wywołuje metodę [WS](../standard-library/istream-functions.md#ws)( **ISTR**), a następnie zwraca  **\*to**. Drugie i trzecie funkcje zapewniają, że inne manipulowania, takie jak [szesnastkowo](../standard-library/ios-functions.md#hex), zachowują się podobnie. Pozostałe funkcje stanowią sformatowaną funkcję wejściową.

Funkcja:

```cpp
basic_istream& operator>>(
    basic_streambuf<Elem, Tr>* strbuf);
```

wyodrębnia elementy, jeśli _ *strbuf* nie jest wskaźnikiem null i wstawia je w *strbuf*. Wyodrębnianie kończy się na końcu pliku. Jest ona także zatrzymywana bez wyodrębniania elementu, jeśli nie powiedzie się lub wygeneruje wyjątek (który jest przechwytywany, ale nie jest ponownie zgłaszany). Jeśli funkcja nie wyodrębni żadnych elementów, wywołuje metodę [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`). W każdym przypadku funkcja zwraca  **\*ten**wynik.

Funkcja:

```cpp
basic_istream& operator>>(bool& val);
```

wyodrębnia pole i konwertuje je na wartość logiczną, wywołując`num_get` [use_facet](../standard-library/basic-filebuf-class.md#open)  <  \< **elem**, **init**> ( [getloc](../standard-library/ios-base-class.md#getloc)). [Pobierz](../standard-library/ios-base-class.md#getloc) ( **Init**( [rdbuf](../standard-library/basic-ios-class.md#rdbuf)), `Init`  **\*(0**), this `val`, ,).`getloc` W tym **miejscu init** definiuje się [jako istreambuf_iterator](../standard-library/istreambuf-iterator-class.md) \< **elem**, **TR**>. Funkcja zwraca  **\*ten**wynik.

Funkcje:

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

Każde wyodrębnienie pola i przekonwertowanie go na wartość liczbową przez `use_facet` wywołanie `num_get` \< <  **elem**, **init**> `getloc`(). [Pobierz](#get) ( **Init**( `rdbuf`), `Init`(0),  **\*this** `getloc`,, `val`). W tym  miejscu Inicjalizacja jest `istreambuf_iterator` definiowana jako \< **elem**, **TR**> `val` i ma typ **Long**, unsigned **Long**lub **void** <strong>\*</strong> w razie konieczności.

Jeśli przekonwertowana wartość nie może być reprezentowana jako typ `val`, funkcja wywołuje metodę setstate ( [](../standard-library/basic-ios-class.md#setstate)`failbit`). W każdym przypadku funkcja zwraca  **\*ten**wynik.

Funkcje:

```cpp
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

Każde wyodrębnienie pola i przekonwertowanie go na wartość liczbową przez `use_facet` wywołanie `num_get` \< <  **elem**, **init**> `getloc`(). **Pobierz** ( **Init**( `rdbuf`), `Init`(0),  **\*this** `getloc`,, `val`). \< `istreambuf_iterator` `val`     W tym miejscu jestdefiniowanajakoelem,TR>imatypdoublelublongdouble,zgodniezwymaganiami.`InIt`

Jeśli przekonwertowana wartość nie może być reprezentowana jako typ `val`, wywołania `setstate`funkcji ( **failbit**). W każdym przypadku zwraca  **\*to**.

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

## <a name="op_eq"></a>basic_istream:: operator =

Przypisuje `basic_istream` po prawej stronie operatora do tego obiektu. Jest to przypisanie przenoszenia obejmujące `rvalue` odwołanie, które nie pozostawia kopii w tle.

```cpp
basic_istream& operator=(basic_istream&& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
`rvalue` Odwołanie`basic_ifstream` do obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca * this.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego wywołuje `( right)`zamianę.

## <a name="peek"></a>basic_istream::p EEK

Zwraca następny znak, który ma zostać odczytany.

```cpp
int_type peek();
```

### <a name="return-value"></a>Wartość zwracana

Następny znak, który zostanie odczytany.

### <a name="remarks"></a>Uwagi

Niesformatowana funkcja wejściowa Wyodrębnia element, jeśli jest to możliwe, tak jak `rdbuf`w przypadku, zwracając  ->  [sgetc —](../standard-library/basic-streambuf-class.md#sgetc). W przeciwnym razie zwraca **traits_type::** [EOF](../standard-library/char-traits-struct.md#eof).

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

## <a name="putback"></a>basic_istream::p utback

Umieszcza określony znak w strumieniu.

```cpp
basic_istream<Elem, Tr>& putback(
    char_type Ch);
```

### <a name="parameters"></a>Parametry

*Ch*\
Znak, który ma zostać przywrócony do strumienia.

### <a name="return-value"></a>Wartość zwracana

Strumień (  **\*ten**).

### <a name="remarks"></a>Uwagi

Niesformatowana [Funkcja wejściowa](../standard-library/basic-istream-class.md) przywraca wartość *ch*, jeśli to możliwe, tak jakby przez wywołanie [rdbuf](../standard-library/basic-ios-class.md#rdbuf)`->`[sputbackc](../standard-library/basic-streambuf-class.md#sputbackc). Jeśli rdbuf jest wskaźnikiem typu null lub jeśli wywołanie `sputbackc` zwraca **traits_type::** [EOF](../standard-library/char-traits-struct.md#eof), funkcja wywołuje metodę setstate [](../standard-library/basic-ios-class.md#setstate)(`badbit`). W każdym przypadku zwraca  **\*to**.

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

## <a name="read"></a>basic_istream:: Read

Odczytuje określoną liczbę znaków ze strumienia i zapisuje je w tablicy.

Ta metoda jest potencjalnie niebezpieczna, ponieważ polega na wywołującym, aby sprawdzić, czy przeszukane wartości są poprawne.

```cpp
basic_istream<Elem, Tr>& read(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*str*\
Tablica, w której mają zostać odczytane znaki.

*liczbą*\
Liczba znaków do odczytania.

### <a name="return-value"></a>Wartość zwracana

Strumień ( `*this`).

### <a name="remarks"></a>Uwagi

Niesformatowana funkcja wejściowa wyodrębnia do *liczby* elementów i zapisuje je w tablicy, zaczynając od _ `Str`. Wyodrębnianie kończy się na końcu pliku, w takim przypadku funkcja wywołuje metodę [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`). W każdym przypadku zwraca wartość `*this`.

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

## <a name="readsome"></a>basic_istream::readsome

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

Liczba znaków faktycznie odczytywanych, [gcount](#gcount).

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

## <a name="seekg"></a>basic_istream::seekg

Przenosi pozycję odczytu w strumieniu.

```cpp
basic_istream<Elem, Tr>& seekg(pos_type pos);

basic_istream<Elem, Tr>& seekg(off_type off, ios_base::seekdir way);
```

### <a name="parameters"></a>Parametry

*Terminal*\
Pozycja absolutna, w której ma zostać przeniesiony wskaźnik odczytu.

*Logowanie*\
Przesunięcie, aby przenieść wskaźnik odczytu względem *metody*.

*możliwości*\
Jedno z [ios_base:: seekdir](../standard-library/ios-base-class.md#seekdir) .

### <a name="return-value"></a>Wartość zwracana

Strumień (  **\*ten**).

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska wykonuje jednokrotne wyszukiwanie, druga funkcja członkowska wykonuje przeszukiwanie względne.

> [!NOTE]
> Nie należy używać drugiej funkcji składowej z plikami tekstowymi, ponieważ C++ Standard nie obsługuje wyszukiwania względnego w plikach tekstowych.

Jeśli [błąd](../standard-library/basic-ios-class.md#fail) ma wartość false, Pierwsza funkcja członkowska wywołuje **newpos** = [rdbuf](../standard-library/basic-ios-class.md#rdbuf) -> [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos)( `pos`) dla pewnego `pos_type` obiektu `newpos`tymczasowego. Jeśli `fail` ma wartość false, druga funkcja wywołuje **newpos** = **rdbuf** -> [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)( `off`, `way`). W obu przypadkach, jeśli ( `off_type`) **newpos** = = ( `off_type`) (-1) (operacja pozycjonowania zakończy się niepowodzeniem) `istr`, wywołania funkcji. [setstate](../standard-library/basic-ios-class.md#setstate) (`failbit`). Obie funkcje zwracają  **\*ten**.

Jeśli [błąd](../standard-library/basic-ios-class.md#fail) ma wartość true, funkcje składowe nie wykonują żadnych operacji.

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

## <a name="sentry"></a>basic_istream:: Sentry

Klasa zagnieżdżona opisuje obiekt, którego struktura deklaracji ma sformatowane i niesformatowane funkcje wejściowe.

Klasa Sentry {Public: Explicit Sentry (basic_istream\<elem, TR > & _Istr, bool _Noskip = false); operator bool () const;};

### <a name="remarks"></a>Uwagi

Jeśli `_Istr.` [dobry](../standard-library/basic-ios-class.md#good) ma wartość true, Konstruktor:

- Wywołania `_Istr`. [](../standard-library/basic-ios-class.md#tie)[Jeśli.](../standard-library/basic-ostream-class.md#flush)  ->  `_Istr` `tie`nie jest wskaźnikiem typu null

- Efektywnie wywołuje [](../standard-library/istream-functions.md#ws)metodę WS `_Istr`() `_Istr`, jeśli. [](../standard-library/ios-base-class.md#flags)**flagi&** [skipws](../standard-library/ios-functions.md#skipws) są różne od zera

Jeśli po dodanym przygotowaniu, należy `_Istr`. `good`ma wartość false, Konstruktor wywołuje `_Istr`. [setstate](../standard-library/basic-ios-class.md#setstate) (`failbit`). W każdym przypadku Konstruktor przechowuje wartość zwracaną przez `_Istr`. `good`w `status`programie. Późniejsze wywołanie w celu `operator bool` dostarczenia tej przechowywanej wartości.

## <a name="swap"></a>basic_istream:: swap

Wymienia zawartość dwóch `basic_istream` obiektów.

```cpp
void swap(basic_istream& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Odwołanie lvalue do `basic_istream` obiektu.

### <a name="remarks"></a>Uwagi

Funkcja członkowska wywołuje [basic_ios:: swap](../standard-library/basic-ios-class.md#swap)`(right)`. Wymienia również liczbę wyodrębniania z liczbą wyodrębniania dla *prawej*.

## <a name="sync"></a>basic_istream:: Sync

Synchronizuje urządzenie wejściowe skojarzone ze strumieniem z buforem strumienia.

```cpp
int sync();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli [rdbuf](../standard-library/basic-ios-class.md#rdbuf) jest wskaźnikiem o wartości null, funkcja zwraca wartość-1. W przeciwnym razie wywołuje `rdbuf`  ->  [pubsync](../standard-library/basic-streambuf-class.md#pubsync). Jeśli zwraca wartość-1, funkcja wywołuje metodę [setstate](../standard-library/basic-ios-class.md#setstate)(`badbit`) i zwraca wartość-1. W przeciwnym razie funkcja zwraca wartość zero.

## <a name="tellg"></a>basic_istream::tellg

Raportuje bieżącą pozycję odczytu w strumieniu.

```cpp
pos_type tellg();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca pozycja w strumieniu.

### <a name="remarks"></a>Uwagi

Jeśli [błąd](../standard-library/basic-ios-class.md#fail) ma wartość false, funkcja członkowska zwraca [rdbuf](../standard-library/basic-ios-class.md#rdbuf) -> [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(0 `cur`,, **in**). W przeciwnym razie zwraca `pos_type`(-1).

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

## <a name="unget"></a>basic_istream::unget

Umieszcza ostatnio odczytywany znak z powrotem do strumienia.

```cpp
basic_istream<Elem, Tr>& unget();
```

### <a name="return-value"></a>Wartość zwracana

Strumień (  **\*ten**).

### <a name="remarks"></a>Uwagi

Niesformatowana [Funkcja wejściowa](../standard-library/basic-istream-class.md) umieszcza poprzedni element w strumieniu, jeśli jest to możliwe, tak jak przez `rdbuf`wywołanie  ->  [sungetc](../standard-library/basic-streambuf-class.md#sungetc). Jeśli [rdbuf](../standard-library/basic-ios-class.md#rdbuf) jest wskaźnikiem typu null lub jeśli `sungetc` wywołanie zwraca **traits_type::** [EOF](../standard-library/basic-ios-class.md#eof), funkcja wywołuje metodę setstate [](../standard-library/basic-ios-class.md#setstate)(`badbit`). W każdym przypadku zwraca  **\*to**.

Aby uzyskać informacje o `unget` tym, jak może się nie powieść, zobacz [basic_streambuf:: sungetc](../standard-library/basic-streambuf-class.md#sungetc).

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

[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
