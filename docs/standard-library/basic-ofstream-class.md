---
title: basic_ofstream — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- fstream/std::basic_ofstream
- fstream/std::basic_ofstream::close
- fstream/std::basic_ofstream::is_open
- fstream/std::basic_ofstream::open
- fstream/std::basic_ofstream::rdbuf
- fstream/std::basic_ofstream::swap
dev_langs:
- C++
helpviewer_keywords:
- std::basic_ofstream [C++]
- std::basic_ofstream [C++], close
- std::basic_ofstream [C++], is_open
- std::basic_ofstream [C++], open
- std::basic_ofstream [C++], rdbuf
- std::basic_ofstream [C++], swap
ms.assetid: 3bcc9c51-6dfc-4844-8fcc-22ef57c9dff1
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f523d8471b2cdb1736e57dbc8b0d101574c42abc
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="basicofstream-class"></a>basic_ofstream — Klasa

Opis obiektu, który kontroluje wstawiania elementów i obiektów zakodowanych do buforu strumienia klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, elementami typu `Elem`, którego znak cechy są określane przez klasę `Tr`.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ofstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

`Elem` Podstawowy element buforu plików.

`Tr` Cechy podstawowy element pliku buforu (zazwyczaj `char_traits` <  `Elem`>).

## <a name="remarks"></a>Uwagi

Gdy `wchar_t` specjalizacja `basic_ofstream` zapisuje dane w pliku, jeśli plik jest otwarty w trybie tekstowym zapisze sekwencji MBCS. Reprezentacji wewnętrznej użyje bufor `wchar_t` znaków.

Obiekt przechowuje obiekt klasy `basic_filebuf` <  `Elem`, `Tr`>.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia sposób tworzenia `basic_ofstream` obiektu i zapisanie w nim tekst.

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

|Funkcja członkowska|Opis|
|-|-|
|[close](#close)|Zamyka plik.|
|[is_open](#is_open)|Określa, czy plik jest otwarty.|
|[open](#open)|Otwiera plik.|
|[rdbuf](#rdbuf)|Zwraca adres buforu przechowywanych strumienia.|
|[swap](#swap)|Wymiana zawartość tych `basic_ofstream` dla zawartości określonego `basic_ofstream`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Przypisuje zawartości tego obiektu strumienia. Jest to dotyczące przypisania przenoszenia `rvalue reference` który nie pozostawione kopii.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<fstream — >

**Namespace:** Standard

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

`_Filename` Nazwa pliku, aby otworzyć.

`_Mode` Jedno z wyliczeń w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

`_Prot` Domyślny plik otwierania ochrony odpowiednikiem `shflag` parametru w [_fsopen —, _wfsopen —](../c-runtime-library/reference/fsopen-wfsopen.md).

`right` Odwołania wartościowane prawostronnie do `basic_ofstream` obiekt używany do inicjowania to `basic_ofstream` obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje klasy podstawowej, przez wywołanie metody [basic_ostream —](../standard-library/basic-ostream-class.md)( **sb**), gdzie **sb** jest przechowywane obiekt klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md) <  `Elem`, `Tr`>. Inicjuje również **sb** przez wywołanie metody `basic_filebuf` <  `Elem`, `Tr`>.

Konstruktory drugiego i trzeciego inicjuje klasy podstawowej, przez wywołanie metody `basic_ostream`( **sb**). Inicjuje również **sb** przez wywołanie metody `basic_filebuf` <  `Elem`, `Tr`>, a następnie **sb**. [Otwórz](../standard-library/basic-filebuf-class.md#open)( `_Filename`, `_Mode` &#124; `ios_base::out`). Jeśli funkcja ostatnie zwraca wskaźnika o wartości null, Konstruktor wywołuje [metoda setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**).

Konstruktor czwarty jest funkcji kopiowania. Inicjuje go do obiektu o zawartość `right`, traktowane jako odwołanie do r-wartości.

### <a name="example"></a>Przykład

Poniższy przykład przedstawia sposób tworzenia `basic_ofstream` obiektu i zapisanie w nim tekst.

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

Wywołania funkcji Członkowskich [rdbuf](../standard-library/basic-ifstream-class.md#rdbuf)**->**[zamknąć](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) na przykład, który używa **zamknąć**.

## <a name="is_open"></a>  basic_ofstream::is_open

Wskazuje, czy plik jest otwarty.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli plik jest otwarty, `false` inaczej.

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

`_Filename` Nazwa pliku, aby otworzyć.

`_Mode` Jedno z wyliczeń w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

`_Prot` Domyślny plik otwierania ochrony odpowiednikiem `shflag` parametru w [_fsopen —, _wfsopen —](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Uwagi

Wywołania funkcji Członkowskich [rdbuf](#rdbuf) **->** [Otwórz](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, `_Mode` &#124; `ios_base::out` ). Jeśli ta funkcja zwróci wartość wskaźnika o wartości null, funkcja wywołuje [metoda setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::open](../standard-library/basic-filebuf-class.md#open) na przykład, który używa **Otwórz**.

## <a name="op_eq"></a>  basic_ofstream::operator =

Przypisuje zawartości tego obiektu strumienia. Jest to dotyczące przypisania przenoszenia `rvalue reference` który nie pozostawione kopii.

```cpp
basic_ofstream& operator=(basic_ofstream&& right);
```

### <a name="parameters"></a>Parametry

`right` Odwołania do r-wartości do `basic_ofstream` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca `*this`.

### <a name="remarks"></a>Uwagi

Operator członkowski zastępuje zawartość obiektu przy użyciu zawartości `right`, traktowane jako odwołanie do r-wartości.

## <a name="rdbuf"></a>  basic_ofstream::rdbuf

Zwraca adres buforu przechowywanych strumienia.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Wartość zwracana

Zwraca adres buforu przechowywanych strumienia.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) na przykład, który używa `rdbuf`.

## <a name="swap"></a>  basic_ofstream::swap

Zamienia zawartość dwóch `basic_ofstream` obiektów.

```cpp
void swap(basic_ofstream& right);
```

### <a name="parameters"></a>Parametry

`right` `lvalue` Odwoływać się do innego `basic_ofstream` obiektu.

### <a name="remarks"></a>Uwagi

Funkcja członkowska wymiany zawartość obiektu zawartość `right`.

## <a name="see-also"></a>Zobacz także

[basic_ostream, klasa](../standard-library/basic-ostream-class.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
