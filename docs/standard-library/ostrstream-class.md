---
title: ostrstream — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- strstream/std::ostrstream::freeze
- strstream/std::ostrstream::pcount
- strstream/std::ostrstream::rdbuf
- strstream/std::ostrstream::str
dev_langs:
- C++
helpviewer_keywords:
- std::ostrstream [C++], freeze
- std::ostrstream [C++], pcount
- std::ostrstream [C++], rdbuf
- std::ostrstream [C++], str
ms.assetid: e2e34679-b266-4728-a8e1-8eda5d400e46
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3d268b9cd2ba7d83f44b5e0ebd516208d17ee726
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858110"
---
# <a name="ostrstream-class"></a>ostrstream — Klasa

Opis obiektu, który kontroluje wstawiania elementów i obiektów zakodowanych do buforu strumienia klasy [strstreambuf —](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Składnia

```cpp
class ostrstream : public ostream
```

## <a name="remarks"></a>Uwagi

Obiekt przechowuje obiekt klasy `strstreambuf`.

> [!NOTE]
> Ta klasa jest przestarzały. Należy rozważyć użycie [ostringstream](../standard-library/sstream-typedefs.md#ostringstream) lub [wostringstream](../standard-library/sstream-typedefs.md#wostringstream) zamiast tego.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[ostrstream](#ostrstream)|Tworzy obiekt typu `ostrstream`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[Blokowanie](#freeze)|Powoduje, że jest niedostępna za pośrednictwem operacji buforu strumienia buforu strumienia.|
|[pcount](#pcount)|Zwraca liczbę z liczbą elementów zapisywane w kontrolowanej sekwencji.|
|[rdbuf](#rdbuf)|Zwraca wskaźnik do strumienia powiązanych `strstreambuf` obiektu.|
|[str](#str)|Wywołania [Zablokuj](../standard-library/strstreambuf-class.md#freeze), a następnie zwraca wskaźnik do początku kontrolowanej sekwencji.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<strstream — >

**Namespace:** Standard

## <a name="freeze"></a>  ostrstream::FREEZE

Powoduje, że jest niedostępna za pośrednictwem operacji buforu strumienia buforu strumienia.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Parametry

`_Freezeit` A `bool` wskazującą, czy ma strumień jest zablokowana.

### <a name="remarks"></a>Uwagi

Wywołania funkcji Członkowskich [rdbuf](#rdbuf) -> [freeze](../standard-library/strstreambuf-class.md#freeze)(_ *Freezeit*).

### <a name="example"></a>Przykład

Zobacz [strstream::freeze](../standard-library/strstreambuf-class.md#freeze) na przykład, który używa **Zablokuj**.

## <a name="ostrstream"></a>  ostrstream::ostrstream

Tworzy obiekt typu `ostrstream`.

```cpp
ostrstream();

ostrstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>Parametry

`ptr` Bufor.

`count` Rozmiar buforu w bajtach.

`_Mode` Tryb wejściowymi i wyjściowymi buforu. Zobacz [ios_base::openmode](../standard-library/ios-base-class.md#openmode) Aby uzyskać więcej informacji.

### <a name="remarks"></a>Uwagi

Oba konstruktory zainicjowanie klasy głównej przez wywołanie metody [ostream](../standard-library/ostream-typedefs.md#ostream)( **sb**), gdzie **sb** jest przechowywane obiekt klasy [strstreambuf —](../standard-library/strstreambuf-class.md). Pierwszy Konstruktor inicjuje również **sb** przez wywołanie metody `strstreambuf`. Drugi Konstruktor inicjuje klasy podstawowej, jeden z dwóch sposobów:

- Jeśli `_Mode`  &  **ios_base::app**== 0, następnie `ptr` musi wyznaczyć pierwszy element tablicy `count` elementów i wywołania konstruktora `strstreambuf`( `ptr`, `count`, `ptr`).

- W przeciwnym razie `ptr` musi wyznaczyć pierwszy element tablicy liczba elementów zawierający parametry C których pierwszy element określony przez `ptr`i wywołania konstruktora `strstreambuf`( `ptr`, `count`, `ptr` + `strlen`( `ptr`) ).

## <a name="pcount"></a>  ostrstream::pcount

Zwraca liczbę z liczbą elementów zapisywane w kontrolowanej sekwencji.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów zapisywane w kontrolowanej sekwencji.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount).

### <a name="example"></a>Przykład

Zobacz [strstream::pcount](../standard-library/strstreambuf-class.md#pcount) dla przykładu korzystającego z `pcount`.

## <a name="rdbuf"></a>  ostrstream::rdbuf

Zwraca wskaźnik do obiektu skojarzone strstreambuf — strumienia.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do strumienia powiązanych strstreambuf — obiektu.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca adres buforu strumienia przechowywanych typu **wskaźnika** do [strstreambuf —](../standard-library/strstreambuf-class.md).

### <a name="example"></a>Przykład

Zobacz [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) dla przykładu korzystającego z `rdbuf`.

## <a name="str"></a>  ostrstream::str

Wywołania [Zablokuj](../standard-library/strstreambuf-class.md#freeze), a następnie zwraca wskaźnik do początku kontrolowanej sekwencji.

```cpp
char *str();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do początku kontrolowanej sekwencji.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Przykład

Zobacz [strstream::str](../standard-library/strstreambuf-class.md#str) dla przykładu korzystającego z **str**.

## <a name="see-also"></a>Zobacz także

[ostream](../standard-library/ostream-typedefs.md#ostream)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
