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
ms.openlocfilehash: a2b62b85953a5f4ec829053c8af93582eec76618
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219303"
---
# <a name="basic_fstream-class"></a>basic_fstream — Klasa

Opisuje obiekt, który kontroluje Wstawianie i wyodrębnianie elementów i zakodowanych obiektów przy użyciu bufora strumienia klasy [basic_filebuf](../standard-library/basic-filebuf-class.md) <  `Elem` , `Tr`>, z elementami typu `Elem` , których cechy znaku są określane przez klasę `Tr` .

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

Obiekt przechowuje obiekt klasy `basic_filebuf` <  `Elem` , `Tr`>.

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

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[basic_fstream](#basic_fstream)|Konstruuje obiekt typu `basic_fstream` .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[ściśle](#close)|Zamyka plik.|
|[is_open](#is_open)|Określa, czy plik jest otwarty.|
|[Otwórz](#open)|Otwiera plik.|
|[rdbuf](#rdbuf)|Zwraca adres buforu zapisanego strumienia, typu wskaźnika do [basic_filebuf](../standard-library/basic-filebuf-class.md) <  `Elem` , `Tr`>.|
|[wymiany](#swap)|Wymienia zawartość tego obiektu z zawartością innego `basic_fstream` obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<fstream>

**Przestrzeń nazw:** std

## <a name="basic_fstreambasic_fstream"></a><a name="basic_fstream"></a>basic_fstream:: basic_fstream

Konstruuje obiekt typu `basic_fstream` .

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

Pierwszy Konstruktor inicjuje klasę bazową, wywołując [basic_iostream](../standard-library/basic-iostream-class.md)( `sb` ), gdzie `sb` jest przechowywany obiekt klasy [basic_filebuf](../standard-library/basic-filebuf-class.md) \< **Elem**, **Tr**> . Inicjuje się to również `sb` przez wywołanie metody `basic_filebuf` \< **Elem**, **Tr**> .

Drugi i trzeci Konstruktor inicjuje klasę bazową przez wywołanie `basic_iostream` ( **SB**). Inicjuje również `sb` wywołanie metody `basic_filebuf` \< **Elem**, **Tr**> , a następnie plik **SB.**[Open](../standard-library/basic-filebuf-class.md#open)(_ *filename*, `_Mode` ). Jeśli druga funkcja zwraca wskaźnik o wartości null, Konstruktor wywołuje metodę [setstate](../standard-library/basic-ios-class.md#setstate)( `failbit` ).

Czwarty Konstruktor inicjuje obiekt z zawartością `right` , traktowany jako odwołanie rvalue.

### <a name="example"></a>Przykład

Zobacz [streampos](../standard-library/ios-typedefs.md#streampos) , aby uzyskać przykład, który używa programu `basic_fstream` .

## <a name="basic_fstreamclose"></a><a name="close"></a>basic_fstream:: Close

Zamyka plik.

```cpp
void close();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska wywołuje [rdbuf](#rdbuf) **->** [Close](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf:: Close](../standard-library/basic-filebuf-class.md#close) , aby zapoznać się z przykładem sposobu korzystania z programu `close` .

## <a name="basic_fstreamis_open"></a><a name="is_open"></a>basic_fstream:: is_open

Określa, czy plik jest otwarty.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli plik jest otwarty, **`false`** w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf:: is_open](../standard-library/basic-filebuf-class.md#is_open) , aby zapoznać się z przykładem użycia programu `is_open` .

## <a name="basic_fstreamopen"></a><a name="open"></a>basic_fstream:: Open

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

Funkcja członkowska wywołuje [rdbuf](#rdbuf) **->** [Open](../standard-library/basic-filebuf-class.md#open)(_ *filename*, `_Mode` ). Jeśli ta funkcja zwróci wskaźnik o wartości null, funkcja wywołuje metodę [setstate](../standard-library/basic-ios-class.md#setstate)( `failbit` ).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf:: Open](../standard-library/basic-filebuf-class.md#open) , aby zapoznać się z przykładem użycia programu `open` .

## <a name="basic_fstreamoperator"></a><a name="op_eq"></a>basic_fstream:: operator =

Przypisuje do tego obiektu zawartość z określonego obiektu strumienia. Jest to przypisanie przenoszenia, które obejmuje rvalue, które nie pozostawia kopii w tle.

```cpp
basic_fstream& operator=(basic_fstream&& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Odwołanie lvalue do `basic_fstream` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość **`*this`** .

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zastępuje zawartość obiektu przy użyciu zawartości *Right*, traktowanej jako odwołanie rvalue.

## <a name="basic_fstreamrdbuf"></a><a name="rdbuf"></a>basic_fstream:: rdbuf

Zwraca adres buforu zapisanego strumienia, typu wskaźnika do [basic_filebuf](../standard-library/basic-filebuf-class.md) \< **Elem**, **Tr**> .

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Wartość zwracana

Adres buforu przechowywanego strumienia.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf:: Close](../standard-library/basic-filebuf-class.md#close) , aby zapoznać się z przykładem sposobu korzystania z programu `rdbuf` .

## <a name="basic_fstreamswap"></a><a name="swap"></a>basic_fstream:: swap

Wymienia zawartość dwóch `basic_fstream` obiektów.

```cpp
void swap(basic_fstream& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
`lvalue`Odwołanie do `basic_fstream` obiektu.

### <a name="remarks"></a>Uwagi

Funkcja członkowska wymienia zawartość tego obiektu *i jego zawartość.*

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostreams](../standard-library/iostreams-conventions.md)
