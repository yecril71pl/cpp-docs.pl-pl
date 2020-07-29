---
title: directory_iterator — klasa
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::directory_iterator
- filesystem/std::experimental::filesystem::_Directory_iterator::_Directory_iterator
- filesystem/std::experimental::filesystem::directory_iterator::directory_iterator
- filesystem/std::experimental::filesystem::directory_iterator::increment
- filesystem/std::experimental::filesystem::directory_iterator::operator=
- filesystem/std::experimental::filesystem::directory_iterator::operator==
- filesystem/std::experimental::filesystem::directory_iterator::operator!=
- filesystem/std::experimental::filesystem::directory_iterator::operator*
- filesystem/std::experimental::filesystem::directory_iterator::operator-&gt;
- filesystem/std::experimental::filesystem::directory_iterator::operator++
ms.assetid: dca2ecf8-3e69-4644-a83d-705061e10cc8
helpviewer_keywords:
- std::experimental::filesystem::directory_iterator
- std::experimental::filesystem::_Directory_iterator::_Directory_iterator
- std::experimental::filesystem::directory_iterator
- std::experimental::filesystem::directory_iterator::directory_iterator
- std::experimental::filesystem::directory_iterator::increment
- std::experimental::filesystem::directory_iterator::operator=
- std::experimental::filesystem::directory_iterator::operator==
- std::experimental::filesystem::directory_iterator::operator!=
- std::experimental::filesystem::directory_iterator::operator*
- std::experimental::filesystem::directory_iterator::operator-&gt;
- std::experimental::filesystem::directory_iterator::operator++
ms.openlocfilehash: a7ccc2a941da079e14092af5b81dc537db4a48c0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215780"
---
# <a name="directory_iterator-class"></a>directory_iterator — klasa

Opisuje iterator danych wejściowych, który przechodzi przez nazwy plików w katalogu. W przypadku iteratora `X` wyrażenie `*X` szacuje obiekt klasy `directory_entry` , która otacza nazwę pliku i wszystkie znane informacje o stanie.

Klasa przechowuje obiekt typu `path` , o nazwie `mydir` w tym miejscu do celów specyfikacji, który reprezentuje nazwę katalogu do sekwencjonowania i obiekt typu `directory_entry` wywoływanego `myentry` w tym miejscu, który reprezentuje bieżącą nazwę pliku w sekwencji katalogu. Domyślny skonstruowany obiekt typu `directory_entry` ma pustą `mydir` nazwę ścieżki i reprezentuje iterator końca sekwencji.

Na przykład, mając katalog `abc` z wpisami `def` i `ghi` , kod:

`for (directory_iterator next(path("abc")), end; next != end; ++next)     visit(next->path());`

będzie wywoływał `visit` z argumentami `path("abc/def")` i `path("abc/ghi")` .

