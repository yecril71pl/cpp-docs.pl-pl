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
ms.openlocfilehash: 9a8255a02c46a4ade33bd95635516e5d36fe8e64
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409801"
---
# <a name="basicofstream-class"></a>basic_ofstream — Klasa

Opisuje obiekt, który kontroluje wstawiania elementów i obiektów zakodowanych do bufora strumienia, klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, z elementami typu `Elem`, którego cechy znaków są określane przez klasę `Tr`.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ofstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem*<br/>
Podstawowy element buforu plików.

*TR*<br/>
Cechy elementu podstawowego buforu pliku (zazwyczaj `char_traits` <  `Elem`>).

## <a name="remarks"></a>Uwagi

Gdy **wchar_t** specjalizacja `basic_ofstream` zapisuje do pliku, jeśli plik jest otwarty w trybie tekstowym zapisze sekwencji MBCS. Wewnętrznej reprezentacji użyje bufor `wchar_t` znaków.

Obiekt przechowuje obiekt klasy `basic_filebuf` <  `Elem`, `Tr`>.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak utworzyć `basic_ofstream` obiektu i wpisać tekst.

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

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[close](#close)|Zamyka plik.|
|[is_open](#is_open)|Określa, czy plik jest otwarty.|
|[open](#open)|Otwiera plik.|
|[rdbuf](#rdbuf)|Zwraca adres buforu strumienia przechowywanych.|
|[swap](#swap)|Wymiana zawartości to `basic_ofstream` dla zawartości dotyczącej dostępnego `basic_ofstream`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Przypisuje zawartość tego obiektu strumienia. Jest to przeniesienia przypisania obejmujące `rvalue reference` , nie pozostawione kopię.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<fstream — >

**Namespace:** standardowe

## <a name="basic_ofstream"></a>  basic_ofstream::basic_ofstream

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

*Nazwa p_liku*<br/>
Nazwa pliku, aby otworzyć.

*_Tryb*<br/>
Jedno z wyliczeń w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*<br/>
Domyślny plik otwarcie ochrony odpowiednikiem `shflag` parametru w [_fsopen —, _wfsopen —](../c-runtime-library/reference/fsopen-wfsopen.md).

*right*<br/>
Odwołania rvalue do `basic_ofstream` obiekt używany do zainicjowania tego `basic_ofstream` obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje klasę bazową, wywołując [basic_ostream](../standard-library/basic-ostream-class.md)(`sb`), gdzie `sb` jest przechowywany obiekt klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md) <  `Elem`, `Tr`>. Inicjuje również `sb` przez wywołanie metody `basic_filebuf` <  `Elem`, `Tr`>.

Drugi i trzeci Konstruktor inicjuje klasę bazową, wywołując `basic_ostream`( **sb**). Inicjuje również `sb` przez wywołanie metody `basic_filebuf` <  `Elem`, `Tr`> a następnie `sb`. [open](../standard-library/basic-filebuf-class.md#open)( `_Filename`, `_Mode` &#124; `ios_base::out`). Jeśli ostatnie funkcja zwraca pusty wskaźnik, wywołuje konstruktor [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`).

Czwarty Konstruktor jest funkcją kopiowania. Inicjuje obiekt z zawartością *prawo*, traktowane jako odwołanie rvalue.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak utworzyć `basic_ofstream` obiektu i wpisać tekst.

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

## <a name="close"></a>  basic_ofstream::Close

Zamyka plik.

```cpp
void close();
```

### <a name="remarks"></a>Uwagi

Wywołania funkcji elementu członkowskiego [rdbuf —](../standard-library/basic-ifstream-class.md#rdbuf)**->**[Zamknij](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) przykład, który używa `close`.

## <a name="is_open"></a>  basic_ofstream::is_open

Wskazuje, czy plik jest otwarty.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli plik jest otwarty, **false** inaczej.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [rdbuf —](#rdbuf) **->** [is_open —](../standard-library/basic-filebuf-class.md#is_open).

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

## <a name="open"></a>  basic_ofstream::Open

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

*Nazwa p_liku*<br/>
Nazwa pliku, aby otworzyć.

*_Tryb*<br/>
Jedno z wyliczeń w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*<br/>
Domyślny plik otwarcie ochrony odpowiednikiem `shflag` parametru w [_fsopen —, _wfsopen —](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Uwagi

Wywołania funkcji elementu członkowskiego [rdbuf —](#rdbuf) **->** [Otwórz](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, `_Mode` &#124; `ios_base::out` ). Jeśli ta funkcja zwraca wskaźnikiem typu null, funkcja wywołuje [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::open](../standard-library/basic-filebuf-class.md#open) przykład, który używa `open`.

## <a name="op_eq"></a>  basic_ofstream::operator =

Przypisuje zawartość tego obiektu strumienia. Jest to przeniesienia przypisania obejmujące `rvalue reference` , nie pozostawione kopię.

```cpp
basic_ofstream& operator=(basic_ofstream&& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Odwołania rvalue do `basic_ofstream` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca `*this`.

### <a name="remarks"></a>Uwagi

Operator składowy zastępuje zawartość obiektu przy użyciu zawartości *prawo*, traktowane jako odwołanie rvalue.

## <a name="rdbuf"></a>  basic_ofstream::rdbuf

Zwraca adres buforu strumienia przechowywanych.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Wartość zwracana

Zwraca adres buforu strumienia przechowywanych.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) przykład, który używa `rdbuf`.

## <a name="swap"></a>  basic_ofstream::swap

Zamienia zawartości dwóch `basic_ofstream` obiektów.

```cpp
void swap(basic_ofstream& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
`lvalue` Odwoływać się do innego `basic_ofstream` obiektu.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego wymienia zawartość tego obiektu, dla zawartości *prawo*.

## <a name="see-also"></a>Zobacz także

[basic_ostream, klasa](../standard-library/basic-ostream-class.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
