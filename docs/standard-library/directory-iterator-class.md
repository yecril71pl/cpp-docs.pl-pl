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
ms.openlocfilehash: 8c6dcce3de32c7e25d2489cb508454dff500a1a6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454425"
---
# <a name="directoryiterator-class"></a>directory_iterator — klasa

Opisuje iterator danych wejściowych, który przechodzi przez nazwy plików w katalogu. W przypadku iteratora `X`wyrażenie `*X` szacuje obiekt klasy `directory_entry` , która otacza nazwę pliku i wszystkie znane informacje o stanie.

`path`Klasa przechowuje obiekt typu, o nazwie `mydir` w tym miejscu do celów specyfikacji, który reprezentuje nazwę katalogu do sekwencjonowania i obiekt typu `directory_entry` wywoływanego `myentry` w tym miejscu, który reprezentuje bieżący Nazwa pliku w sekwencji katalogów. Domyślny skonstruowany obiekt typu `directory_entry` ma pustą `mydir` nazwę ścieżki i reprezentuje iterator końca sekwencji.

Na przykład, mając katalog `abc` z wpisami `def` i `ghi`, kod:

`for (directory_iterator next(path("abc")), end; next != end; ++next)     visit(next->path());`

będzie wywoływał `visit` z argumentami `path("abc/def")` i `path("abc/ghi")`.

Aby uzyskać więcej informacji i przykładów kodu, zobacz [Nawigacja systemu plikówC++()](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Składnia

```cpp
class directory_iterator;
```

### <a name="constructors"></a>Konstruktorów

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
|[operator!=](#op_neq)|Zwraca `!(*this == right)`wartość.|
|[operator=](#op_as)|Operatory przypisywania domyślnego elementu członkowskiego zachowują się zgodnie z oczekiwaniami.|
|[operator==](#op_eq)|Zwraca **wartość true** tylko wtedy `*this` , gdy obie i *prawo* są iteratorami End-of-Sequence lub oba nie są kompletnymi iteratorami sekwencji.|
|[zakład](#op_star)|Zwraca `myentry`wartość.|
|[operator — >](#op_cast)|Zwraca `&**this`wartość.|
|[operator++](#op_increment)|Wywołuje `increment()`, następnie zwraca `*this`lub tworzy kopię obiektu, wywołuje `increment()`, a następnie zwraca kopię.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<eksperymentalny/> systemu plików

**Przestrzeń nazw:** std:: eksperymentalne:: filesystem

## <a name="directory_iterator"></a>Directory_iterator::d irectory_iterator

Pierwszy Konstruktor tworzy iterator końca sekwencji. Drugi i trzeci konstruktory przechowują *Pval* w `mydir`, a następnie próbują otworzyć `mydir` i odczytać jako katalog. W przypadku pomyślnego przechowywania pierwszej nazwy pliku w katalogu w `myentry`programie; w przeciwnym razie tworzą iterator sekwencji końcowej.

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

## <a name="increment"></a>Directory_iterator:: Increment

Funkcja próbuje przejść do kolejnej nazwy pliku w katalogu. Jeśli to się powiedzie, przechowuje tę `myentry`nazwę pliku w; w przeciwnym razie generuje iterator sekwencji końcowej.

```cpp
directory_iterator& increment(error_code& ec) noexcept;
```

## <a name="op_neq"></a>Directory_iterator:: operator! =

Operator elementu członkowskiego `!(*this == right)`zwraca.

```cpp
bool operator!=(const directory_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
[Directory_iterator](../standard-library/directory-iterator-class.md) jest porównywany `directory_iterator`z.

## <a name="op_as"></a>Directory_iterator:: operator =

Operatory przypisywania domyślnego elementu członkowskiego zachowują się zgodnie z oczekiwaniami.

```cpp
directory_iterator& operator=(const directory_iterator&) = default;
directory_iterator& operator=(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
[Directory_iterator](../standard-library/directory-iterator-class.md) kopiowany do `directory_iterator`.

## <a name="op_eq"></a>Directory_iterator:: operator = =

Operator członkowski zwraca **wartość true** tylko wtedy, `*this` gdy oba i *prawo* są iteratorami kończącymi sekwencję lub oba nie są kompletnymi iteratorami sekwencji.

```cpp
bool operator==(const directory_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
[Directory_iterator](../standard-library/directory-iterator-class.md) jest porównywany `directory_iterator`z.

## <a name="op_star"></a>Directory_iterator:: operator *

Operator elementu członkowskiego `myentry`zwraca.

```cpp
const directory_entry& operator*() const;
```

## <a name="op_cast"></a>Directory_iterator:: operator->

Funkcja członkowska zwraca `&**this`wartość.

```cpp
const directory_entry * operator->() const;
```

## <a name="op_increment"></a>Directory_iterator:: operator + +

Pierwsza funkcja elementu członkowskiego `increment()`wywołuje metodę, `*this`a następnie zwraca. Druga funkcja członkowska wykonuje kopię obiektu, wywołuje `increment()`, a następnie zwraca kopię.

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
[Nawigacja w systemie plikówC++()](../standard-library/file-system-navigation.md)