Aby uzyskać więcej informacji i przykładów kodu, zobacz [Nawigacja w systemie plików (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Składnia

```cpp
class directory_iterator;
```

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[directory_iterator](#directory_iterator)|Konstruuje iterator danych wejściowych, który przechodzi przez nazwy plików w katalogu.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[pełny](#increment)|Próbuje przejść do kolejnej nazwy pliku w katalogu.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator! =](#op_neq)|Zwraca wartość `!(*this == right)`.|
|[operator =](#op_as)|Operatory przypisywania domyślnego elementu członkowskiego zachowują się zgodnie z oczekiwaniami.|
|[operator = =](#op_eq)|Zwraca **`true`** tylko wtedy, gdy oba **`*this`** i *prawo* są iteratorami kończącymi sekwencję lub oba nie są kompletnymi iteratorami sekwencji.|
|[zakład](#op_star)|Zwraca wartość `myentry`.|
|[operator — >](#op_cast)|Zwraca wartość `&**this`.|
|[operator + +](#op_increment)|Wywołuje, `increment()` następnie zwraca **`*this`** lub tworzy kopię obiektu, wywołuje `increment()` , a następnie zwraca kopię.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<experimental/filesystem>

**Przestrzeń nazw:** std:: eksperymentalne:: filesystem

## <a name="directory_iteratordirectory_iterator"></a><a name="directory_iterator"></a>directory_iterator::d irectory_iterator

Pierwszy Konstruktor tworzy iterator końca sekwencji. Drugi i trzeci konstruktory przechowują *Pval* w `mydir` , a następnie próbują otworzyć i odczytać `mydir` jako katalog. W przypadku pomyślnego przechowywania pierwszej nazwy pliku w katalogu w programie `myentry` ; w przeciwnym razie tworzą iterator sekwencji końcowej.

Wartość domyślna construtors zachowuje się zgodnie z oczekiwaniami.

```cpp
directory_iterator() noexcept;
explicit directory_iterator(const path& pval);

directory_iterator(const path& pval, error_code& ec) noexcept;
directory_iterator(const directory_iterator&) = default;
directory_iterator(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parametry

*pval*\
Ścieżka nazwy przechowywanego pliku.

*udziela*\
Kod błędu stanu.

*directory_iterator*\
Przechowywany obiekt.

## <a name="directory_iteratorincrement"></a><a name="increment"></a>directory_iterator:: Increment

Funkcja próbuje przejść do kolejnej nazwy pliku w katalogu. Jeśli to się powiedzie, przechowuje tę nazwę pliku w `myentry` ; w przeciwnym razie generuje iterator sekwencji końcowej.

```cpp
directory_iterator& increment(error_code& ec) noexcept;
```

## <a name="directory_iteratoroperator"></a><a name="op_neq"></a>directory_iterator:: operator! =

Operator elementu członkowskiego zwraca `!(*this == right)` .

```cpp
bool operator!=(const directory_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
[Directory_iterator](../standard-library/directory-iterator-class.md) jest porównywana z `directory_iterator` .

## <a name="directory_iteratoroperator"></a><a name="op_as"></a>directory_iterator:: operator =

Operatory przypisywania domyślnego elementu członkowskiego zachowują się zgodnie z oczekiwaniami.

```cpp
directory_iterator& operator=(const directory_iterator&) = default;
directory_iterator& operator=(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
[Directory_iterator](../standard-library/directory-iterator-class.md) kopiowana do programu `directory_iterator` .

## <a name="directory_iteratoroperator"></a><a name="op_eq"></a>directory_iterator:: operator = =

Operator elementu członkowskiego zwraca **`true`** tylko wtedy **`*this`** , gdy oba i *prawo* są iteratorami End-of-Sequence lub oba nie są kompletnymi iteratorami sekwencji.

```cpp
bool operator==(const directory_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
[Directory_iterator](../standard-library/directory-iterator-class.md) jest porównywana z `directory_iterator` .

## <a name="directory_iteratoroperator"></a><a name="op_star"></a>directory_iterator:: operator *

Operator elementu członkowskiego zwraca `myentry` .

```cpp
const directory_entry& operator*() const;
```

## <a name="directory_iteratoroperator-"></a><a name="op_cast"></a>directory_iterator:: operator->

Funkcja członkowska zwraca wartość `&**this` .

```cpp
const directory_entry * operator->() const;
```

## <a name="directory_iteratoroperator"></a><a name="op_increment"></a>directory_iterator:: operator + +

Pierwsza funkcja elementu członkowskiego wywołuje metodę `increment()` , a następnie zwraca **`*this`** . Druga funkcja członkowska wykonuje kopię obiektu, wywołuje `increment()` , a następnie zwraca kopię.

```cpp
directory_iterator& operator++();
directory_iterator& operator++(int);
```

### <a name="parameters"></a>Parametry

*ZAOKR*\
Liczba przyrostów.

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)\
[Nawigacja w systemie plików (C++)](../standard-library/file-system-navigation.md)
