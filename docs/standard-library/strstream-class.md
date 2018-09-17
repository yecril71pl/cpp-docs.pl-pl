---
title: strstream — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- strstream/std::strstream::freeze
- strstream/std::strstream::pcount
- strstream/std::strstream::rdbuf
- strstream/std::strstream::str
dev_langs:
- C++
helpviewer_keywords:
- std::strstream [C++], freeze
- std::strstream [C++], pcount
- std::strstream [C++], rdbuf
- std::strstream [C++], str
ms.assetid: 63f3be31-9e36-42b1-9715-a474a5997e2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b321891bc5b9392fffc72ec0c9661a39a5631e5a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717837"
---
# <a name="strstream-class"></a>strstream — Klasa

Opisuje obiekt, który kontroluje wstawienia i wydobycia elementów i obiektów zakodowanych przy użyciu bufor strumienia klasy [strstreambuf —](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Składnia

```cpp
class strstream : public iostream
```

## <a name="remarks"></a>Uwagi

Obiekt przechowuje obiekt klasy `strstreambuf`.

> [!NOTE]
> Ta klasa jest przestarzały. Należy rozważyć użycie [stringstream](../standard-library/sstream-typedefs.md#stringstream) lub [wstringstream](../standard-library/sstream-typedefs.md#wstringstream) zamiast tego.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[strstream](#strstream)|Tworzy obiekt typu `strstream`.|

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

## <a name="freeze"></a>  strstream::FREEZE

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

Zobacz [strstreambuf::freeze](../standard-library/strstreambuf-class.md#freeze) przykład, który używa `freeze`.

## <a name="pcount"></a>  strstream::pcount

Zwraca liczbę elementów zapisywane w kontrolowanej sekwencji.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów zapisywane w kontrolowanej sekwencji.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [rdbuf —](#rdbuf) -> [pcount —](../standard-library/strstreambuf-class.md#pcount).

### <a name="example"></a>Przykład

Zobacz [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) przykład użycia pcount —.

## <a name="rdbuf"></a>  strstream::rdbuf

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

## <a name="str"></a>  strstream::str

Wywołania [freeze](../standard-library/strstreambuf-class.md#freeze), a następnie zwraca wskaźnik do początku kontrolowanej sekwencji.

```cpp
char *str();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik na początek kontrolowanej sekwencji.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [rdbuf —](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Przykład

Zobacz [strstreambuf::str](../standard-library/strstreambuf-class.md#str) dla przykładu, który używa `str`.

## <a name="strstream"></a>  strstream::strstream

Tworzy obiekt typu `strstream`.

```cpp
strstream();

strstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*Liczba*<br/>
Rozmiar buforu.

*_Tryb*<br/>
Tryb wejściowe i wyjściowe buforu. Zobacz [ios_base::openmode](../standard-library/ios-base-class.md#openmode) Aby uzyskać więcej informacji.

*ptr*<br/>
Bufor.

### <a name="remarks"></a>Uwagi

Oba konstruktory inicjowania klasy bazowej, wywołując [streambuf](../standard-library/streambuf-typedefs.md#streambuf)( **sb**), gdzie `sb` jest przechowywany obiekt klasy [strstreambuf —](../standard-library/strstreambuf-class.md). Pierwszy Konstruktor inicjuje również `sb` przez wywołanie metody [strstreambuf —](../standard-library/strstreambuf-class.md#strstreambuf). Drugi Konstruktor inicjuje klasę bazową, jeden z dwóch sposobów:

- Jeśli `_Mode`  &  **ios_base::app**== 0, następnie *ptr* należy wyznaczyć pierwszy element tablicy `count` elementów i Konstruktor wywołuje `strstreambuf`( `ptr`, `count`, `ptr`).

- W przeciwnym razie *ptr* należy wyznaczyć pierwszy element tablicy liczba elementów zawierające ciąg C którego pierwszy element określony przez *ptr*i wywołuje konstruktor `strstreambuf`( `ptr`, `count`, `ptr` + `strlen`( `ptr`) ).

## <a name="see-also"></a>Zobacz także

[iostream](../standard-library/istream-typedefs.md#iostream)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
