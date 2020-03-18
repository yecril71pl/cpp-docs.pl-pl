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
ms.openlocfilehash: a73803f25c4fb9e54703b8bca93e68fedb63074e
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416908"
---
# <a name="basic_ofstream-class"></a>basic_ofstream — Klasa

Opisuje obiekt, który kontroluje Wstawianie elementów i zakodowanych obiektów do buforu strumienia klasy [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, z elementami typu `Elem`, których cechy znaków są określane przez klasę `Tr`.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ofstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem*\
Podstawowy element buforu pliku.

\ *TR*
Cechy podstawowego elementu buforu plików (zwykle `char_traits`< `Elem`>).

## <a name="remarks"></a>Uwagi

Gdy **wchar_t** specjalizacji `basic_ofstream` zapisywania do pliku, jeśli plik zostanie otwarty w trybie tekstowym, nastąpi zapisanie sekwencji MBCS. Wewnętrzna reprezentacja użyje bufora `wchar_t` znaków.

Obiekt przechowuje obiekt klasy `basic_filebuf`< `Elem`, `Tr`>.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak utworzyć obiekt `basic_ofstream` i zapisać w nim tekst.

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

### <a name="constructors"></a>Konstruktorzy

|Konstruktor|Opis|
|-|-|
|[basic_ofstream](#basic_ofstream)|Tworzy obiekt typu `basic_ofstream`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[close](#close)|Zamyka plik.|
|[is_open](#is_open)|Określa, czy plik jest otwarty.|
|[open](#open)|Otwiera plik.|
|[rdbuf](#rdbuf)|Zwraca adres buforu zapisanego strumienia.|
|[wymiany](#swap)|Zamienij zawartość tego `basic_ofstream` dla zawartości podanej `basic_ofstream`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator =](#op_eq)|Przypisuje zawartość tego obiektu strumienia. Jest to przypisanie przenoszenia obejmujące `rvalue reference`, które nie pozostawia kopii w tle.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<fstream — >

**Przestrzeń nazw:** std

## <a name="basic_ofstream"></a>basic_ofstream:: basic_ofstream

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

*_Mode*\
Jedno z wyliczeń w [ios_base:: openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Domyślna ochrona otwierania plików, równoważna parametrowi `shflag` w [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

*prawa*\
Odwołanie rvalue do obiektu `basic_ofstream` używanego do inicjowania tego obiektu `basic_ofstream`.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje klasę bazową, wywołując [basic_ostream](../standard-library/basic-ostream-class.md)(`sb`), gdzie `sb` jest przechowywanym obiektem klasy [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>. Inicjuje również `sb` przez wywoływanie `basic_filebuf`< `Elem`, `Tr`>.

Drugi i trzeci Konstruktor inicjuje klasę bazową, wywołując `basic_ostream`( **SB**). Inicjuje również `sb` przez wywołanie `basic_filebuf`< `Elem`, `Tr`>, a następnie `sb`. [Otwórz](../standard-library/basic-filebuf-class.md#open)(`_Filename`, `_Mode` &#124; `ios_base::out`). Jeśli druga funkcja zwraca wskaźnik o wartości null, Konstruktor wywołuje metodę [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`).

Czwarty Konstruktor jest funkcją kopiowania. Inicjuje obiekt z zawartością *prawa*, traktowane jako odwołanie rvalue.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak utworzyć obiekt `basic_ofstream` i zapisać w nim tekst.

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

## <a name="close"></a>basic_ofstream:: Close

Zamyka plik.

```cpp
void close();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska wywołuje [rdbuf](../standard-library/basic-ifstream-class.md#rdbuf) **->** [Close](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf:: Close](../standard-library/basic-filebuf-class.md#close) , aby zapoznać się z przykładem korzystającym z `close`.

## <a name="is_open"></a>basic_ofstream:: is_open

Wskazuje, czy plik jest otwarty.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli plik jest otwarty; w przeciwnym razie **zwraca wartość false** .

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open).

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

## <a name="open"></a>basic_ofstream:: Open

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

*_Mode*\
Jedno z wyliczeń w [ios_base:: openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Domyślna ochrona otwierania plików, równoważna parametrowi `shflag` w [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Uwagi

Funkcja członkowska wywołuje [rdbuf](#rdbuf) **->** [otwórz](../standard-library/basic-filebuf-class.md#open)(_ *filename*`_Mode` &#124; `ios_base::out`). Jeśli ta funkcja zwróci wskaźnik o wartości null, funkcja wywołuje metodę [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf:: Open](../standard-library/basic-filebuf-class.md#open) , aby zapoznać się z przykładem korzystającym z `open`.

## <a name="op_eq"></a>basic_ofstream:: operator =

Przypisuje zawartość tego obiektu strumienia. Jest to przypisanie przenoszenia obejmujące `rvalue reference`, które nie pozostawia kopii w tle.

```cpp
basic_ofstream& operator=(basic_ofstream&& right);
```

### <a name="parameters"></a>Parametry

*prawa*\
Odwołanie rvalue do obiektu `basic_ofstream`.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość `*this`.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zastępuje zawartość obiektu przy użyciu zawartości *Right*, traktowanej jako odwołanie rvalue.

## <a name="rdbuf"></a>basic_ofstream:: rdbuf

Zwraca adres buforu zapisanego strumienia.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca adres buforu zapisanego strumienia.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf:: Close](../standard-library/basic-filebuf-class.md#close) , aby zapoznać się z przykładem korzystającym z `rdbuf`.

## <a name="swap"></a>basic_ofstream:: swap

Wymienia zawartość dwóch `basic_ofstream` obiektów.

```cpp
void swap(basic_ofstream& right);
```

### <a name="parameters"></a>Parametry

*prawa*\
`lvalue` odwołanie do innego obiektu `basic_ofstream`.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zamienia zawartość tego obiektu na zawartość z *prawej strony*.

## <a name="see-also"></a>Zobacz też

\ [klasy basic_ostream](../standard-library/basic-ostream-class.md)
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
\ [programowania iostream](../standard-library/iostream-programming.md)
[Konwencje iostream](../standard-library/iostreams-conventions.md)
