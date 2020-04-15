---
title: ostrstream — Klasa
ms.date: 11/04/2016
f1_keywords:
- strstream/std::ostrstream::freeze
- strstream/std::ostrstream::pcount
- strstream/std::ostrstream::rdbuf
- strstream/std::ostrstream::str
helpviewer_keywords:
- std::ostrstream [C++], freeze
- std::ostrstream [C++], pcount
- std::ostrstream [C++], rdbuf
- std::ostrstream [C++], str
ms.assetid: e2e34679-b266-4728-a8e1-8eda5d400e46
ms.openlocfilehash: b52ba70607a5214a6aa28f04cdded0b19a56b2f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373546"
---
# <a name="ostrstream-class"></a>ostrstream — Klasa

W tym artykule opisano obiekt, który kontroluje wstawianie elementów i zakodowanych obiektów do buforu strumienia [klasy strstreambuf](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Składnia

```cpp
class ostrstream : public ostream
```

## <a name="remarks"></a>Uwagi

Obiekt przechowuje obiekt `strstreambuf`klasy .

> [!NOTE]
> Ta klasa jest przestarzała. Zamiast tego należy rozważyć użycie [ostringstream](../standard-library/sstream-typedefs.md#ostringstream) lub [wostringstream.](../standard-library/sstream-typedefs.md#wostringstream)

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[ostrstream](#ostrstream)|Konstruuje obiekt `ostrstream`typu .|

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

## <a name="ostrstreamfreeze"></a><a name="freeze"></a>ostrstream::freeze

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

Zobacz [strstream::freeze](../standard-library/strstreambuf-class.md#freeze) na przykład, `freeze`który używa .

## <a name="ostrstreamostrstream"></a><a name="ostrstream"></a>ostrstream::ostrstream

Konstruuje obiekt `ostrstream`typu .

```cpp
ostrstream();

ostrstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>Parametry

*Ptr*\
Bufor.

*Liczba*\
Rozmiar buforu w bajtach.

*_mode*\
Tryb wejścia i wyjścia buforu. Zobacz [ios_base::openmode, aby](../standard-library/ios-base-class.md#openmode) uzyskać więcej informacji.

### <a name="remarks"></a>Uwagi

Oba konstruktory inicjują klasę podstawową, `sb` wywołując [ostream](../standard-library/ostream-typedefs.md#ostream)**(sb),** gdzie jest przechowywanym obiektem klasy [strstreambuf](../standard-library/strstreambuf-class.md). Pierwszy konstruktor również `sb` inicjuje, wywołując `strstreambuf`. Drugi konstruktor inicjuje klasę podstawową na dwa sposoby:

- Jeśli `_Mode`  &  **ios_base::app**== 0, `ptr` należy wyznaczyć pierwszy element `count` tablicy elementów, `strstreambuf`a`ptr` `count`konstruktor wywołuje ( , , `ptr`).

- W `ptr` przeciwnym razie należy wyznaczyć pierwszy element tablicy elementów zliczania, `ptr`który zawiera ciąg `strstreambuf`C, którego pierwszy element jest wyznaczony przez , a konstruktor`ptr`wywołuje ( , `count`, , `ptr`  +  `strlen`( `ptr`).

## <a name="ostrstreampcount"></a><a name="pcount"></a>ostrstream::pcount

Zwraca liczbę elementów zapisanych w kontrolowanej sekwencji.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów zapisanych w kontrolowanej sekwencji.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount).

### <a name="example"></a>Przykład

Zobacz [strstream::pliczone](../standard-library/strstreambuf-class.md#pcount) dla próbki, która `pcount`używa .

## <a name="ostrstreamrdbuf"></a><a name="rdbuf"></a>ostrstream::rdbuf

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

## <a name="ostrstreamstr"></a><a name="str"></a>ostrstream::str

Wywołania [freeze](../standard-library/strstreambuf-class.md#freeze), a następnie zwraca wskaźnik na początku kontrolowanej sekwencji.

```cpp
char *str();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do początku kontrolowanej sekwencji.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Przykład

Zobacz [strstream::str](../standard-library/strstreambuf-class.md#str) dla próbki, `str`która używa .

## <a name="see-also"></a>Zobacz też

[Ostream](../standard-library/ostream-typedefs.md#ostream)\
[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
