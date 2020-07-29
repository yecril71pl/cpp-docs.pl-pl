---
title: basic_ifstream — Klasa
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_ifstream
- fstream/std::basic_ifstream::close
- fstream/std::basic_ifstream::is_open
- fstream/std::basic_ifstream::open
- fstream/std::basic_ifstream::rdbuf
- fstream/std::basic_ifstream::swap
helpviewer_keywords:
- std::basic_ifstream [C++]
- std::basic_ifstream [C++], close
- std::basic_ifstream [C++], is_open
- std::basic_ifstream [C++], open
- std::basic_ifstream [C++], rdbuf
- std::basic_ifstream [C++], swap
ms.assetid: 366cd9a7-efc4-4b7f-ba10-c8271e47ffcf
ms.openlocfilehash: f4f5ddd3d1c0c595dd1661fab73f5267fb161593
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219290"
---
# <a name="basic_ifstream-class"></a>basic_ifstream — Klasa

Opisuje obiekt, który kontroluje wyodrębnianie elementów i zakodowanych obiektów z bufora strumienia klasy [basic_filebuf](../standard-library/basic-filebuf-class.md) <  `Elem` , `Tr`>, z elementami typu `Elem` , których cechy znaku są określane przez klasę `Tr` .

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ifstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem*\
Podstawowy element buforu pliku.

*Zdawczy*\
Cechy podstawowego elementu buforu plików (zwykle `char_traits` <  `Elem`>).

## <a name="remarks"></a>Uwagi

Obiekt przechowuje obiekt klasy `basic_filebuf` <  `Elem` , `Tr`>.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak czytać tekst z pliku.

```cpp
// basic_ifstream_class.cpp
// compile with: /EHsc

#include <fstream>
#include <iostream>

using namespace std;

int main(int argc, char **argv)
{
    ifstream ifs("basic_ifstream_class.txt");
    if (!ifs.bad())
    {
        // Dump the contents of the file to cout.
        cout << ifs.rdbuf();
        ifs.close();
    }
}
```

## <a name="input-basic_ifstream_classtxt"></a>Dane wejściowe: basic_ifstream_class.txt

```cpp
This is the contents of basic_ifstream_class.txt.
```

## <a name="output"></a>Dane wyjściowe

