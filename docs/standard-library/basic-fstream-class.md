---
title: basic_fstream — Klasa
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_fstream
- fstream/std::basic_fstream::close
- fstream/std::basic_fstream::is_open
- fstream/std::basic_fstream::open
- fstream/std::basic_fstream::rdbuf
- fstream/std::basic_fstream::swap
helpviewer_keywords:
- std::basic_fstream [C++]
- std::basic_fstream [C++], close
- std::basic_fstream [C++], is_open
- std::basic_fstream [C++], open
- std::basic_fstream [C++], rdbuf
- std::basic_fstream [C++], swap
ms.assetid: 8473817e-42a4-430b-82b8-b476c86bcf8a
ms.openlocfilehash: 8d26d0fe0e4e4152cf05476f546b753650209dfe
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459602"
---
# <a name="basic_fstream-class"></a>basic_fstream — Klasa

Opisuje obiekt, który kontroluje Wstawianie i wyodrębnianie elementów i zakodowanych obiektów przy użyciu bufora strumienia [](../standard-library/basic-filebuf-class.md)< klasy basic_filebuf `Tr``Elem`, >, z elementami typu `Elem`, których znak cechy są określane przez klasę `Tr`.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_fstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem*\
Podstawowy element buforu pliku.

*Zdawczy*\
Cechy podstawowego elementu buforu plików (zwykle `char_traits` <  `Elem`>).

## <a name="remarks"></a>Uwagi

`basic_filebuf`Obiekt przechowuje obiekt klasy <  `Elem`, >.`Tr`

> [!NOTE]
> Wskaźnik get i Put obiektu fstream — **nie** są od siebie niezależne. Jeśli wskaźnik Get zostanie przesunięty, w związku z tym robi wskaźnik Put.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak utworzyć `basic_fstream` obiekt, który może być odczytywany i zapisywana.

```cpp
// basic_fstream_class.cpp
// compile with: /EHsc

#include <fstream>
#include <iostream>

using namespace std;

int main(int argc, char **argv)
{
    fstream fs("fstream.txt", ios::in | ios::out | ios::trunc);
    if (!fs.bad())
    {
        // Write to the file.
        fs << "Writing to a basic_fstream object..." << endl;
        fs.close();

        // Dump the contents of the file to cout.
        fs.open("fstream.txt", ios::in);
        cout << fs.rdbuf();
        fs.close();
    }
}
```

```Output
Writing to a basic_fstream object...
```

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_fstream](#basic_fstream)|Konstruuje obiekt typu `basic_fstream`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[close](#close)|Zamyka plik.|
|[is_open](#is_open)|Określa, czy plik jest otwarty.|
|[open](#open)|Otwiera plik.|
|[rdbuf](#rdbuf)|Zwraca adres przechowywanego bufora strumienia, typu wskaźnika do [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>.|
|[swap](#swap)|Wymienia zawartość tego obiektu z zawartością innego `basic_fstream` obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<fstream — >

**Przestrzeń nazw:** std

## <a name="basic_fstream"></a>basic_fstream::basic_fstream

Konstruuje obiekt typu `basic_fstream`.

```cpp
basic_fstream();

explicit basic_fstream(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

explicit basic_fstream(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

basic_fstream(basic_fstream&& right);
```

### <a name="parameters"></a>Parametry

*_Filename*\
Nazwa pliku do otwarcia.

*_Mode*\
Jedno z wyliczeń w [ios_base:: openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Domyślna ochrona otwierania plików, równoważna parametrowi *Shflag* w [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje klasę bazową przez wywołanie [basic_iostream](../standard-library/basic-iostream-class.md)(`sb` `sb` ), gdzie jest przechowywany obiekt klasy [basic_filebuf](../standard-library/basic-filebuf-class.md) \< **elem**, **TR**>. Jest on również `sb` inicjowany `basic_filebuf` przez \< wywołanie **elem**, **TR**>.

Drugi i trzeci Konstruktor inicjuje klasę bazową przez wywołanie `basic_iostream`( **SB**). Jest on również `sb` inicjowany `basic_filebuf` przez wywołanie \< **elem**, **TR**>, a następnie **SB.** [Open](../standard-library/basic-filebuf-class.md#open)(_ `_Mode` *filename*,). Jeśli druga funkcja zwraca wskaźnik o wartości null, Konstruktor wywołuje metodę [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`).

Czwarty Konstruktor inicjuje obiekt z zawartością `right`, traktowany jako odwołanie rvalue.

### <a name="example"></a>Przykład

Zobacz [streampos](../standard-library/ios-typedefs.md#streampos) , aby uzyskać przykład, `basic_fstream`który używa programu.

## <a name="close"></a>basic_fstream:: Close

Zamyka plik.

```cpp
void close();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska wywołuje [rdbuf](#rdbuf) **->** [Close](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf:: Close](../standard-library/basic-filebuf-class.md#close) , aby zapoznać się z przykładem `close`użycia.

## <a name="is_open"></a>basic_fstream::is_open

Określa, czy plik jest otwarty.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli plik jest otwarty; w przeciwnym razie **zwraca wartość false** .

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf:: is_open](../standard-library/basic-filebuf-class.md#is_open) , aby zapoznać się z przykładem `is_open`sposobu korzystania z programu.

## <a name="open"></a>basic_fstream:: Open

Otwiera plik.

```cpp
void open(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
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
Domyślna ochrona otwierania plików, równoważna parametrowi *Shflag* w [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Uwagi

Funkcja członkowska wywołuje [rdbuf](#rdbuf) **->** [Open](../standard-library/basic-filebuf-class.md#open)(_ *filename*, `_Mode`). Jeśli ta funkcja zwróci wskaźnik o wartości null, funkcja wywołuje [](../standard-library/basic-ios-class.md#setstate)metodę setstate `failbit`().

### <a name="example"></a>Przykład

Zobacz [basic_filebuf:: Open](../standard-library/basic-filebuf-class.md#open) , aby zapoznać się z przykładem `open`użycia.

## <a name="op_eq"></a>basic_fstream:: operator =

Przypisuje do tego obiektu zawartość z określonego obiektu strumienia. Jest to przypisanie przenoszenia, które obejmuje rvalue, które nie pozostawia kopii w tle.

```cpp
basic_fstream& operator=(basic_fstream&& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Odwołanie lvalue do `basic_fstream` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca `*this`wartość.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zastępuje zawartość obiektu przy użyciu zawartości *Right*, traktowanej jako odwołanie rvalue.

## <a name="rdbuf"></a>basic_fstream:: rdbuf

Zwraca adres przechowywanego bufora strumienia, typu wskaźnika do [basic_filebuf](../standard-library/basic-filebuf-class.md) \< **elem**, **TR**>.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Wartość zwracana

Adres buforu przechowywanego strumienia.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf:: Close](../standard-library/basic-filebuf-class.md#close) , aby zapoznać się z przykładem `rdbuf`użycia.

## <a name="swap"></a>basic_fstream:: swap

Wymienia zawartość dwóch `basic_fstream` obiektów.

```cpp
void swap(basic_fstream& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
`lvalue` Odwołanie`basic_fstream` do obiektu.

### <a name="remarks"></a>Uwagi

Funkcja członkowska wymienia zawartość tego obiektu i jego *zawartość.*

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
