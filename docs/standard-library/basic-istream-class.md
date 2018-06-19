---
title: basic_istream — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 22dc1282dc165941c1a611583138c2d9aed51090
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33848927"
---
# <a name="basicistream-class"></a>basic_istream — Klasa

Zawiera opis obiektu, który kontroluje wyodrębniania elementów i zakodowanego obiektów z buforu strumienia elementami typu `Elem`, znanej także jako [char_type](../standard-library/basic-ios-class.md#char_type), którego cech znaków są określane przez klasę *Tr* , znanej także jako [traits_type](../standard-library/basic-ios-class.md#traits_type).

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_istream : virtual public basic_ios<Elem, Tr>
```

## <a name="remarks"></a>Uwagi

Większość elementu członkowskiego funkcje tego przeciążenia [operator >>](#op_gt_gt) sformatowanych funkcji wejściowych. One zgodne ze wzorcem:

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

Wiele innych funkcji elementów członkowskich są niesformatowany funkcji wejściowych. One zgodne ze wzorcem:

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

Obie grupy wywołania funkcji [metoda setstate](../standard-library/basic-ios-class.md#setstate)( **eofbit**) w momencie napotkania koniec pliku podczas wyodrębniania elementów.

Obiekt klasy `basic_istream` <  `Elem`, *Tr*> przechowuje:

- Publiczny wirtualny obiektu podstawowego klasy [basic_ios —](../standard-library/basic-ios-class.md)< `Elem`, *Tr*> `.`

- Liczba wyodrębniania ostatniej operacji wejściowych niesformatowany (nazywane **liczba** w poprzednim kodzie).

## <a name="example"></a>Przykład

Zobacz przykład [basic_ifstream — klasa](../standard-library/basic-ifstream-class.md) Aby dowiedzieć się więcej na temat strumienie wejściowe.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_istream](#basic_istream)|Tworzy obiekt typu `basic_istream`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[gcount](#gcount)|Zwraca liczbę znaków do odczytu podczas ostatniego niesformatowanych danych wejściowych.|
|[get](#get)|Odczytuje co najmniej jeden znak ze strumienia wejściowego.|
|[getline](#getline)|Odczytuje wiersz ze strumienia wejściowego.|
|[Ignoruj](#ignore)|Powoduje, że liczba elementów do pominięcia z bieżącej pozycji do odczytu.|
|[Podgląd](#peek)|Zwraca następny znak do odczytania.|
|[putback](#putback)|Przełącza określony znak w strumieniu.|
|[read](#read)|Odczytuje określoną liczbę znaków ze strumienia i przechowuje je w tablicy.|
|[readsome](#readsome)|Z buforu tylko do odczytu.|
|[seekg](#seekg)|Przenosi odczytu pozycji w strumieniu.|
|[Sentry](#sentry)|Zagnieżdżona klasa opisuje obiekt, którego deklaracji struktury niesformatowany funkcji wejściowych i sformatowany funkcji wejściowych.|
|[swap](#swap)|Zamienia to `basic_istream` obiektu dla udostępnionych `basic_istream` obiekt parametru.|
|[sync](#sync)|Synchronizuje urządzenie wejściowe skojarzone z strumienia z buforu strumienia.|
|[tellg](#tellg)|Zgłasza, że bieżący odczytu pozycją w strumieniu.|
|[unget](#unget)|Naraża ostatnio odczytać znaku do strumienia.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator>>](#op_gt_gt)|Wywołuje funkcję na strumień wejściowy lub odczytuje sformatowanych danych ze strumienia wejściowego.|
|[operator=](#op_eq)|Przypisuje `basic_istream` po prawej stronie operatora do tego obiektu. Jest to dotyczące przypisania przenoszenia `rvalue` odwołanie, które nie pozostawione kopii.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<istream >

**Namespace:** Standard

## <a name="basic_istream"></a>  basic_istream::basic_istream

Tworzy obiekt typu `basic_istream`.

```cpp
explicit basic_istream(
    basic_streambuf<Elem, Tr>* strbuf,
    bool _Isstd = false);

basic_istream(basic_istream&& right);
```

### <a name="parameters"></a>Parametry

`strbuf` Obiekt typu [basic_streambuf —](../standard-library/basic-streambuf-class.md).

`_Isstd` `true` Jeśli jest to Standardowy strumień; w przeciwnym razie `false`.

`right` A `basic_istream` obiektu do skopiowania.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje klasy podstawowej, przez wywołanie metody [init](../standard-library/basic-ios-class.md#init)(_S `trbuf`). Przechowuje także zerowej liczby wyodrębniania. Aby uzyskać więcej informacji na temat licznik ten uwzględnia wyodrębniania, zobacz sekcję uwag [basic_istream — klasa](../standard-library/basic-istream-class.md) temat.

Drugi Konstruktor inicjuje klasy podstawowej, przez wywołanie metody `move( right)`. Przechowuje także _R `ight.gcount()` w magazynach zerowej liczby wyodrębniania _R i liczba wyodrębniania `ight`.

### <a name="example"></a>Przykład

Zobacz przykład [basic_ifstream::basic_ifstream](../standard-library/basic-ifstream-class.md#basic_ifstream) Aby dowiedzieć się więcej na temat strumienie wejściowe.

## <a name="gcount"></a>  basic_istream::gcount

Zwraca liczbę znaków do odczytu podczas ostatniego niesformatowanych danych wejściowych.

```cpp
streamsize gcount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba wyodrębniania.

### <a name="remarks"></a>Uwagi

Użyj [basic_istream::get](#get) niesformatowany znaków.

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

```Output

a

```

```Output

      aType the letter 'a':
a
1
```

## <a name="get"></a>  basic_istream::Get

Odczytuje co najmniej jeden znak ze strumienia wejściowego.

```cpp
int_type get();

basic_istream<Elem, Tr>& get(Elem& Ch);
basic_istream<Elem, Tr>& get(Elem* str, streamsize count);
basic_istream<Elem, Tr>& get(Elem* str, streamsize count, Elem Delim);

basic_istream<Elem, Tr>& get(basic_streambuf<Elem, Tr>& strbuf);
basic_istream<Elem, Tr>& get(basic_streambuf<Elem, Tr>& strbuf, Elem Delim);
```

### <a name="parameters"></a>Parametry

`count` Liczba znaków do odczytu z `strbuf`.

`Delim` Znak, który należy zakończyć odczytu, jeśli okaże się przed `count`.

`str` Ciąg, w którym można zapisać.

`Ch` Znak do pobrania.

`strbuf` Bufor w jakim zostanie zapisane.

### <a name="return-value"></a>Wartość zwracana

Bez parametrów formę get zwraca element odczytany jako liczba całkowita lub koniec pliku. Formularze pozostałych zwrócić strumień (* `this`).

### <a name="remarks"></a>Uwagi

Pierwszy niesformatowany funkcji wejściowych wyodrębnia Jeśli to możliwe, element, tak, jakby zwracanie przez `rdbuf` ->  `sbumpc`. W przeciwnym razie zwraca **traits_type::**[eof](../standard-library/char-traits-struct.md#eof). Jeśli funkcja wyodrębnia żaden element, wywołuje metodę [metoda setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**).

Wyodrębnia funkcji second [int_type](../standard-library/basic-ios-class.md#int_type) elementu `meta` taki sam sposób. Jeśli `meta` porównuje równa **traits_type::eof**, wywołania funkcji `setstate`( **failbit**). W przeciwnym razie przechowuje **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)( `meta`) w `Ch`. Funkcja zwraca  **\*to**.

Zwraca funkcję trzeci **uzyskać**(_ *Str*, `count`, `widen`('\ **n**")).

Funkcja czwarty wyodrębnia do `count` - 1 elementów i zapisuje je w tablicy, począwszy od _ *Str*. Zawsze przechowuje `char_type` po wyodrębnieniu dowolne elementy są przechowywane. W kolejności testów zatrzymuje wyodrębniania:

- Na końcu pliku.

- Po funkcji wyodrębnia element, który porównuje równa `Delim`, w którym to przypadku element jest przywracane do kontrolowanej sekwencji.

- Po wyodrębnia funkcji `count` - 1 elementów.

Jeśli funkcja wyodrębnia żadnych elementów, wywołuje metodę `setstate`( **failbit**). W każdym przypadku zwraca  **\*to**.

Zwraca funkcję piątego **uzyskać**( **strbuf**, `widen`('\ **n**")).

Funkcja szóstego wyodrębnia elementów i wstawia je w **strbuf**. Wyodrębniania zatrzymuje się na końcu pliku lub na element, który porównuje równa _ *Delim,* który nie jest wyodrębniana. Powoduje także zatrzymanie, bez wyodrębniania elementu w danym przypadku wstawiania nie powiedzie się lub zgłasza wyjątek (która jest przechwycony, ale nie został zgłoszony). Jeśli funkcja wyodrębnia żadnych elementów, wywołuje metodę `setstate`( **failbit**). W każdym przypadku, funkcja zwraca  **\*to**.

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

## <a name="getline"></a>  basic_istream::getline

Pobiera linię ze strumienia wejściowego.

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

`count` Liczba znaków do odczytu z **strbuf**.

`Delim` Znak, który należy zakończyć odczytu, jeśli okaże się przed `count`.

`str` Ciąg, w którym można zapisać.

### <a name="return-value"></a>Wartość zwracana

Strumień (  **\*to**).

### <a name="remarks"></a>Uwagi

Pierwszy niesformatowanych danych wejściowych zwraca funkcji **getline**(_ *Str*, `count`, `widen`(" `\` **n**")).

Druga funkcja wyodrębnia do `count` - 1 elementów i zapisuje je w tablicy, począwszy od _ *Str*. Zawsze przechowuje ciąg znaków zakończenia po elementów wyodrębnionego, które przechowuje. W kolejności testów zatrzymuje wyodrębniania:

- Na końcu pliku.

- Po funkcji wyodrębnia element, który porównuje równa `Delim`, w którym to przypadku element nie jest odłożyć ani dołączane do kontrolowanej sekwencji.

- Po wyodrębnia funkcji `count` - 1 elementów.

Jeśli funkcja wyodrębnia żadnych elementów lub `count` - 1 elementów, wywołuje [metoda setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**). W każdym przypadku zwraca  **\*to**.

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

## <a name="ignore"></a>  basic_istream::Ignore

Powoduje, że liczba elementów do pominięcia z bieżącej pozycji do odczytu.

```cpp
basic_istream<Elem, Tr>& ignore(
    streamsize count = 1,
    int_type Delim = traits_type::eof());
```

### <a name="parameters"></a>Parametry

`count` Liczba elementów do pominięcia z bieżącej pozycji odczytu.

`Delim` Element, jeśli przed count, powoduje, że **Ignoruj** do zwrócenia, dzięki czemu wszystkie elementy po `Delim` do odczytu.

### <a name="return-value"></a>Wartość zwracana

Strumień (  **\*to**).

### <a name="remarks"></a>Uwagi

Niesformatowany funkcja wejściowych wyodrębnia do `count` elementów i odrzuca je. Jeśli `count` jest równe **numeric_limits\<int >:: max**, jednak jest traktowana jako dowolnie dużą. Wyodrębniania wczesne zatrzymuje się na końcu pliku lub elementu `Ch` tak, aby **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `Ch`) porównuje równa *Delim* (który również jest wyodrębniany). Funkcja zwraca  **\*to**.

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

## <a name="op_gt_gt"></a>  podstawowe\_istream::operator >>

Wywołuje funkcję na strumień wejściowy lub odczytuje sformatowanych danych ze strumienia wejściowego.

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

`Pfn` Wskaźnik funkcji.

`strbuf` Obiekt typu **stream_buf**.

`val` Wartość do odczytu ze strumienia.

### <a name="return-value"></a>Wartość zwracana

Strumień (  **\*to**).

### <a name="remarks"></a>Uwagi

\<Istream > nagłówka definiuje również kilka operatorów wyodrębniania globalnego. Aby uzyskać więcej informacji, zobacz [operator >> (\<istream >)](../standard-library/istream-operators.md#op_gt_gt).

Pierwszy funkcji członkowskiej zapewnia, że wyrażenie w postaci **istr**  >>  `ws` wywołania [ws](../standard-library/istream-functions.md#ws)( **istr**), a następnie zwraca  **\*to**. Drugi i trzeci funkcje upewnij się, że inne manipulatory, takich jak [szesnastkowych](../standard-library/ios-functions.md#hex), zachowują się podobnie. Pozostałe funkcje stanowią sformatowany funkcji wejściowych.

Funkcja:

```cpp
basic_istream& operator>>(
    basic_streambuf<Elem, Tr>* strbuf);
```

wyodrębnia elementy, jeśli _ *Strbuf* nie jest wskaźnika o wartości null i wstawia je w `strbuf`. Wyodrębnianie zatrzymuje się na końcu pliku. Również zatrzymuje bez wyodrębniania elementu w danym przypadku wstawiania nie powiedzie się lub zgłasza wyjątek (która jest przechwycony, ale nie został zgłoszony). Jeśli funkcja wyodrębnia żadnych elementów, wywołuje metodę [metoda setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**). W każdym przypadku, funkcja zwraca  **\*to**.

Funkcja:

```cpp
basic_istream& operator>>(bool& val);
```

wyodrębnia pola i konwertuje ją na wartość logiczną, wywołując [use_facet](../standard-library/basic-filebuf-class.md#open)  <  `num_get` \< **elementu**, **InIt**> ( [getloc](../standard-library/ios-base-class.md#getloc)). [Pobierz](../standard-library/ios-base-class.md#getloc)( **InIt**( [rdbuf](../standard-library/basic-ios-class.md#rdbuf)), `Init`(0),  **\*to**, `getloc`, `val`). W tym miejscu **InIt** jest zdefiniowany jako [istreambuf_iterator —](../standard-library/istreambuf-iterator-class.md) \< **elementu**, **Tr**>. Funkcja zwraca  **\*to**.

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

Każde Wyodrębnij pole i wykonać jego konwersję na wartość numeryczną, wywołując `use_facet` <  `num_get` \< **elementu**, **InIt**> ( `getloc`). [Pobierz](#get)( **InIt**( `rdbuf`), `Init`(0),  **\*to**, `getloc`, `val`). W tym miejscu **InIt** jest zdefiniowany jako `istreambuf_iterator` \< **elementu**, **Tr**>, a `val` ma typ **długi**,`unsigned long`, lub **void \***  zgodnie z potrzebami.

Jeśli skonwertowana wartość nie może być reprezentowany jako typ `val`, wywołania funkcji [metoda setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**). W każdym przypadku, funkcja zwraca  **\*to**.

Funkcje:

```cpp
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

Każde Wyodrębnij pole i wykonać jego konwersję na wartość numeryczną, wywołując `use_facet` <  `num_get` \< **elementu**, **InIt**> ( `getloc`). **Pobierz**( **InIt**( `rdbuf`), `Init`(0),  **\*to**, `getloc`, `val`). W tym miejscu **InIt** jest zdefiniowany jako `istreambuf_iterator` \< **elementu**, **Tr**>, a `val` ma typ **podwójne** lub `long double` zgodnie z potrzebami.

Jeśli skonwertowana wartość nie może być reprezentowany jako typ `val`, wywołania funkcji `setstate`( **failbit**). W każdym przypadku zwraca  **\*to**.

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

## <a name="op_eq"></a>  basic_istream::operator =

Przypisuje `basic_istream` po prawej stronie operatora do tego obiektu. Jest to dotyczące przypisania przenoszenia `rvalue` odwołanie, które nie pozostawione kopii.

```cpp
basic_istream& operator=(basic_istream&& right);
```

### <a name="parameters"></a>Parametry

`right` `rvalue` Odwołanie do `basic_ifstream` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca * to.

### <a name="remarks"></a>Uwagi

Operator członkowski wywołuje wymiany `( right)`.

## <a name="peek"></a>  basic_istream::Peek

Zwraca następny znak do odczytania.

```cpp
int_type peek();
```

### <a name="return-value"></a>Wartość zwracana

Następny znak, który będzie odczytywany.

### <a name="remarks"></a>Uwagi

Niesformatowany funkcja wejściowych wyodrębnia Jeśli to możliwe, element, tak, jakby zwracanie przez `rdbuf`  ->  [sgetc](../standard-library/basic-streambuf-class.md#sgetc). W przeciwnym razie zwraca **traits_type::**[eof](../standard-library/char-traits-struct.md#eof).

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

```Output

abcde

```

```Output

      abcdeType 'abcde': abcde
a abcde
```

## <a name="putback"></a>  basic_istream::putback

Przełącza określony znak w strumieniu.

```cpp
basic_istream<Elem, Tr>& putback(
    char_type Ch);
```

### <a name="parameters"></a>Parametry

`Ch` Znak do poddane strumienia.

### <a name="return-value"></a>Wartość zwracana

Strumień (  **\*to**).

### <a name="remarks"></a>Uwagi

[Niesformatowany wejściowe funkcji](../standard-library/basic-istream-class.md) powrotem przełącza `Ch`, jeśli to możliwe, tak jakby przez wywołanie [rdbuf](../standard-library/basic-ios-class.md#rdbuf)`->`[sputbackc](../standard-library/basic-streambuf-class.md#sputbackc). Jeśli rdbuf jest wskaźnika o wartości null lub wywołanie `sputbackc` zwraca **traits_type::**[eof](../standard-library/char-traits-struct.md#eof), wywołania funkcji [metoda setstate](../standard-library/basic-ios-class.md#setstate)( **badbit**). W każdym przypadku zwraca  **\*to**.

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

## <a name="read"></a>  basic_istream::Read

Odczytuje określoną liczbę znaków ze strumienia i przechowuje je w tablicy.

Ta metoda jest potencjalnie niebezpieczne, ponieważ zależy od obiekt wywołujący, aby sprawdzić, czy przekazane wartości są poprawne.

```cpp
basic_istream<Elem, Tr>& read(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Parametry

`str` Tablica, w której mają być odczytywane znaki.

`count` Liczba znaków do odczytania.

### <a name="return-value"></a>Wartość zwracana

Strumień ( `*this`).

### <a name="remarks"></a>Uwagi

Niesformatowany funkcja wejściowych wyodrębnia do `count` elementów i zapisuje je w tablicy, począwszy od _ `Str`. Wyodrębnianie wczesne zatrzymuje się na końcu pliku, w którym wywołuje przypadek funkcji [metoda setstate](../standard-library/basic-ios-class.md#setstate)( `failbit`). W każdym przypadku zwraca `*this`.

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

```Output

abcde

```

```Output

      abcdeType 'abcde': abcde
abcde
```

## <a name="readsome"></a>  basic_istream::readsome

Odczytuje określoną liczbę znaków.

Ta metoda jest potencjalnie niebezpieczne, ponieważ zależy od obiekt wywołujący, aby sprawdzić, czy przekazane wartości są poprawne.

```cpp
streamsize readsome(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Parametry

`str` Tablica, w którym `readsome` przechowuje znaki tekstu.

`count` Liczba znaków do odczytania.

### <a name="return-value"></a>Wartość zwracana

Liczba znaków, które faktycznie odczytanych [gcount](#gcount).

### <a name="remarks"></a>Uwagi

Niesformatowany funkcja wejściowych wyodrębnia do `count` elementy wejściowego strumienia i przechowuje je w tablicy `str`.

Ta funkcja nie oczekuje danych wejściowych. Odczytuje niezależnie od danych jest dostępna.

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

## <a name="seekg"></a>  basic_istream::seekg

Przenosi odczytu pozycji w strumieniu.

```cpp
basic_istream<Elem, Tr>& seekg(pos_type pos);

basic_istream<Elem, Tr>& seekg(off_type off, ios_base::seekdir way);
```

### <a name="parameters"></a>Parametry

`pos` Położenie bezwzględne, w którym można przenieść wskaźnik odczytu.

`off` Przesunięcie do odczytu wskaźnika względem `way`.

`way` Jeden z [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) wyliczenia.

### <a name="return-value"></a>Wartość zwracana

Strumień (  **\*to**).

### <a name="remarks"></a>Uwagi

Pierwszej funkcji Członkowskich wykonuje bezwzględną wyszukiwania, drugi funkcji członkowskiej wykonuje względną wyszukiwania.

> [!NOTE]
> Nie należy używać funkcji second elementu członkowskiego z plików tekstowych, ponieważ nie obsługuje standardu C++ względem wyszukiwania w plikach tekstowych.

Jeśli [niepowodzenie](../standard-library/basic-ios-class.md#fail) ma wartość false, pierwszego wywołania funkcji Członkowskich **newpos** = [rdbuf](../standard-library/basic-ios-class.md#rdbuf) -> [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos)( `pos`), w przypadku niektórych **pos_type** tymczasowy obiekt **newpos**. Jeśli **niepowodzenie** ma wartość false, drugi wywołania funkcji **newpos** = **rdbuf** -> [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)( `off`, `way`). W obu przypadkach jeśli ( `off_type`) **newpos** == ( `off_type`)(-1) (pozycjonowania niepowodzenia operacji), wywołania funkcji **istr**. [Metoda setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**). Obie funkcje zwracają  **\*to**.

Jeśli [niepowodzenie](../standard-library/basic-ios-class.md#fail) ma wartość true, nic nie rób funkcji elementów członkowskich.

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

## <a name="sentry"></a>  basic_istream::Sentry

Zagnieżdżona klasa opisuje obiekt, którego deklaracji struktury sformatowany i niesformatowany funkcji wejściowych.

sentry klasy {publicznego: jawne sentry (basic_istream —\<elementu, Tr > & _Istr, bool _Noskip = false); operator bool() const;};

### <a name="remarks"></a>Uwagi

Jeśli `_Istr.` [dobrej](../standard-library/basic-ios-class.md#good) ma wartość true, konstruktora:

- Wywołania `_Istr`. [Powiązanie](../standard-library/basic-ios-class.md#tie) -> [opróżnić](../standard-library/basic-ostream-class.md#flush) Jeśli `_Istr`. `tie` nie jest wskaźnika o wartości null

- Wywołuje [ws](../standard-library/istream-functions.md#ws)( `_Istr`) Jeśli `_Istr`. [flagi](../standard-library/ios-base-class.md#flags)**&**[skipws](../standard-library/ios-functions.md#skipws) jest różna od zera

Jeśli po takiego przygotowania `_Istr`. **dobrym** ma wartość false, Konstruktor wywołuje `_Istr`. [Metoda setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**). W każdym przypadku Konstruktor przechowuje wartość zwrócona przez `_Istr`. **dobrym** w **stan**. Wywołanie nowsze **bool — operator** zapewnia to przechowywanej wartości.

## <a name="swap"></a>  basic_istream::swap

Zamienia zawartość dwóch `basic_istream` obiektów.

```cpp
void swap(basic_istream& right);
```

### <a name="parameters"></a>Parametry

`right` Odwołania do wartości do `basic_istream` obiektu.

### <a name="remarks"></a>Uwagi

Wywołania funkcji Członkowskich [basic_ios::swap](../standard-library/basic-ios-class.md#swap)`(right)`. Również wymienia liczba wyodrębniania z licznikiem wyodrębniania dla `right`.

## <a name="sync"></a>  basic_istream::Sync

Synchronizuje urządzenie wejściowe skojarzone z strumienia z buforu strumienia.

```cpp
int sync();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli [rdbuf](../standard-library/basic-ios-class.md#rdbuf) jest wskaźnika o wartości null, funkcja zwraca wartość -1. W przeciwnym razie wywołuje `rdbuf`  ->  [pubsync](../standard-library/basic-streambuf-class.md#pubsync). Jeśli która zwraca wartość -1, wywołuje funkcję [metoda setstate](../standard-library/basic-ios-class.md#setstate)( **badbit**) i zwraca wartość -1. W przeciwnym razie funkcja zwraca wartość zero.

## <a name="tellg"></a>  basic_istream::tellg

Zgłasza, że bieżący odczytu pozycją w strumieniu.

```cpp
pos_type tellg();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca pozycja w strumieniu.

### <a name="remarks"></a>Uwagi

Jeśli [niepowodzenie](../standard-library/basic-ios-class.md#fail) wynosi false, zwraca funkcja członkowska [rdbuf](../standard-library/basic-ios-class.md#rdbuf) -> [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(0, `cur`, **w**). W przeciwnym razie zwraca `pos_type`(-1).

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

## <a name="unget"></a>  basic_istream::unget

Naraża ostatnio odczytać znaku do strumienia.

```cpp
basic_istream<Elem, Tr>& unget();
```

### <a name="return-value"></a>Wartość zwracana

Strumień (  **\*to**).

### <a name="remarks"></a>Uwagi

[Niesformatowany wejściowe funkcji](../standard-library/basic-istream-class.md) umieszcza ponownie poprzedni element w strumieniu, jeśli to możliwe, tak jakby przez wywołanie `rdbuf`  ->  [sungetc](../standard-library/basic-streambuf-class.md#sungetc). Jeśli [rdbuf](../standard-library/basic-ios-class.md#rdbuf) jest wskaźnika o wartości null, lub jeśli wywołanie `sungetc` zwraca **traits_type::**[eof](../standard-library/basic-ios-class.md#eof), wywołania funkcji [metoda setstate](../standard-library/basic-ios-class.md#setstate)() **badbit**). W każdym przypadku zwraca  **\*to**.

Aby uzyskać informacje na temat `unget` może zakończyć się niepowodzeniem, zobacz [basic_streambuf::sungetc](../standard-library/basic-streambuf-class.md#sungetc).

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

```Output

abc

```

```Output

      abcType 'abc': abc
abc
```

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
