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
ms.openlocfilehash: 2d4a7a780f1a7db27bcb600c13430deaa0dc35cd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370875"
---
# <a name="ostrstream-class"></a>ostrstream — Klasa

Opisuje obiekt, który kontroluje wstawiania elementów i obiektów zakodowanych do bufora strumienia, klasy [strstreambuf —](../standard-library/strstreambuf-class.md).

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

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[blokowanie](#freeze)|Powoduje, że bufor strumienia będzie dostępny za pośrednictwem operacji buforu strumienia.|
|[pcount —](#pcount)|Zwraca liczbę elementów zapisywane w kontrolowanej sekwencji.|
|[rdbuf](#rdbuf)|Zwraca wskaźnik do strumienia skojarzonej `strstreambuf` obiektu.|
|[str](#str)|Wywołania [freeze](../standard-library/strstreambuf-class.md#freeze), a następnie zwraca wskaźnik do początku kontrolowanej sekwencji.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<strstream — >

**Namespace:** standardowe

## <a name="freeze"></a>  ostrstream::FREEZE

Powoduje, że bufor strumienia będzie dostępny za pośrednictwem operacji buforu strumienia.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Parametry

*_Freezeit*<br/>
A **bool** wskazującą, czy chcesz, aby strumień jest zablokowana.

### <a name="remarks"></a>Uwagi

Wywołania funkcji elementu członkowskiego [rdbuf —](#rdbuf) -> [freeze](../standard-library/strstreambuf-class.md#freeze)(_ *Freezeit*).

### <a name="example"></a>Przykład

Zobacz [strstream::freeze](../standard-library/strstreambuf-class.md#freeze) przykład, który używa `freeze`.

## <a name="ostrstream"></a>  ostrstream::ostrstream

Tworzy obiekt typu `ostrstream`.

```cpp
ostrstream();

ostrstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Bufor.

*Liczba*<br/>
Rozmiar buforu w bajtach.

*_Tryb*<br/>
Tryb wejściowe i wyjściowe buforu. Zobacz [ios_base::openmode](../standard-library/ios-base-class.md#openmode) Aby uzyskać więcej informacji.

### <a name="remarks"></a>Uwagi

Oba konstruktory inicjowania klasy bazowej, wywołując [ostream](../standard-library/ostream-typedefs.md#ostream)(**sb**), gdzie `sb` jest przechowywany obiekt klasy [strstreambuf —](../standard-library/strstreambuf-class.md). Pierwszy Konstruktor inicjuje również `sb` przez wywołanie metody `strstreambuf`. Drugi Konstruktor inicjuje klasę bazową, jeden z dwóch sposobów:

- Jeśli `_Mode`  &  **ios_base::app**== 0, następnie `ptr` należy wyznaczyć pierwszy element tablicy `count` elementów i Konstruktor wywołuje `strstreambuf`(`ptr`, `count`, `ptr`).

- W przeciwnym razie `ptr` należy wyznaczyć pierwszy element tablicy liczba elementów zawierające ciąg C którego pierwszy element określony przez `ptr`i wywołuje konstruktor `strstreambuf`(`ptr`, `count`, `ptr` + `strlen`( `ptr`) ).

## <a name="pcount"></a>  ostrstream::pcount

Zwraca liczbę elementów zapisywane w kontrolowanej sekwencji.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów zapisywane w kontrolowanej sekwencji.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [rdbuf —](#rdbuf) -> [pcount —](../standard-library/strstreambuf-class.md#pcount).

### <a name="example"></a>Przykład

Zobacz [strstream::pcount](../standard-library/strstreambuf-class.md#pcount) dla przykładu, który używa `pcount`.

## <a name="rdbuf"></a>  ostrstream::rdbuf

Zwraca wskaźnik do obiektu skojarzone strstreambuf — strumienia.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Wartość zwracana

Strstreambuf — obiekt skojarzonej wskaźnik do strumienia.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca adres buforu strumienia przechowywanych typu `pointer` do [strstreambuf —](../standard-library/strstreambuf-class.md).

### <a name="example"></a>Przykład

Zobacz [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) dla przykładu, który używa `rdbuf`.

## <a name="str"></a>  ostrstream::str

Wywołania [freeze](../standard-library/strstreambuf-class.md#freeze), a następnie zwraca wskaźnik do początku kontrolowanej sekwencji.

```cpp
char *str();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik na początek kontrolowanej sekwencji.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [rdbuf —](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Przykład

Zobacz [strstream::str](../standard-library/strstreambuf-class.md#str) dla przykładu, który używa `str`.

## <a name="see-also"></a>Zobacz także

[ostream](../standard-library/ostream-typedefs.md#ostream)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