```cpp
This is the contents of basic_ifstream_class.txt.
```

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[basic_ifstream](#basic_ifstream)|Inicjuje nowe wystąpienie `basic_ifstream` obiektu.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[ściśle](#close)|Zamyka plik.|
|[is_open](#is_open)|Określa, czy plik jest otwarty.|
|[Otwórz](#open)|Otwiera plik.|
|[rdbuf](#rdbuf)|Zwraca adres buforu zapisanego strumienia.|
|[wymiany](#swap)|Wymienia zawartość tego elementu `basic_ifstream` dla zawartości podanej `basic_ifstream` .|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator =](#op_eq)|Przypisuje zawartość tego obiektu strumienia. Jest to przypisanie przenoszenia obejmujące element `rvalue` , który nie pozostawia kopii w tle.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<fstream>

**Przestrzeń nazw:** std

## <a name="basic_ifstreambasic_ifstream"></a><a name="basic_ifstream"></a>basic_ifstream:: basic_ifstream

Konstruuje obiekt typu `basic_ifstream` .

```cpp
basic_ifstream();

explicit basic_ifstream(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

explicit basic_ifstream(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

basic_ifstream(basic_ifstream&& right);
```

### <a name="parameters"></a>Parametry

*_Filename*\
Nazwa pliku do otwarcia.

*_Mode*\
Jedno z wyliczeń w [ios_base:: openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Domyślna ochrona otwierania plików, równoważna `shflag` parametrowi w [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje klasę bazową, wywołując [basic_istream](../standard-library/basic-istream-class.md)( `sb` ), gdzie `sb` jest przechowywany obiekt klasy [basic_filebuf](../standard-library/basic-filebuf-class.md) <  `Elem` , `Tr`>. Inicjuje się to również `sb` przez wywołanie `basic_filebuf` <  `Elem` , `Tr`>.

Drugi i trzeci Konstruktor inicjuje klasę bazową przez wywołanie `basic_istream` ( `sb` ). Jest on również inicjowany `sb` przez wywołanie [basic_filebuf](../standard-library/basic-filebuf-class.md#basic_filebuf) <  `Elem` , `Tr`>, a następnie `sb` . [Otwórz](../standard-library/basic-filebuf-class.md#open)( `_Filename` , `_Mode` &#124; `ios_base::in` ). Jeśli druga funkcja zwraca wskaźnik o wartości null, Konstruktor wywołuje metodę **setstate**( `failbit` ).

Czwarty Konstruktor inicjuje obiekt z zawartością `right` , traktowany jako odwołanie rvalue.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak czytać tekst z pliku. Aby utworzyć plik, zobacz przykład dla [basic_ofstream:: basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream).

```cpp
// basic_ifstream_ctor.cpp
// compile with: /EHsc

#include <fstream>
#include <iostream>

using namespace std;

int main(int argc, char **argv)
{
    ifstream ifs("basic_ifstream_ctor.txt");
    if (!ifs.bad())
    {
        // Dump the contents of the file to cout.
        cout << ifs.rdbuf();
        ifs.close();
    }
}
```

## <a name="basic_ifstreamclose"></a><a name="close"></a>basic_ifstream:: Close

Zamyka plik.

```cpp
void close();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska wywołuje [rdbuf](#rdbuf) **->** [Close](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf:: Close](../standard-library/basic-filebuf-class.md#close) , aby zapoznać się z przykładem, który używa `close` .

## <a name="basic_ifstreamis_open"></a><a name="is_open"></a>basic_ifstream:: is_open

Określa, czy plik jest otwarty.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli plik jest otwarty, **`false`** w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf:: is_open](../standard-library/basic-filebuf-class.md#is_open) , aby zapoznać się z przykładem `is_open` .

## <a name="basic_ifstreamopen"></a><a name="open"></a>basic_ifstream:: Open

Otwiera plik.

```cpp
void open(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in,
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
Domyślna ochrona otwierania plików, równoważna `shflag` parametrowi w [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Uwagi

Funkcja członkowska wywołuje [rdbuf](#rdbuf) **->** [Open](../standard-library/basic-filebuf-class.md#open)(_ *filename*, `_Mode` &#124; **ios_base:: in**). Jeśli operacja otwierania nie powiedzie się, funkcja wywołuje metodę [setstate](../standard-library/basic-ios-class.md#setstate)( `failbit` ), która może zgłosić wyjątek ios_base:: Failure.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf:: Open](../standard-library/basic-filebuf-class.md#open) , aby zapoznać się z przykładem, który używa `open` .

## <a name="basic_ifstreamoperator"></a><a name="op_eq"></a>basic_ifstream:: operator =

Przypisuje zawartość tego obiektu strumienia. Jest to przypisanie przenoszenia obejmujące rvalue, które nie pozostawia kopii w tle.

```cpp
basic_ifstream& operator=(basic_ifstream&& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Odwołanie rvalue do `basic_ifstream` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość **`*this`** .

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zastępuje zawartość obiektu przy użyciu zawartości *Right*, traktowanej jako odwołanie rvalue. Aby uzyskać więcej informacji, zobacz [lvalues i rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md).

## <a name="basic_ifstreamrdbuf"></a><a name="rdbuf"></a>basic_ifstream:: rdbuf

Zwraca adres buforu zapisanego strumienia.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [basic_filebuf](../standard-library/basic-filebuf-class.md) reprezentujący przechowywany bufor strumienia.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf:: Close](../standard-library/basic-filebuf-class.md#close) , aby zapoznać się z przykładem, który używa `rdbuf` .

## <a name="basic_ifstreamswap"></a><a name="swap"></a>basic_ifstream:: swap

Wymienia zawartość dwóch `basic_ifstream` obiektów.

```cpp
void swap(basic_ifstream& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Odwołanie do innego buforu strumienia.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zamienia zawartość tego obiektu na zawartość z *prawej strony*.

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostreams](../standard-library/iostreams-conventions.md)
