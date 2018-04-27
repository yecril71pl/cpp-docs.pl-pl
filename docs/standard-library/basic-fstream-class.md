---
title: basic_fstream — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- fstream/std::basic_fstream
- fstream/std::basic_fstream::close
- fstream/std::basic_fstream::is_open
- fstream/std::basic_fstream::open
- fstream/std::basic_fstream::rdbuf
- fstream/std::basic_fstream::swap
dev_langs:
- C++
helpviewer_keywords:
- std::basic_fstream [C++]
- std::basic_fstream [C++], close
- std::basic_fstream [C++], is_open
- std::basic_fstream [C++], open
- std::basic_fstream [C++], rdbuf
- std::basic_fstream [C++], swap
ms.assetid: 8473817e-42a4-430b-82b8-b476c86bcf8a
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9a0f1a9b62f7b64befdbd724da5b6bd5ad3d555c
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="basicfstream-class"></a>basic_fstream — Klasa

Zawiera opis obiektu, który kontroluje wstawiania i wyodrębniania elementów i obiektów zakodowany przy użyciu buforu strumienia klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, elementami typu `Elem`, których cech znaków są określane przez klasę `Tr`.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_fstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

`Elem` Podstawowy element buforu plików.

`Tr` Cechy podstawowy element pliku buforu (zazwyczaj `char_traits` <  `Elem`>).

## <a name="remarks"></a>Uwagi

Obiekt przechowuje obiekt klasy `basic_filebuf` <  `Elem`, `Tr`>.

> [!NOTE]
> Wskaźnik get i put wskaźnika obiektu fstream — **nie** od siebie niezależne. Jeśli get wskaźnik myszy przesuwa się, co powoduje umieść wskaźnik myszy.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak utworzyć `basic_fstream` obiektów, które mogą być odczytywane i zapisywane do.

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
|[basic_fstream](#basic_fstream)|Tworzy obiekt typu `basic_fstream`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[close](#close)|Zamyka plik.|
|[is_open](#is_open)|Określa, czy plik jest otwarty.|
|[open](#open)|Otwiera plik.|
|[rdbuf](#rdbuf)|Zwraca adres buforu przechowywanych strumienia, typu wskaźnika do [basic_filebuf —](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>.|
|[swap](#swap)|Zamienia zawartości tego obiektu z zawartością innego `basic_fstream` obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<fstream — >

**Namespace:** Standard

## <a name="basic_fstream"></a>  basic_fstream::basic_fstream

Tworzy obiekt typu `basic_fstream`.

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

`_Filename` Nazwa pliku, aby otworzyć.

`_Mode` Jedno z wyliczeń w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

`_Prot` Domyślny plik otwierania ochrony odpowiednikiem `shflag` parametru w [_fsopen —, _wfsopen —](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje klasy podstawowej, przez wywołanie metody [basic_iostream —](../standard-library/basic-iostream-class.md)( **sb**), gdzie **sb** jest przechowywane obiekt klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md) \< **Elementu**, **Tr**>. Inicjuje również **sb** przez wywołanie metody `basic_filebuf` \< **elementu**, **Tr**>.

Konstruktory drugiego i trzeciego inicjuje klasy podstawowej, przez wywołanie metody `basic_iostream`( **sb**). Inicjuje również **sb** przez wywołanie metody `basic_filebuf` \< **elementu**, **Tr**>, a następnie **sb.** [ Otwórz](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, `_Mode`). Jeśli funkcja ostatnie zwraca wskaźnika o wartości null, Konstruktor wywołuje [metoda setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**).

Czwarty Konstruktor inicjuje obiekt z zawartością `right`, traktowane jako odwołanie do r-wartości.

### <a name="example"></a>Przykład

Zobacz [streampos](../standard-library/ios-typedefs.md#streampos) na przykład, który używa `basic_fstream`.

## <a name="close"></a>  basic_fstream::Close

Zamyka plik.

```cpp
void close();
```

### <a name="remarks"></a>Uwagi

Wywołania funkcji Członkowskich [rdbuf](#rdbuf) **->** [zamknąć](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) przykład sposobu użycia **zamknąć**.

## <a name="is_open"></a>  basic_fstream::is_open

Określa, czy plik jest otwarty.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli plik jest otwarty, **false** inaczej.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [rdbuf](#rdbuf)**->**[is_open](../standard-library/basic-filebuf-class.md#is_open).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::is_open](../standard-library/basic-filebuf-class.md#is_open) przykład sposobu użycia `is_open`.

## <a name="open"></a>  basic_fstream::Open

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

`_Filename` Nazwa pliku, aby otworzyć.

`_Mode` Jedno z wyliczeń w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

`_Prot` Domyślny plik otwierania ochrony odpowiednikiem `shflag` parametru w [_fsopen —, _wfsopen —](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Uwagi

Wywołania funkcji Członkowskich [rdbuf](#rdbuf) **->** [Otwórz](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, `_Mode`). Jeśli ta funkcja zwróci wartość wskaźnika o wartości null, funkcja wywołuje [metoda setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::open](../standard-library/basic-filebuf-class.md#open) przykład sposobu użycia **Otwórz**.

## <a name="op_eq"></a>  basic_fstream::operator =

Przypisuje do tego obiektu zawartości z obiektu określonego strumienia. Jest to przypisania przenoszenia, która obejmuje r-wartości nie pozostawione kopii.

```cpp
basic_fstream& operator=(basic_fstream&& right);
```

### <a name="parameters"></a>Parametry

`right` Odwołania do wartości do `basic_fstream` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca `*this`.

### <a name="remarks"></a>Uwagi

Operator członkowski zastępuje zawartość obiektu przy użyciu zawartości `right`, traktowane jako odwołanie do r-wartości.

## <a name="rdbuf"></a>  basic_fstream::rdbuf

Zwraca adres buforu przechowywanych strumienia, typu wskaźnika do [basic_filebuf —](../standard-library/basic-filebuf-class.md) \< **elementu**, **Tr**>.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Wartość zwracana

Adres buforu przechowywanych strumienia.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) przykład sposobu użycia `rdbuf`.

## <a name="swap"></a>  basic_fstream::swap

Zamienia zawartość dwóch `basic_fstream` obiektów.

```cpp
void swap(basic_fstream& right);
```

### <a name="parameters"></a>Parametry

`right` `lvalue` Odwołanie do `basic_fstream` obiektu.

### <a name="remarks"></a>Uwagi

Funkcja członkowska wymiany zawartość tego obiektu i zawartość `right`.

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
