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
ms.openlocfilehash: 30ae1e6384b3861bc4324d42f095516f80dce6e4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400685"
---
# <a name="basicifstream-class"></a>basic_ifstream — Klasa

Opisuje obiekt, który kontroluje wyodrębniania elementów i zakodowany obiektów z bufor strumienia klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, z elementami typu `Elem`, którego cechy znaków są określane przez klasę `Tr`.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ifstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem*<br/>
Podstawowy element buforu plików.

*TR*<br/>
Cechy elementu podstawowego buforu pliku (zazwyczaj `char_traits` <  `Elem`>).

## <a name="remarks"></a>Uwagi

Obiekt przechowuje obiekt klasy `basic_filebuf` <  `Elem`, `Tr`>.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia sposób odczytywania tekstu z pliku.

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

## <a name="input-basicifstreamclasstxt"></a>Dane wejściowe: basic_ifstream_class.txt

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
|[basic_ifstream](#basic_ifstream)|Inicjuje nowe wystąpienie klasy `basic_ifstream` obiektu.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[close](#close)|Zamyka plik.|
|[is_open](#is_open)|Określa, czy plik jest otwarty.|
|[open](#open)|Otwiera plik.|
|[rdbuf](#rdbuf)|Zwraca adres buforu strumienia przechowywanych.|
|[swap](#swap)|Wymienia zawartość tego `basic_ifstream` zawartości dotyczącej dostępnego `basic_ifstream`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Przypisuje zawartość tego obiektu strumienia. Jest to przeniesienia przypisania obejmujące `rvalue` , nie pozostawione kopię.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<fstream — >

**Namespace:** standardowe

## <a name="basic_ifstream"></a>  basic_ifstream::basic_ifstream

Tworzy obiekt typu `basic_ifstream`.

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

*Nazwa p_liku*<br/>
Nazwa pliku, aby otworzyć.

*_Tryb*<br/>
Jedno z wyliczeń w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*<br/>
Domyślny plik otwarcie ochrony odpowiednikiem `shflag` parametru w [_fsopen —, _wfsopen —](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje klasę bazową, wywołując [basic_istream](../standard-library/basic-istream-class.md)( `sb`), gdzie `sb` jest przechowywany obiekt klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md) <  `Elem`, `Tr`>. Inicjuje również `sb` przez wywołanie metody `basic_filebuf` <  `Elem`, `Tr`>.

Drugi i trzeci Konstruktor inicjuje klasę bazową, wywołując `basic_istream`( `sb`). Inicjuje również `sb` przez wywołanie metody [basic_filebuf —](../standard-library/basic-filebuf-class.md#basic_filebuf)< `Elem`, `Tr`>, następnie `sb`. [open](../standard-library/basic-filebuf-class.md#open)( `_Filename`, `_Mode` &#124; `ios_base::in`). Jeśli ostatnie funkcja zwraca pusty wskaźnik, wywołuje konstruktor **setstate**( `failbit`).

Czwarty Konstruktor inicjuje obiekt z zawartością `right`, traktowane jako odwołanie rvalue.

### <a name="example"></a>Przykład

Poniższy przykład przedstawia sposób odczytywania tekstu z pliku. Aby utworzyć plik, zobacz przykład [basic_ofstream::basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream).

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

## <a name="close"></a>  basic_ifstream::Close

Zamyka plik.

```cpp
void close();
```

### <a name="remarks"></a>Uwagi

Wywołania funkcji elementu członkowskiego [rdbuf —](#rdbuf) **->** [Zamknij](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) przykład, który używa `close`.

## <a name="is_open"></a>  basic_ifstream::is_open

Określa, czy plik jest otwarty.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli plik jest otwarty, **false** inaczej.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [rdbuf —](#rdbuf) **->** [is_open —](../standard-library/basic-filebuf-class.md#is_open).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::is_open](../standard-library/basic-filebuf-class.md#is_open) przykład, który używa `is_open`.

## <a name="open"></a>  basic_ifstream::Open

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

*Nazwa p_liku*<br/>
Nazwa pliku, aby otworzyć.

*_Tryb*<br/>
Jedno z wyliczeń w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*<br/>
Domyślny plik otwarcie ochrony odpowiednikiem `shflag` parametru w [_fsopen —, _wfsopen —](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Uwagi

Wywołania funkcji elementu członkowskiego [rdbuf —](#rdbuf) **->** [Otwórz](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, `_Mode` &#124;  **ios_base::in**). Jeśli open zakończy się niepowodzeniem, wywołania funkcji [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`), które mogą zgłosić wyjątek ios_base::failure.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::open](../standard-library/basic-filebuf-class.md#open) przykład, który używa `open`.

## <a name="op_eq"></a>  basic_ifstream::operator =

Przypisuje zawartość tego obiektu strumienia. Jest to przeniesienia przypisania obejmujące rvalue, który nie pozostawione kopię.

```cpp
basic_ifstream& operator=(basic_ifstream&& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Odwołania rvalue do `basic_ifstream` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca `*this`.

### <a name="remarks"></a>Uwagi

Operator składowy zastępuje zawartość obiektu przy użyciu zawartości *prawo*, traktowane jako odwołanie rvalue. Aby uzyskać więcej informacji, zobacz [Lvalues i Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md).

## <a name="rdbuf"></a>  basic_ifstream::rdbuf

Zwraca adres buforu strumienia przechowywanych.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [basic_filebuf —](../standard-library/basic-filebuf-class.md) obiekt reprezentujący bufor strumienia przechowywanych.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) przykład, który używa `rdbuf`.

## <a name="swap"></a>  basic_ifstream::swap

Zamienia zawartości dwóch `basic_ifstream` obiektów.

```cpp
void swap(basic_ifstream& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Odwołanie do innego buforu strumienia.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego wymienia zawartość tego obiektu, dla zawartości *prawo*.

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
