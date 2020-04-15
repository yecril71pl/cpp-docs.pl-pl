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
ms.openlocfilehash: 85a315ee393a002da4d0999569d4af6c34a37ee3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376846"
---
# <a name="basic_ifstream-class"></a>basic_ifstream — Klasa

Opisuje obiekt, który steruje wyodrębnianiem elementów i [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`zakodowanych `Tr` obiektów z buforu strumienia klasy basic_filebuf ,>, z elementami typu `Elem`, których cechy charakteru są określane przez klasę `Tr`.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ifstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem*\
Podstawowy element buforu plików.

*Tr*\
Cechy podstawowego elementu buforu plików (zwykle `char_traits` <  `Elem`>).

## <a name="remarks"></a>Uwagi

Obiekt przechowuje obiekt `basic_filebuf` <  `Elem`klasy `Tr` ,>.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak czytać w tekście z pliku.

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

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_ifstream](#basic_ifstream)|Inicjuje nowe wystąpienie `basic_ifstream` obiektu.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Zamknij](#close)|Zamyka plik.|
|[is_open](#is_open)|Określa, czy plik jest otwarty.|
|[Otwórz](#open)|Otwiera plik.|
|[Rdbuf](#rdbuf)|Zwraca adres buforu przechowywanego strumienia.|
|[Wymiany](#swap)|Wymienia się jego `basic_ifstream` treścią na `basic_ifstream`treść.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Przypisuje zawartość tego obiektu strumienia. Jest to przypisanie przenoszenia obejmujące, `rvalue` który nie pozostawia kopię za sobą.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<fstream>

**Przestrzeń nazw:** std

## <a name="basic_ifstreambasic_ifstream"></a><a name="basic_ifstream"></a>basic_ifstream::basic_ifstream

Konstruuje obiekt `basic_ifstream`typu .

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

*_mode*\
Jedno z wyliczenia w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Domyślna ochrona przed otwarciem `shflag` pliku, równoważna parametrowi [w _fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor inicjuje klasę [basic_istream](../standard-library/basic-istream-class.md)podstawową, `sb`wywołując `sb` basic_istream ( ), gdzie jest przechowywanym obiektem [klasy basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`>. `Tr` Inicjuje `sb` również, `basic_filebuf` <  `Elem` `Tr` wywołując>.

Drugi i trzeci konstruktorzy inicjuje klasę podstawową przez wywołanie `basic_istream`( `sb`). Inicjuje `sb` również, wywołując [basic_filebuf](../standard-library/basic-filebuf-class.md#basic_filebuf)< `Elem`, `Tr`>, `sb`a następnie . [open](../standard-library/basic-filebuf-class.md#open) `_Filename`( `_Mode` , &#124; `ios_base::in`). Jeśli ta ostatnia funkcja zwraca wskaźnik zerowy, `failbit`konstruktor wywołuje **setstate**( ).

Czwarty konstruktor inicjuje obiekt `right`z zawartością , traktowane jako odwołanie rvalue.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak czytać w tekście z pliku. Aby utworzyć plik, zobacz przykład [basic_ofstream::basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream).

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

## <a name="basic_ifstreamclose"></a><a name="close"></a>basic_ifstream::zamknij

Zamyka plik.

```cpp
void close();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego wywołuje [rdbuf](#rdbuf) **->** [close](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) na przykład, który `close`używa .

## <a name="basic_ifstreamis_open"></a><a name="is_open"></a>basic_ifstream::is_open

Określa, czy plik jest otwarty.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli plik jest otwarty, **false** inaczej.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::is_open](../standard-library/basic-filebuf-class.md#is_open) na przykład, który używa `is_open`.

## <a name="basic_ifstreamopen"></a><a name="open"></a>basic_ifstream::otwórz

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

*_mode*\
Jedno z wyliczenia w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Domyślna ochrona przed otwarciem `shflag` pliku, równoważna parametrowi [w _fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego wywołuje [rdbuf](#rdbuf) **->** [open](../standard-library/basic-filebuf-class.md#open)(_ *Nazwa pliku*, `_Mode` &#124; **ios_base::in**). Jeśli open nie powiedzie się, funkcja wywołuje [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`), który może zgłosić wyjątek ios_base::failure.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::otwórz](../standard-library/basic-filebuf-class.md#open) na przykład, który `open`używa .

## <a name="basic_ifstreamoperator"></a><a name="op_eq"></a>basic_ifstream::operator=

Przypisuje zawartość tego obiektu strumienia. Jest to przypisanie przenoszenia obejmujące wartość r, która nie pozostawia kopii za sobą.

```cpp
basic_ifstream& operator=(basic_ifstream&& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Odwołanie do `basic_ifstream` wartości r. do obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość `*this`.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zastępuje zawartość obiektu przy użyciu zawartości *prawa,* traktowane jako odwołanie rvalue. Aby uzyskać więcej informacji, zobacz [Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md).

## <a name="basic_ifstreamrdbuf"></a><a name="rdbuf"></a>basic_ifstream::rdbuf

Zwraca adres buforu przechowywanego strumienia.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [obiektu basic_filebuf](../standard-library/basic-filebuf-class.md) reprezentującego bufor strumienia przechowywanego.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) na przykład, który `rdbuf`używa .

## <a name="basic_ifstreamswap"></a><a name="swap"></a>basic_ifstream::swap

Wymienia zawartość dwóch `basic_ifstream` obiektów.

```cpp
void swap(basic_ifstream& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Odwołanie do innego buforu strumienia.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego wymienia zawartość tego obiektu na zawartość *prawego*.

## <a name="see-also"></a>Zobacz też

[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
