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
ms.openlocfilehash: ca0b25f5df6d4efb70e27fea6ef2323568134b2e
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964473"
---
# <a name="basicistream-class"></a>basic_istream — Klasa

Opisuje obiekt, który kontroluje wyodrębniania elementów i zakodowany obiektów z elementami typu bufor strumienia `Elem`, znane również jako [char_type](../standard-library/basic-ios-class.md#char_type), którego cech są określane przez klasę *Tr* , znane również jako [traits_type](../standard-library/basic-ios-class.md#traits_type).

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_istream : virtual public basic_ios<Elem, Tr>
```

## <a name="remarks"></a>Uwagi

Większość elementu członkowskiego funkcje tego przeciążenia [operator >>](#op_gt_gt) są sformatowane funkcje danych wejściowych. Są zgodne ze wzorcem:

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

Wiele innych funkcji elementów członkowskich są niesformatowane funkcje danych wejściowych. Są zgodne ze wzorcem:

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

Obie grupy wywołanie funkcji [setstate](../standard-library/basic-ios-class.md#setstate)(`eofbit`) w momencie napotkania koniec pliku podczas wyodrębniania elementów.

Obiekt klasy `basic_istream` <  `Elem`, *Tr*> przechowuje:

- Publiczny podstawowy obiekt wirtualnych klasy [basic_ios —](../standard-library/basic-ios-class.md)< `Elem`, *Tr*> `.`

- Liczba wyodrębniania dla ostatniej operacji wejściowych niesformatowany (o nazwie `count` w poprzednim kodzie).

## <a name="example"></a>Przykład

Zobacz przykład [basic_ifstream — klasa](../standard-library/basic-ifstream-class.md) Aby dowiedzieć się więcej na temat strumienie wejściowe.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_istream](#basic_istream)|Tworzy obiekt typu `basic_istream`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[gcount](#gcount)|Zwraca liczbę znaków odczytanych ostatniego niesformatowany danych wejściowych.|
|[get](#get)|Odczytuje co najmniej jeden znak ze strumienia wejściowego.|
|[getline](#getline)|Odczytuje wiersz ze strumienia wejściowego.|
|[Ignoruj](#ignore)|Powoduje, że liczba elementów, które mają zostać pominięte z bieżącej pozycji odczytu.|
|[Odbierz](#peek)|Zwraca następny znak do odczytania.|
|[putback](#putback)|Przełącza określony znak w strumieniu.|
|[read](#read)|Odczytuje określoną liczbę znaków ze strumienia i przechowuje je w tablicy.|
|[readsome —](#readsome)|Odczytywanie tylko buforu.|
|[seekg](#seekg)|Przenosi pozycję w strumieniu.|
|[Sentry](#sentry)|Zagnieżdżona klasa opisująca obiekt, którego deklaracji struktury niesformatowany funkcje danych wejściowych i sformatowany funkcje danych wejściowych.|
|[swap](#swap)|Wymienia to `basic_istream` obiektu dla podanych `basic_istream` obiektu parametru.|
|[sync](#sync)|Synchronizuje urządzenie wejściowe skojarzone z usługą stream z buforu strumienia.|
|[tellg —](#tellg)|Raporty Read bieżącej pozycji w strumieniu.|
|[unget](#unget)|Umieszcza ostatnio odczytują znak do strumienia.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator>>](#op_gt_gt)|Wywołuje funkcję dla strumienia wejściowego lub odczyty sformatowanych danych ze strumienia wejściowego.|
|[operator=](#op_eq)|Przypisuje `basic_istream` po prawej stronie operatora do tego obiektu. Jest to przeniesienia przypisania obejmujące `rvalue` odwołania, który nie pozostawione kopię.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<istream >

**Namespace:** standardowe

## <a name="basic_istream"></a>  basic_istream::basic_istream

Tworzy obiekt typu `basic_istream`.

```cpp
explicit basic_istream(
    basic_streambuf<Elem, Tr>* strbuf,
    bool _Isstd = false);

basic_istream(basic_istream&& right);
```

### <a name="parameters"></a>Parametry

*strbuf* obiektu typu [basic_streambuf](../standard-library/basic-streambuf-class.md).

*_Isstd* **true** Jeśli jest to Standardowy strumień; w przeciwnym razie **false**.

*prawy* A `basic_istream` obiektu do skopiowania.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje klasę bazową, wywołując [init](../standard-library/basic-ios-class.md#init)(_S `trbuf`). Przechowuje także zera, liczba wyodrębniania. Aby uzyskać więcej informacji na temat tej liczby wyodrębniania, zobacz sekcję Uwagi [basic_istream — klasa](../standard-library/basic-istream-class.md) temat.

Drugi Konstruktor inicjuje klasę bazową, wywołując `move( right)`. Przechowuje także _R `ight.gcount()` liczba wyodrębniania i magazyny zero w obliczeniach wyodrębniania _R `ight`.

### <a name="example"></a>Przykład

Zobacz przykład [basic_ifstream::basic_ifstream](../standard-library/basic-ifstream-class.md#basic_ifstream) Aby dowiedzieć się więcej na temat strumienie wejściowe.

## <a name="gcount"></a>  basic_istream::gcount

Zwraca liczbę znaków odczytanych ostatniego niesformatowany danych wejściowych.

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

*Liczba* liczba znaków do odczytu z `strbuf`.

*Delim* znak, który powinien wygasają odczytu, jeśli zostanie osiągnięty zanim *liczba*.

*str* ciąg, w którym mają zostać zapisane.

*Ch* znaku można pobrać.

*strbuf* buforu, w którym mają zostać zapisane.

### <a name="return-value"></a>Wartość zwracana

Bez parametrów formularza get zwraca element, który został odczytany jako liczba całkowita lub koniec pliku. Pozostałych form zwrócić strumień, który (* `this`).

### <a name="remarks"></a>Uwagi

Pierwszego dnia niesformatowany funkcje danych wejściowych wyodrębnia, jeśli jest to możliwe, elementu, tak, jakby przez zwracanie `rdbuf` ->  `sbumpc`. W przeciwnym razie zwraca **traits_type::**[eof](../standard-library/char-traits-struct.md#eof). Jeśli funkcja wyodrębnia żaden element, wywołuje metodę [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`).

