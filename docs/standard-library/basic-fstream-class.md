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
ms.openlocfilehash: 894ac0bf7703bf68c9125d11023dbc32cfbb5941
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400674"
---
# <a name="basicfstream-class"></a>basic_fstream — Klasa

Opisuje obiekt, który kontroluje wstawienia i wydobycia elementów i obiektów zakodowanych przy użyciu bufor strumienia klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, z elementami typu `Elem`, którego cech są określane przez klasę `Tr`.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_fstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem*<br/>
Podstawowy element buforu plików.

*TR*<br/>
Cechy elementu podstawowego buforu pliku (zazwyczaj `char_traits` <  `Elem`>).

## <a name="remarks"></a>Uwagi

Obiekt przechowuje obiekt klasy `basic_filebuf` <  `Elem`, `Tr`>.

> [!NOTE]
> Wskaźnik get i put wskaźnika obiektu fstream — **nie** od siebie niezależne. Jeśli get wskaźnik myszy jest przesuwany, więc nie umieść wskaźnik myszy.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia sposób tworzenia `basic_fstream` obiekt, który może odczytywać i zapisane.

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

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[close](#close)|Zamyka plik.|
|[is_open](#is_open)|Określa, czy plik jest otwarty.|
|[open](#open)|Otwiera plik.|
|[rdbuf](#rdbuf)|Zwraca adres bufor strumienia przechowywane, typu wskaźnika do [basic_filebuf —](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>.|
|[swap](#swap)|Wymienia zawartość tego obiektu z zawartością innego `basic_fstream` obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<fstream — >

**Namespace:** standardowe

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

*Nazwa p_liku*<br/>
Nazwa pliku, aby otworzyć.

*_Tryb*<br/>
Jedno z wyliczeń w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*<br/>
Domyślny plik otwarcie ochrony odpowiednikiem *shflag* parametru w [_fsopen —, _wfsopen —](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje klasę bazową, wywołując [basic_iostream —](../standard-library/basic-iostream-class.md)(`sb`), gdzie `sb` jest przechowywany obiekt klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md) \< **Elem**, **Tr**>. Inicjuje również `sb` przez wywołanie metody `basic_filebuf` \< **Elem**, **Tr**>.

Drugi i trzeci Konstruktor inicjuje klasę bazową, wywołując `basic_iostream`( **sb**). Inicjuje również `sb` przez wywołanie metody `basic_filebuf` \< **Elem**, **Tr**>, a następnie **sb.**[Otwórz](../standard-library/basic-filebuf-class.md#open)() _ *Filename*, `_Mode`). Jeśli ostatnie funkcja zwraca pusty wskaźnik, wywołuje konstruktor [setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`).

Czwarty Konstruktor inicjuje obiekt z zawartością `right`, traktowane jako odwołanie rvalue.

### <a name="example"></a>Przykład

Zobacz [streampos](../standard-library/ios-typedefs.md#streampos) przykład, który używa `basic_fstream`.

## <a name="close"></a>  basic_fstream::Close

Zamyka plik.

```cpp
void close();
```

### <a name="remarks"></a>Uwagi

Wywołania funkcji elementu członkowskiego [rdbuf —](#rdbuf) **->** [Zamknij](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) przykład sposobu użycia `close`.

## <a name="is_open"></a>  basic_fstream::is_open

Określa, czy plik jest otwarty.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli plik jest otwarty, **false** inaczej.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [rdbuf —](#rdbuf)**->**[is_open —](../standard-library/basic-filebuf-class.md#is_open).

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

*Nazwa p_liku*<br/>
Nazwa pliku, aby otworzyć.

*_Tryb*<br/>
Jedno z wyliczeń w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*<br/>
Domyślny plik otwarcie ochrony odpowiednikiem *shflag* parametru w [_fsopen —, _wfsopen —](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Uwagi

Wywołania funkcji elementu członkowskiego [rdbuf —](#rdbuf) **->** [Otwórz](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, `_Mode`). Jeśli ta funkcja zwraca wskaźnikiem typu null, funkcja wywołuje [setstate](../standard-library/basic-ios-class.md#setstate)( `failbit`).

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::open](../standard-library/basic-filebuf-class.md#open) przykład sposobu użycia `open`.

## <a name="op_eq"></a>  basic_fstream::operator =

Przypisuje ten obiekt zawartości z obiektu określonego strumienia. Jest to przeniesienia przypisania, która obejmuje rvalue, który nie pozostawione kopię.

```cpp
basic_fstream& operator=(basic_fstream&& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Odwołania wartościowanego lewostronnie do `basic_fstream` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca `*this`.

### <a name="remarks"></a>Uwagi

Operator składowy zastępuje zawartość obiektu przy użyciu zawartości *prawo*, traktowane jako odwołanie rvalue.

## <a name="rdbuf"></a>  basic_fstream::rdbuf

Zwraca adres bufor strumienia przechowywane, typu wskaźnika do [basic_filebuf —](../standard-library/basic-filebuf-class.md) \< **Elem**, **Tr**>.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Wartość zwracana

Adres buforu strumienia przechowywanych.

### <a name="example"></a>Przykład

Zobacz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) przykład sposobu użycia `rdbuf`.

## <a name="swap"></a>  basic_fstream::swap

Zamienia zawartości dwóch `basic_fstream` obiektów.

```cpp
void swap(basic_fstream& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
`lvalue` Odwołanie do `basic_fstream` obiektu.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego wymienia zawartość tego obiektu i zawartość *prawo*.

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
