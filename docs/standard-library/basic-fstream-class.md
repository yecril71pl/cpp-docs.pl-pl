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
ms.openlocfilehash: 80992430d6bef6fc46106452dfaa44cc0ed9e71c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376860"
---
# <a name="basic_fstream-class"></a>basic_fstream — Klasa

W tym artykule opisano obiekt, który steruje wstawianiem i wyodrębnianiem `Tr` elementów i zakodowanych obiektów przy użyciu buforu strumienia klasy [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`,>, z elementami typu `Elem`, których cechy charakteru są określane przez klasę `Tr`.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_fstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem*\
Podstawowy element buforu plików.

*Tr*\
Cechy podstawowego elementu buforu plików (zwykle `char_traits` <  `Elem`>).

## <a name="remarks"></a>Uwagi

Obiekt przechowuje obiekt `basic_filebuf` <  `Elem`klasy `Tr` ,>.

> [!NOTE]
> Wskaźnik get i umieścić wskaźnik obiektu fstream **nie** są niezależne od siebie. Jeśli wskaźnik get zostanie przesunie się, podobnie jak wskaźnik put.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak utworzyć `basic_fstream` obiekt, który może być odczytywany i zapisywany do.

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
|[basic_fstream](#basic_fstream)|Konstruuje obiekt `basic_fstream`typu .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Zamknij](#close)|Zamyka plik.|
|[is_open](#is_open)|Określa, czy plik jest otwarty.|
|[Otwórz](#open)|Otwiera plik.|
|[Rdbuf](#rdbuf)|Zwraca adres buforu strumienia przechowywanego, wskaźnika typu [do basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>.|
|[Wymiany](#swap)|Wymienia zawartość tego obiektu z zawartością innego `basic_fstream` obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<fstream>

**Przestrzeń nazw:** std

## <a name="basic_fstreambasic_fstream"></a><a name="basic_fstream"></a>basic_fstream::basic_fstream

Konstruuje obiekt `basic_fstream`typu .

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

*_mode*\
Jedno z wyliczenia w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Domyślna ochrona przed otwarciem pliku, równoważna parametrowi *shflag* w [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor inicjuje klasę [basic_iostream](../standard-library/basic-iostream-class.md)podstawową,`sb`wywołując `sb` basic_iostream ( ), gdzie jest przechowywanym obiektem klasy [basic_filebuf](../standard-library/basic-filebuf-class.md) \< **Elem**, **Tr**>. Inicjuje `sb` również, `basic_filebuf` \< dzwoniąc do **Elem**, **Tr**>.

Drugi i trzeci konstruktorzy inicjuje klasę podstawową przez wywołanie `basic_iostream` **(sb**). `sb` Inicjuje również, `basic_filebuf` \< wywołując **Elem**, **Tr**>, a następnie **sb.**[open](../standard-library/basic-filebuf-class.md#open)(_ Nazwa *pliku*, `_Mode`). Jeśli ta ostatnia funkcja zwraca wskaźnik zerowy,`failbit`konstruktor wywołuje [setstate](../standard-library/basic-ios-class.md#setstate)( ).

Czwarty konstruktor inicjuje obiekt `right`z zawartością , traktowane jako odwołanie rvalue.

### <a name="example"></a>Przykład

Zobacz [streampos](../standard-library/ios-typedefs.md#streampos) na przykład, `basic_fstream`który używa .

## <a name="basic_fstreamclose"></a><a name="close"></a>basic_fstream::zamknij

Zamyka plik.

```cpp
void close();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego wywołuje [rdbuf](#rdbuf) **->** [close](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::close,](../standard-library/basic-filebuf-class.md#close) aby zapoznać się `close`z przykładem użycia .

## <a name="basic_fstreamis_open"></a><a name="is_open"></a>basic_fstream::is_open

Określa, czy plik jest otwarty.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli plik jest otwarty, **false** inaczej.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [rdbuf](#rdbuf)**->**[is_open](../standard-library/basic-filebuf-class.md#is_open).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::is_open](../standard-library/basic-filebuf-class.md#is_open) na przykład, jak używać `is_open`.

## <a name="basic_fstreamopen"></a><a name="open"></a>basic_fstream::otwórz

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

*_mode*\
Jedno z wyliczenia w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
Domyślna ochrona przed otwarciem pliku, równoważna parametrowi *shflag* w [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego wywołuje [rdbuf](#rdbuf) **->** [open](../standard-library/basic-filebuf-class.md#open)(_ *Nazwa pliku*, `_Mode`). Jeśli ta funkcja zwraca wskaźnik zerowy, `failbit`funkcja wywołuje [setstate](../standard-library/basic-ios-class.md#setstate)( ).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::otwórz,](../standard-library/basic-filebuf-class.md#open) aby uzyskać przykład użycia `open`.

## <a name="basic_fstreamoperator"></a><a name="op_eq"></a>basic_fstream::operator=

Przypisuje do tego obiektu zawartość z określonego obiektu strumienia. Jest to przypisanie przenoszenia, które obejmuje wartość rvalue, która nie pozostawia kopii za.

```cpp
basic_fstream& operator=(basic_fstream&& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Odwołanie lvalue do `basic_fstream` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość `*this`.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zastępuje zawartość obiektu przy użyciu zawartości *prawa,* traktowane jako odwołanie rvalue.

## <a name="basic_fstreamrdbuf"></a><a name="rdbuf"></a>basic_fstream::rdbuf

Zwraca adres przechowywanego buforu strumienia, wskaźnika typu [basic_filebuf](../standard-library/basic-filebuf-class.md) \< **Elem**, **Tr**>.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Wartość zwracana

Adres buforu przechowywanego strumienia.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::close,](../standard-library/basic-filebuf-class.md#close) aby zapoznać się `rdbuf`z przykładem użycia .

## <a name="basic_fstreamswap"></a><a name="swap"></a>basic_fstream::swap

Wymienia zawartość dwóch `basic_fstream` obiektów.

```cpp
void swap(basic_fstream& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Odwołanie `lvalue` do `basic_fstream` obiektu.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego wymienia zawartość tego obiektu i zawartość *praw*.

## <a name="see-also"></a>Zobacz też

[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