Druga funkcja wyodrębnia [int_type](../standard-library/basic-ios-class.md#int_type) elementu `meta` taki sam sposób. Jeśli `meta` porównuje równa **traits_type::eof**, wywołania funkcji `setstate`( **failbit**). W przeciwnym razie przechowuje **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)( `meta`) w `Ch`. Funkcja zwraca  **\*to**.

Trzecia funkcja zwraca **uzyskać**(_ *Str*, `count`, `widen`("\ **n**")).

Funkcja czwarty wyodrębnia maksymalnie *liczba* - 1 elementy i przechowuje je w tablicy, zaczynając od _ *Str*. Zawsze przechowuje `char_type` po wyodrębnieniu dowolne elementy, które są przechowywane. W kolejności testów zatrzymuje się wyodrębnienie:

- Na końcu pliku.

- Po funkcji wyodrębnia element, który jest równy *Delim*, w którym to przypadku element jest przywracane do kontrolowanej sekwencji.

- Po funkcji wyodrębnia *liczba* - 1 elementów.

Jeśli funkcja wyodrębnia żadnych elementów, wywołuje metodę `setstate`( **failbit**). W każdym przypadku zwraca  **\*to**.

Piąty funkcja zwraca **uzyskać**( **strbuf**, `widen`("\ **n**")).

Funkcja szóstego wyodrębnia elementów i wstawia je w `strbuf`. Wyodrębnianie zatrzymuje się na końcu pliku, lub na element, który porównuje równa _ *Delim,* który nie jest wyodrębniany. On również nie będzie możliwy, bez wyodrębniania w danym elemencie, jeśli wstawienie ulegnie awarii lub zgłasza wyjątek (która jest przechwycony, ale nie zgłaszany ponownie). Jeśli funkcja wyodrębnia żadnych elementów, wywołuje metodę `setstate`( **failbit**). W każdym przypadku, funkcja zwraca  **\*to**.

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

*Liczba* liczba znaków do odczytu z `strbuf`.

*Delim* znak, który powinien wygasają odczytu, jeśli zostanie osiągnięty zanim *liczba*.

*str* ciąg, w którym mają zostać zapisane.

### <a name="return-value"></a>Wartość zwracana

Strumień (  **\*to**).

### <a name="remarks"></a>Uwagi

Pierwsze zachowanie niesformatowany dane wejściowe funkcji zwraca **getline —**(_ *Str*, `count`, `widen`(" `\` **n**")).

Druga funkcja wyodrębnia maksymalnie *liczba* - 1 elementy i przechowuje je w tablicy, zaczynając od _ *Str*. Zawsze przechowuje znak zakończenia ciągu po wyodrębnione elementy, które przechowuje. W kolejności testów zatrzymuje się wyodrębnienie:

- Na końcu pliku.

- Po funkcji wyodrębnia element, który jest równy *Delim*, w którym to przypadku element nie jest ponownie ani dołączany do kontrolowanej sekwencji.

- Po funkcji wyodrębnia *liczba* - 1 elementów.

Jeśli funkcja wyodrębnia żadnych elementów lub *liczba* - 1 elementów wywoływanych przez nią [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`). W każdym przypadku zwraca  **\*to**.

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

Powoduje, że liczba elementów, które mają zostać pominięte z bieżącej pozycji odczytu.

```cpp
basic_istream<Elem, Tr>& ignore(
    streamsize count = 1,
    int_type Delim = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*Liczba* liczba elementów do pominięcia z bieżącej pozycja odczytu.

*Delim* element, który, jeśli osiągnięty zanim liczba, powoduje, że `ignore` do zwrócenia, dzięki czemu wszystkie elementy po *Delim* do odczytu.

### <a name="return-value"></a>Wartość zwracana

Strumień (  **\*to**).

### <a name="remarks"></a>Uwagi

Niesformatowany funkcja wejściowych wyodrębnia maksymalnie *liczba* elementów i ich usuwanie. Jeśli *liczba* jest równa **numeric_limits —\<int >:: max**, jednak jest ona traktowana jak dowolnie duże. Wyodrębniania wcześnie zatrzymuje się na końcu pliku lub elementu `Ch` tak, aby **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `Ch`) porównuje równa *Delim* (który jest on także wyodrębniany). Funkcja zwraca  **\*to**.

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

Wywołuje funkcję dla strumienia wejściowego lub odczyty sformatowanych danych ze strumienia wejściowego.

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

*Nazwy Pfn* wskaźnika funkcji.

*strbuf* obiektu typu `stream_buf`.

*Val* wartości, które można odczytać ze strumienia.

### <a name="return-value"></a>Wartość zwracana

Strumień (  **\*to**).

### <a name="remarks"></a>Uwagi

\<Istream > nagłówka definiuje również kilka operatorów globalnych wyodrębniania. Aby uzyskać więcej informacji, zobacz [operator >> (\<istream >)](../standard-library/istream-operators.md#op_gt_gt).

Pierwsza funkcja elementu członkowskiego zapewnia, że wyrażenie w formie **istr**  >>  `ws` wywołania [ws](../standard-library/istream-functions.md#ws)( **istr**), a następnie zwraca  **\*to**. Drugi i trzeci funkcje upewnij się, że inne manipulatory, takich jak [szesnastkowy](../standard-library/ios-functions.md#hex), działają w podobny sposób. Pozostałe funkcje stanowią sformatowane funkcje danych wejściowych.

Funkcja:

```cpp
basic_istream& operator>>(
    basic_streambuf<Elem, Tr>* strbuf);
```

wyodrębnia elementów, jeśli _ *Strbuf* nie jest wskaźnikiem typu null, a następnie wstawianie ich w *strbuf*. Wyodrębnianie zatrzymuje się na końcu pliku. On również nie będzie możliwy bez wyodrębniania w danym elemencie, jeśli wstawienie ulegnie awarii lub zgłasza wyjątek (która jest przechwycony, ale nie zgłaszany ponownie). Jeśli funkcja wyodrębnia żadnych elementów, wywołuje metodę [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`). W każdym przypadku, funkcja zwraca  **\*to**.

Funkcja:

```cpp
basic_istream& operator>>(bool& val);
```

wyodrębnia pola i konwertuje ją na wartość logiczną, wywołując [use_facet](../standard-library/basic-filebuf-class.md#open)  <  `num_get` \< **Elem**, **InIt**> ( [getloc —](../standard-library/ios-base-class.md#getloc)). [Pobierz](../standard-library/ios-base-class.md#getloc)( **InIt**( [rdbuf —](../standard-library/basic-ios-class.md#rdbuf)), `Init`(0),  **\*to**, `getloc`, `val`). W tym miejscu **InIt** jest zdefiniowany jako [istreambuf_iterator](../standard-library/istreambuf-iterator-class.md) \< **Elem**, **Tr**>. Funkcja zwraca  **\*to**.

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

Każda Wyodrębnij pola i przekonwertować go na wartość liczbową, wywołując `use_facet` <  `num_get` \< **Elem**, **InIt**> ( `getloc`). [Pobierz](#get)( **InIt**( `rdbuf`), `Init`(0),  **\*to**, `getloc`, `val`). W tym miejscu **InIt** jest zdefiniowany jako `istreambuf_iterator` \< **Elem**, **Tr**>, a `val` ma typ **długie**,**unsigned long**, lub **void \***  zgodnie z potrzebami.

Jeśli typ nie może być reprezentowana przekonwertowana wartości `val`, wywołania funkcji [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`). W każdym przypadku, funkcja zwraca  **\*to**.

Funkcje:

```cpp
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

Każda Wyodrębnij pola i przekonwertować go na wartość liczbową, wywołując `use_facet` <  `num_get` \< **Elem**, **InIt**> ( `getloc`). **Pobierz**( **InIt**( `rdbuf`), `Init`(0),  **\*to**, `getloc`, `val`). W tym miejscu `InIt` jest zdefiniowany jako `istreambuf_iterator` \< **Elem**, **Tr**>, i `val` ma typ **double** lub **długi podwójne** zgodnie z potrzebami.

Jeśli typ nie może być reprezentowana przekonwertowana wartości `val`, wywołania funkcji `setstate`( **failbit**). W każdym przypadku zwraca  **\*to**.

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

Przypisuje `basic_istream` po prawej stronie operatora do tego obiektu. Jest to przeniesienia przypisania obejmujące `rvalue` odwołania, który nie pozostawione kopię.

```cpp
basic_istream& operator=(basic_istream&& right);
```

### <a name="parameters"></a>Parametry

*prawy* `rvalue` odwołanie do `basic_ifstream` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca * to.

### <a name="remarks"></a>Uwagi

Operator składowy wywołuje wymiany `( right)`.

## <a name="peek"></a>  basic_istream::Peek

Zwraca następny znak do odczytania.

```cpp
int_type peek();
```

### <a name="return-value"></a>Wartość zwracana

Następny znak, który będzie odczytywany.

### <a name="remarks"></a>Uwagi

Niesformatowany funkcja wejściowych wyodrębniania, jeśli jest to możliwe, elementu, tak, jakby przez zwracanie `rdbuf`  ->  [sgetc —](../standard-library/basic-streambuf-class.md#sgetc). W przeciwnym razie zwraca **traits_type::**[eof](../standard-library/char-traits-struct.md#eof).

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

*Ch* znak zostać umieszczona w strumieniu.

### <a name="return-value"></a>Wartość zwracana

Strumień (  **\*to**).

### <a name="remarks"></a>Uwagi

[Niesformatowany wprowadzania funkcji](../standard-library/basic-istream-class.md) przywraca *Ch*, jeśli jest to możliwe, tak, jakby przez wywołanie [rdbuf —](../standard-library/basic-ios-class.md#rdbuf)`->`[sputbackc —](../standard-library/basic-streambuf-class.md#sputbackc). Jeśli rdbuf — jest wskaźnikiem typu null lub wywołanie `sputbackc` zwraca **traits_type::**[eof](../standard-library/char-traits-struct.md#eof), wywołania funkcji [setstate](../standard-library/basic-ios-class.md#setstate)(`badbit`). W każdym przypadku zwraca  **\*to**.

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

Ta metoda jest potencjalnie niebezpieczne, ponieważ opiera się na obiekt wywołujący, aby sprawdzić, czy przekazanych wartości są poprawne.

```cpp
basic_istream<Elem, Tr>& read(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*str* tablicy, w której mają zostać odczytane znaków.

*Liczba* liczba znaków do odczytania.

### <a name="return-value"></a>Wartość zwracana

Strumień ( `*this`).

### <a name="remarks"></a>Uwagi

Niesformatowany funkcja wejściowych wyodrębnia maksymalnie *liczba* elementy i przechowuje je w tablicy, zaczynając od _ `Str`. Wyodrębnianie wcześnie zatrzymuje się na końcu pliku, w którym przypadku funkcja wywołuje [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`). W każdym przypadku zwraca `*this`.

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

Ta metoda jest potencjalnie niebezpieczne, ponieważ opiera się na obiekt wywołujący, aby sprawdzić, czy przekazanych wartości są poprawne.

```cpp
streamsize readsome(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*str* tablicy, w którym `readsome` znaki odczytuje są przechowywane.

*Liczba* liczba znaków do odczytania.

### <a name="return-value"></a>Wartość zwracana

Liczba znaków odczytanych w rzeczywistości [gcount —](#gcount).

### <a name="remarks"></a>Uwagi

Tę funkcję, danych wejściowych niesformatowany wyodrębnia maksymalnie *liczba* elementy z danych wejściowych, przesyłanie strumieniowe i przechowuje je w tablicy *str*.

Ta funkcja nie czeka na dane wejściowe. Odczytuje dowolne dane są dostępne.

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

Przenosi pozycję w strumieniu.

```cpp
basic_istream<Elem, Tr>& seekg(pos_type pos);

basic_istream<Elem, Tr>& seekg(off_type off, ios_base::seekdir way);
```

### <a name="parameters"></a>Parametry

*POS* położenie bezwzględne, w której chcesz przenieść wskaźnik odczytu.

*Wyłącz* przesunięcia wskaźnika odczytu względem *sposób*.

*sposób* jednego z [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) wyliczenia.

### <a name="return-value"></a>Wartość zwracana

Strumień (  **\*to**).

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego wykonuje wyszukiwanie bezwzględny, funkcja drugiego członka wykonuje wyszukiwanie względnych.

> [!NOTE]
> Nie należy używać funkcja drugiego członka z plików tekstowych, ponieważ Standard C++ nie obsługuje względnych szuka w plikach tekstowych.

Jeśli [się nie powieść](../standard-library/basic-ios-class.md#fail) ma wartość FAŁSZ, pierwszego wywołania funkcji elementu członkowskiego **newpos** = [rdbuf —](../standard-library/basic-ios-class.md#rdbuf) -> [pubseekpos —](../standard-library/basic-streambuf-class.md#pubseekpos)( `pos`), w przypadku niektórych `pos_type` tymczasowy obiekt `newpos`. Jeśli `fail` ma wartość false, drugi wywołania funkcji **newpos** = **rdbuf —** -> [pubseekoff —](../standard-library/basic-streambuf-class.md#pubseekoff)( `off`, `way`). W obu przypadkach jeśli ( `off_type`) **newpos** == ( `off_type`)(-1) (pozycjonowania operacja kończy się niepowodzeniem), wywołania funkcji `istr`. [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`). Obie funkcje zwracają  **\*to**.

Jeśli [się nie powieść](../standard-library/basic-ios-class.md#fail) ma wartość true, nic nie rób funkcje elementów członkowskich.

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

Zagnieżdżona klasa opisująca obiekt, którego deklaracji struktury funkcje danych wejściowych sformatowany i niesformatowane.

sentry klasy {publicznej: jawne sentry (basic_istream\<Elem, Tr > & _Istr, bool _Noskip = false); operator bool() const;};

### <a name="remarks"></a>Uwagi

Jeśli `_Istr.` [dobre](../standard-library/basic-ios-class.md#good) ma wartość true, Konstruktor:

- Wywołania `_Istr`. [Powiązanie](../standard-library/basic-ios-class.md#tie) -> [opróżniania](../standard-library/basic-ostream-class.md#flush) Jeśli `_Istr`. `tie` nie jest wskaźnikiem typu null

- Skutecznie wywołuje [ws](../standard-library/istream-functions.md#ws)( `_Istr`) Jeśli `_Istr`. [flagi](../standard-library/ios-base-class.md#flags)**&**[skipws](../standard-library/ios-functions.md#skipws) jest różna od zera

Jeśli po takiego przygotowania `_Istr`. `good` ma wartość FAŁSZ, Konstruktor wywołuje `_Istr`. [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`). W każdym przypadku Konstruktor przechowuje wartość zwrócona przez obiekt `_Istr`. `good` w `status`. Nowsze wywołanie `operator bool` zapewnia to przechowywanej wartości.

## <a name="swap"></a>  basic_istream::swap

Zamienia zawartości dwóch `basic_istream` obiektów.

```cpp
void swap(basic_istream& right);
```

### <a name="parameters"></a>Parametry

*prawy* odwołania wartościowanego lewostronnie do `basic_istream` obiektu.

### <a name="remarks"></a>Uwagi

Wywołania funkcji elementu członkowskiego [basic_ios::swap](../standard-library/basic-ios-class.md#swap)`(right)`. Również zamienia liczba wyodrębniania z liczbą wyodrębniania dla *prawo*.

## <a name="sync"></a>  basic_istream::Sync

Synchronizuje urządzenie wejściowe skojarzone z usługą stream z buforu strumienia.

```cpp
int sync();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli [rdbuf —](../standard-library/basic-ios-class.md#rdbuf) jest pustym wskaźnikiem, funkcja zwraca wartość -1. W przeciwnym razie wywoływanych przez nią `rdbuf`  ->  [pubsync —](../standard-library/basic-streambuf-class.md#pubsync). Jeśli, zwraca wartość -1, funkcja wywołuje [setstate](../standard-library/basic-ios-class.md#setstate)(`badbit`) i zwraca wartość -1. W przeciwnym razie funkcja zwraca wartość zero.

## <a name="tellg"></a>  basic_istream::tellg

Raporty Read bieżącej pozycji w strumieniu.

```cpp
pos_type tellg();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca pozycja w strumieniu.

### <a name="remarks"></a>Uwagi

Jeśli [się nie powieść](../standard-library/basic-ios-class.md#fail) ma wartość FAŁSZ, funkcja elementu członkowskiego zwraca [rdbuf —](../standard-library/basic-ios-class.md#rdbuf) -> [pubseekoff —](../standard-library/basic-streambuf-class.md#pubseekoff)(0, `cur`, **w**). W przeciwnym razie zwraca `pos_type`(-1).

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

Umieszcza ostatnio odczytują znak do strumienia.

```cpp
basic_istream<Elem, Tr>& unget();
```

### <a name="return-value"></a>Wartość zwracana

Strumień (  **\*to**).

### <a name="remarks"></a>Uwagi

[Niesformatowany wprowadzania funkcji](../standard-library/basic-istream-class.md) przywraca poprzedni element w usłudze stream, jeśli jest to możliwe tak, jakby przez wywołanie `rdbuf`  ->  [sungetc —](../standard-library/basic-streambuf-class.md#sungetc). Jeśli [rdbuf —](../standard-library/basic-ios-class.md#rdbuf) jest wskaźnikiem typu null, lub jeśli wywołanie `sungetc` zwraca **traits_type::**[eof](../standard-library/basic-ios-class.md#eof), wywołania funkcji [setstate](../standard-library/basic-ios-class.md#setstate)() `badbit`). W każdym przypadku zwraca  **\*to**.

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
