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
ms.openlocfilehash: 1e5e22c837ca2d6389591cec6d2cdd256ca50b1a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865872"
---
# <a name="basic_ifstream-class"></a>basic_ifstream — Klasa

Opisuje obiekt, który kontroluje wyodrębnianie elementów i zakodowanych obiektów z bufora strumienia klasy [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, z elementami typu `Elem`, których cechy znaku są określane przez klasę `Tr`.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ifstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem*\
Podstawowy element buforu pliku.

\ *TR*
Cechy podstawowego elementu buforu plików (zwykle `char_traits`< `Elem`>).

## <a name="remarks"></a>Uwagi

Obiekt przechowuje obiekt klasy `basic_filebuf`< `Elem`, `Tr`>.

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

## <a name="input-basic_ifstream_classtxt"></a>Dane wejściowe: basic_ifstream_class. txt

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
|[basic_ifstream](#basic_ifstream)|Inicjuje nowe wystąpienie obiektu `basic_ifstream`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[close](#close)|Zamyka plik.|
|[is_open](#is_open)|Określa, czy plik jest otwarty.|
|[open](#open)|Otwiera plik.|
|[rdbuf](#rdbuf)|Zwraca adres buforu zapisanego strumienia.|
|[wymiany](#swap)|Wymienia zawartość tego `basic_ifstream` dla zawartości podanej `basic_ifstream`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator =](#op_eq)|Przypisuje zawartość tego obiektu strumienia. Jest to przypisanie przenoszenia obejmujące `rvalue`, które nie pozostawia kopii w tle.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<fstream — >

**Przestrzeń nazw:** std

## <a name="basic_ifstream"></a>basic_ifstream:: basic_ifstream

Konstruuje obiekt typu `basic_ifstream`.

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
Domyślna ochrona otwierania plików, równoważna parametrowi `shflag` w [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje klasę bazową, wywołując [basic_istream](../standard-library/basic-istream-class.md)(`sb`), gdzie `sb` jest przechowywanym obiektem klasy [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>. Inicjuje również `sb` przez wywoływanie `basic_filebuf`< `Elem`, `Tr`>.

Drugi i trzeci konstruktory inicjuje klasę bazową, wywołując `basic_istream`(`sb`). Inicjuje również `sb` przez wywołanie [basic_filebuf](../standard-library/basic-filebuf-class.md#basic_filebuf)< `Elem`, `Tr`>, a następnie `sb`. [Otwórz](../standard-library/basic-filebuf-class.md#open)(`_Filename`, `_Mode` &#124; `ios_base::in`). Jeśli druga funkcja zwraca wskaźnik o wartości null, Konstruktor wywołuje metodę **setstate**(`failbit`).

Czwarty Konstruktor inicjuje obiekt z zawartością `right`, traktowany jako odwołanie rvalue.

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

## <a name="close"></a>basic_ifstream:: Close

Zamyka plik.

```cpp
void close();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska wywołuje [rdbuf](#rdbuf) **->** [Close](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf:: Close](../standard-library/basic-filebuf-class.md#close) , aby zapoznać się z przykładem korzystającym z `close`.

## <a name="is_open"></a>basic_ifstream:: is_open

Określa, czy plik jest otwarty.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli plik jest otwarty; w przeciwnym razie **zwraca wartość false** .

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf:: is_open](../standard-library/basic-filebuf-class.md#is_open) , aby uzyskać przykład, który używa `is_open`.

## <a name="open"></a>basic_ifstream:: Open

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
Domyślna ochrona otwierania plików, równoważna parametrowi `shflag` w [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Uwagi

Funkcja członkowska wywołuje [rdbuf](#rdbuf) **->** [Otwórz](../standard-library/basic-filebuf-class.md#open)(_ *filename*, `_Mode` &#124; **ios_base:: in**). Jeśli operacja otwierania nie powiedzie się, funkcja wywołuje metodę [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`), która może zgłosić wyjątek ios_base:: Failure.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf:: Open](../standard-library/basic-filebuf-class.md#open) , aby zapoznać się z przykładem korzystającym z `open`.

## <a name="op_eq"></a>basic_ifstream:: operator =

Przypisuje zawartość tego obiektu strumienia. Jest to przypisanie przenoszenia obejmujące rvalue, które nie pozostawia kopii w tle.

```cpp
basic_ifstream& operator=(basic_ifstream&& right);
```

### <a name="parameters"></a>Parametry

*prawa*\
Odwołanie rvalue do obiektu `basic_ifstream`.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość `*this`.

### <a name="remarks"></a>Uwagi

Operator elementu członkowskiego zastępuje zawartość obiektu przy użyciu zawartości *Right*, traktowanej jako odwołanie rvalue. Aby uzyskać więcej informacji, zobacz [lvalues i rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md).

## <a name="rdbuf"></a>basic_ifstream:: rdbuf

Zwraca adres buforu zapisanego strumienia.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [basic_filebuf](../standard-library/basic-filebuf-class.md) reprezentujący przechowywany bufor strumienia.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf:: Close](../standard-library/basic-filebuf-class.md#close) , aby zapoznać się z przykładem korzystającym z `rdbuf`.

## <a name="swap"></a>basic_ifstream:: swap

Wymienia zawartość dwóch `basic_ifstream` obiektów.

```cpp
void swap(basic_ifstream& right);
```

### <a name="parameters"></a>Parametry

*prawa*\
Odwołanie do innego buforu strumienia.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zamienia zawartość tego obiektu na zawartość z *prawej strony*.

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
\ [programowania iostream](../standard-library/iostream-programming.md)
[Konwencje iostream](../standard-library/iostreams-conventions.md)
