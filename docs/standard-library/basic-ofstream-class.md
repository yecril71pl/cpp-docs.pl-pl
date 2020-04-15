---
title: basic_ofstream — Klasa
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_ofstream
- fstream/std::basic_ofstream::close
- fstream/std::basic_ofstream::is_open
- fstream/std::basic_ofstream::open
- fstream/std::basic_ofstream::rdbuf
- fstream/std::basic_ofstream::swap
helpviewer_keywords:
- std::basic_ofstream [C++]
- std::basic_ofstream [C++], close
- std::basic_ofstream [C++], is_open
- std::basic_ofstream [C++], open
- std::basic_ofstream [C++], rdbuf
- std::basic_ofstream [C++], swap
ms.assetid: 3bcc9c51-6dfc-4844-8fcc-22ef57c9dff1
ms.openlocfilehash: f2d0facd92e0ef1935f8218a6d323a62edb81e5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376792"
---
# <a name="basic_ofstream-class"></a>basic_ofstream — Klasa

Opisuje obiekt, który steruje wstawianiem elementów i zakodowanych obiektów `Tr` do buforu strumienia `Elem`klasy [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`,>, z `Tr`elementami typu , których cechy charakteru są określane przez klasę .

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ofstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem*\
Podstawowy element buforu plików.

*Tr*\
Cechy podstawowego elementu buforu plików (zwykle `char_traits` <  `Elem`>).

## <a name="remarks"></a>Uwagi

Gdy **wchar_t** specjalizacja `basic_ofstream` zapisów do pliku, jeśli plik jest otwarty w trybie tekstowym, zapisze sekwencję MBCS. Reprezentacja wewnętrzna użyje `wchar_t` buforu znaków.

Obiekt przechowuje obiekt `basic_filebuf` <  `Elem`klasy `Tr` ,>.

## <a name="example"></a>Przykład

W poniższym przykładzie `basic_ofstream` pokazano, jak utworzyć obiekt i napisać do niego tekst.

```cpp
// basic_ofstream_class.cpp
// compile with: /EHsc
#include <fstream>

using namespace std;

int main(int argc, char **argv)
{
    ofstream ofs("ofstream.txt");
    if (!ofs.bad())
    {
        ofs << "Writing to a basic_ofstream object..." << endl;
        ofs.close();
    }
}
```

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_ofstream](#basic_ofstream)|Tworzy obiekt typu `basic_ofstream`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Zamknij](#close)|Zamyka plik.|
|[is_open](#is_open)|Określa, czy plik jest otwarty.|
|[Otwórz](#open)|Otwiera plik.|
|[Rdbuf](#rdbuf)|Zwraca adres buforu przechowywanego strumienia.|
|[Wymiany](#swap)|Wymienić zawartość `basic_ofstream` tego na zawartość `basic_ofstream`dostarczonego .|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Przypisuje zawartość tego obiektu strumienia. Jest to przypisanie przenoszenia obejmujące, `rvalue reference` który nie pozostawia kopię za sobą.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<fstream>

**Przestrzeń nazw:** std

## <a name="basic_ofstreambasic_ofstream"></a><a name="basic_ofstream"></a>basic_ofstream::basic_ofstream

Tworzy obiekt typu `basic_ofstream`.

```cpp
basic_ofstream();

explicit basic_ofstream(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

explicit basic_ofstream(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

basic_ofstream(
    basic_ofstream&& right);
```

### <a name="parameters"></a>Parametry

*_Filename*\
Nazwa pliku do otwarcia.

*_mode*\
Jedno z wyliczenia w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Domyślna ochrona przed otwarciem `shflag` pliku, równoważna parametrowi [w _fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

*Prawo*\
Odwołanie rvalue do `basic_ofstream` obiektu używanego do `basic_ofstream` inicjowania tego obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor inicjuje klasę podstawową,`sb`wywołując `sb` [basic_ostream](../standard-library/basic-ostream-class.md)( ), gdzie jest przechowywanym obiektem [klasy basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>. Inicjuje `sb` również, `basic_filebuf` <  `Elem` `Tr` wywołując>.

Drugi i trzeci konstruktorzy inicjuje klasę podstawową przez wywołanie `basic_ostream` **(sb**). Inicjuje `sb` również, `basic_filebuf` <  `Elem` `Tr` wywołując ,> `sb`a następnie . [open](../standard-library/basic-filebuf-class.md#open) `_Filename`( `_Mode` , &#124; `ios_base::out`). Jeśli ta ostatnia funkcja zwraca wskaźnik zerowy,`failbit`konstruktor wywołuje [setstate](../standard-library/basic-ios-class.md#setstate)( ).

Czwarty konstruktor jest funkcją kopiowania. Inicjuje obiekt z zawartością *right*, traktowane jako odwołanie rvalue.

### <a name="example"></a>Przykład

W poniższym przykładzie `basic_ofstream` pokazano, jak utworzyć obiekt i napisać do niego tekst.

```cpp
// basic_ofstream_ctor.cpp
// compile with: /EHsc
#include <fstream>

using namespace std;

int main(int argc, char **argv)
{
    ofstream ofs("C:\\ofstream.txt");
    if (!ofs.bad())
    {
        ofs << "Writing to a basic_ofstream object..." << endl;
        ofs.close();
    }
}
```

## <a name="basic_ofstreamclose"></a><a name="close"></a>basic_ofstream::zamknij

Zamyka plik.

```cpp
void close();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego wywołuje [rdbuf](../standard-library/basic-ifstream-class.md#rdbuf)**->**[close](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) na przykład, który `close`używa .

## <a name="basic_ofstreamis_open"></a><a name="is_open"></a>basic_ofstream::is_open

Wskazuje, czy plik jest otwarty.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli plik jest otwarty, **false** inaczej.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open).

### <a name="example"></a>Przykład

```cpp
// basic_ofstream_is_open.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main( )
{
   using namespace std;
   ifstream file;
   // Open and close with a basic_filebuf
   file.rdbuf( )->open( "basic_ofstream_is_open.txt", ios::in );
   file.close( );
   if (file.is_open())
      cout << "it's open" << endl;
   else
      cout << "it's closed" << endl;
}
```

## <a name="basic_ofstreamopen"></a><a name="open"></a>basic_ofstream::otwórz

Otwiera plik.

```cpp
void open(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode);
```

### <a name="parameters"></a>Parametry

*_Filename*\
Nazwa pliku do otwarcia.

*_mode*\
Jedno z wyliczenia w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Domyślna ochrona przed otwarciem `shflag` pliku, równoważna parametrowi [w _fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego wywołuje [rdbuf](#rdbuf) **->** [open](../standard-library/basic-filebuf-class.md#open)(_ Nazwa `ios_base::out` *pliku*, `_Mode` &#124; ). Jeśli ta funkcja zwraca wskaźnik zerowy,`failbit`funkcja wywołuje [setstate](../standard-library/basic-ios-class.md#setstate)( ).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::otwórz](../standard-library/basic-filebuf-class.md#open) na przykład, który `open`używa .

## <a name="basic_ofstreamoperator"></a><a name="op_eq"></a>basic_ofstream::operator=

Przypisuje zawartość tego obiektu strumienia. Jest to przypisanie przenoszenia obejmujące, `rvalue reference` który nie pozostawia kopię za sobą.

```cpp
basic_ofstream& operator=(basic_ofstream&& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Odwołanie do `basic_ofstream` wartości r. do obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość `*this`.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zastępuje zawartość obiektu przy użyciu zawartości *prawa,* traktowane jako odwołanie rvalue.

## <a name="basic_ofstreamrdbuf"></a><a name="rdbuf"></a>basic_ofstream::rdbuf

Zwraca adres buforu przechowywanego strumienia.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Wartość zwracana

Zwraca adres buforu przechowywanego strumienia.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) na przykład, który `rdbuf`używa .

## <a name="basic_ofstreamswap"></a><a name="swap"></a>basic_ofstream::swap

Wymienia zawartość dwóch `basic_ofstream` obiektów.

```cpp
void swap(basic_ofstream& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Odwołanie `lvalue` do `basic_ofstream` innego obiektu.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego wymienia zawartość tego obiektu na zawartość *prawego*.

## <a name="see-also"></a>Zobacz też

[Klasa basic_ostream](../standard-library/basic-ostream-class.md)\
[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
