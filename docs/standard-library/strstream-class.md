---
title: strstream — Klasa
ms.date: 11/04/2016
f1_keywords:
- strstream/std::strstream::freeze
- strstream/std::strstream::pcount
- strstream/std::strstream::rdbuf
- strstream/std::strstream::str
helpviewer_keywords:
- std::strstream [C++], freeze
- std::strstream [C++], pcount
- std::strstream [C++], rdbuf
- std::strstream [C++], str
ms.assetid: 63f3be31-9e36-42b1-9715-a474a5997e2a
ms.openlocfilehash: 047b7e9d7fdece75137980b013d43abf1d5e3ec3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376618"
---
# <a name="strstream-class"></a>strstream — Klasa

W tym artykule opisano obiekt, który kontroluje wstawianie i wyodrębnianie elementów i zakodowanych obiektów przy użyciu buforu strumienia [klasy strstreambuf](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Składnia

```cpp
class strstream : public iostream
```

## <a name="remarks"></a>Uwagi

Obiekt przechowuje obiekt `strstreambuf`klasy .

> [!NOTE]
> Ta klasa jest przestarzała. Należy rozważyć użycie [stringstream](../standard-library/sstream-typedefs.md#stringstream) lub [wstringstream](../standard-library/sstream-typedefs.md#wstringstream) zamiast.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[strstream](#strstream)|Konstruuje obiekt `strstream`typu .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Zamrozić](#freeze)|Powoduje, że bufor strumienia jest niedostępny za pośrednictwem operacji buforu strumienia.|
|[pcount (liczba pcount)](#pcount)|Zwraca liczbę elementów zapisanych w kontrolowanej sekwencji.|
|[Rdbuf](#rdbuf)|Zwraca wskaźnik do skojarzonego z `strstreambuf` nim obiektu strumienia.|
|[Str](#str)|Wywołania [freeze](../standard-library/strstreambuf-class.md#freeze), a następnie zwraca wskaźnik na początku kontrolowanej sekwencji.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<strstream>

**Przestrzeń nazw:** std

## <a name="strstreamfreeze"></a><a name="freeze"></a>strstream::zamrożenie

Powoduje, że bufor strumienia jest niedostępny za pośrednictwem operacji buforu strumienia.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Parametry

*_Freezeit*\
**Bool** wskazujący, czy strumień ma zostać zamrożony.

### <a name="remarks"></a>Uwagi

Funkcja członkowna wywołuje[zamrożenie](../standard-library/strstreambuf-class.md#freeze) [rdbuf](#rdbuf) -> (_ *Freezeit*).

### <a name="example"></a>Przykład

Zobacz [strstreambuf::freeze](../standard-library/strstreambuf-class.md#freeze) na przykład, `freeze`który używa .

## <a name="strstreampcount"></a><a name="pcount"></a>strstream::pcount

Zwraca liczbę elementów zapisanych w kontrolowanej sekwencji.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów zapisanych w kontrolowanej sekwencji.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount).

### <a name="example"></a>Przykład

Zobacz [strstreambuf::pliczyć](../standard-library/strstreambuf-class.md#pcount) dla próbki przy użyciu pcount.

## <a name="strstreamrdbuf"></a><a name="rdbuf"></a>strstream::rdbuf

Zwraca wskaźnik do skojarzonego strumienia strstreambuf obiektu.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu strstreambuf skojarzonego strumienia.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca adres przechowywanego `pointer` buforu strumienia typu do [strstreambuf](../standard-library/strstreambuf-class.md).

### <a name="example"></a>Przykład

Zobacz [strstreambuf::plice](../standard-library/strstreambuf-class.md#pcount) dla próbki, która `rdbuf`używa .

## <a name="strstreamstr"></a><a name="str"></a>strstream::str

Wywołania [freeze](../standard-library/strstreambuf-class.md#freeze), a następnie zwraca wskaźnik na początku kontrolowanej sekwencji.

```cpp
char *str();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do początku kontrolowanej sekwencji.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Przykład

Zobacz [strstreambuf::str](../standard-library/strstreambuf-class.md#str) dla próbki, `str`która używa .

## <a name="strstreamstrstream"></a><a name="strstream"></a>strstream::strstream

Konstruuje obiekt `strstream`typu .

```cpp
strstream();

strstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*Liczba*\
Rozmiar buforu.

*_mode*\
Tryb wejścia i wyjścia buforu. Zobacz [ios_base::openmode, aby](../standard-library/ios-base-class.md#openmode) uzyskać więcej informacji.

*Ptr*\
Bufor.

### <a name="remarks"></a>Uwagi

Oba konstruktory inicjują klasę podstawową, `sb` wywołując [streambuf](../standard-library/streambuf-typedefs.md#streambuf) **(sb),** gdzie jest przechowywanym obiektem klasy [strstreambuf](../standard-library/strstreambuf-class.md). Pierwszy konstruktor również `sb` inicjuje, wywołując [strstreambuf](../standard-library/strstreambuf-class.md#strstreambuf). Drugi konstruktor inicjuje klasę podstawową na dwa sposoby:

- Jeśli `_Mode`  &  **ios_base::app**== 0, *ptr* musi wyznaczyć pierwszy element `count` tablicy elementów, `strstreambuf`a `ptr` `count`konstruktor wywołuje ( , , `ptr`).

- W przeciwnym razie *ptr* musi wyznaczyć pierwszy element tablicy elementów zliczania, który zawiera ciąg C, którego `ptr`  +  `strlen` `ptr`pierwszy element jest wyznaczony przez *ptr,* a konstruktor wywołuje `strstreambuf`( `ptr`, , `count`( ).

## <a name="see-also"></a>Zobacz też

[Iostream](../standard-library/istream-typedefs.md#iostream)\
[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
