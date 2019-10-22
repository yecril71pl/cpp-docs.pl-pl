---
title: recursive_directory_iterator — klasa
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::tr2::sys::recursive_directory_iterator
ms.assetid: 79a061bd-5b64-404c-97e8-749c888c2ced
ms.openlocfilehash: a5200c030986ebbcfccb1eba2963e8317c879eb6
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72686803"
---
# <a name="recursive_directory_iterator-class"></a>recursive_directory_iterator — klasa

Opisuje iterator danych wejściowych, który umożliwia cykliczne przechodzenie sekwencji między nazwami plików w katalogu. Dla `X` iteratora wyrażenie `*X` oblicza do obiektu klasy `directory_entry`, który zawija nazwę pliku i wszystkie znane informacje o stanie.

Aby uzyskać więcej informacji i przykładów kodu, zobacz [Nawigacja systemu plikówC++()](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Składnia

```cpp
class recursive_directory_iterator;
```

## <a name="remarks"></a>Uwagi

Szablony klas są przechowywane:

1. Obiekt typu `stack<pair<directory_iterator, path>>`, o nazwie `mystack` w tym miejscu na potrzeby specyfikacji, która reprezentuje zagnieżdżenie katalogów do sekwencjonowania

1. Obiekt typu `directory_entry` o nazwie `myentry` tutaj, który reprezentuje bieżącą nazwę pliku w sekwencji katalogu

1. Obiekt typu **bool**o nazwie `no_push` tutaj, który rejestruje, czy rekursywny w podkatalogach jest wyłączony

1. Obiekt typu `directory_options`, o nazwie `myoptions` tutaj, który rejestruje opcje ustalone w konstrukcji

Domyślny skonstruowany obiekt typu `recursive_directory_entry` ma iterator końca sekwencji w `mystack.top().first` i reprezentuje iterator końca sekwencji. Na przykład, jeśli katalog `abc` z wpisami `def` (katalog), `def/ghi` i `jkl`, kod:

```cpp
for (recursive_directory_iterator next(path("abc")), end; next != end; ++next)
    visit(next->path());
```

nawiąże odwiedzenie z argumentami `path("abc/def/ghi")` i `path("abc/jkl")`. Sekwencjonowanie można zakwalifikować za pomocą poddrzewa katalogów na dwa sposoby:

1. Link symboliczny katalogu będzie skanowany tylko wtedy, gdy konstruujesz `recursive_directory_iterator` z argumentem `directory_options`, którego wartość jest `directory_options::follow_directory_symlink`.

1. Jeśli wywołasz `disable_recursion_pending`, kolejny katalog napotkany podczas przyrostu nie będzie przeskanowany cyklicznie.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[recursive_directory_iterator](#recursive_directory_iterator)|Konstruuje `recursive_directory_iterator`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[ścisł](#depth)|Zwraca `mystack.size() - 1`, więc `pval` ma głębokość równą zero.|
|[disable_recursion_pending](#disable_recursion_pending)|Przechowuje **wartość true** w `no_push`.|
|[pełny](#increment)|Przechodzi do kolejnej nazwy pliku w sekwencji.|
|[Opcje](#options)|Zwraca `myoptions`.|
|[skakując](#pop)|Zwraca następny obiekt.|
|[recursion_pending](#recursion_pending)|Zwraca `!no_push`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator!=](#op_neq)|Zwraca `!(*this == right)`.|
|[operator =](#op_as)|Operatory przypisywania domyślnego elementu członkowskiego zachowują się zgodnie z oczekiwaniami.|
|[operator = =](#op_eq)|Zwraca **wartość true** tylko wtedy, gdy oba `*this` i *Right* są iteratorami kończącymi sekwencję lub oba nie są iteracjami końca sekwencji.|
|[zakład](#op_multiply)|Zwraca `myentry`.|
|[operator — >](#op_cast)|Zwraca `&**this`.|
|[operator + +](#op_increment)|Zwiększa `recursive_directory_iterator`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<filesystem >

**Przestrzeń nazw:** std:: TR2:: sys

## <a name="depth"></a>recursive_directory_iterator::d epth

Zwraca `mystack.size() - 1`, więc `pval` ma głębokość równą zero.

```cpp
int depth() const;
```

## <a name="disable_recursion_pending"></a>recursive_directory_iterator::d isable_recursion_pending

Przechowuje **wartość true** w `no_push`.

```cpp
void disable_recursion_pending();
```

## <a name="increment"></a>recursive_directory_iterator:: Increment

Przechodzi do kolejnej nazwy pliku w sekwencji.

```cpp
recursive_directory_iterator& increment(error_code& ec) noexcept;
```

### <a name="parameters"></a>Parametry

\ *EC*
Określony kod błędu.

### <a name="remarks"></a>Uwagi

Funkcja próbuje przejść do kolejnej nazwy pliku w sekwencji zagnieżdżonej. Jeśli to się powiedzie, przechowuje nazwę pliku w `myentry`; w przeciwnym razie tworzy iterator końca sekwencji.

## <a name="op_neq"></a>recursive_directory_iterator:: operator! =

Zwraca `!(*this == right)`.

```cpp
bool operator!=(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*prawa* \
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) do porównania.

## <a name="op_as"></a>recursive_directory_iterator:: operator =

Operatory przypisywania domyślnego elementu członkowskiego zachowują się zgodnie z oczekiwaniami.

```cpp
recursive_directory_iterator& operator=(const recursive_directory_iterator&) = default;
recursive_directory_iterator& operator=(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parametry

*recursive_directory_iterator* \
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) jest kopiowana do `recursive_directory_iterator`.

## <a name="op_eq"></a>recursive_directory_iterator:: operator = =

Zwraca **wartość true** tylko wtedy, gdy oba `*this` i *Right* są iteratorami kończącymi sekwencję lub oba nie są iteracjami końca sekwencji.

```cpp
bool operator==(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*prawa* \
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) do porównania.

## <a name="op_multiply"></a>recursive_directory_iterator:: operator *

Zwraca `myentry`.

```cpp
const directory_entry& operator*() const;
```

## <a name="op_cast"></a>recursive_directory_iterator:: operator->

Zwraca `&**this`.

```cpp
const directory_entry * operator->() const;
```

## <a name="op_increment"></a>recursive_directory_iterator:: operator + +

Zwiększa `recursive_directory_iterator`.

```cpp
recursive_directory_iterator& operator++();

recursive_directory_iterator& operator++(int);
```

### <a name="parameters"></a>Parametry

\ *int*
Określony przyrost.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego wywołuje `increment()`, a następnie zwraca `*this`. Druga funkcja członkowska wykonuje kopię obiektu, wywołuje `increment()`, a następnie zwraca kopię.

## <a name="options"></a>recursive_directory_iterator:: Options

Zwraca `myoptions`.

```cpp
directory_options options() const;
```

## <a name="pop"></a>recursive_directory_iterator::p op

Zwraca następny obiekt.

```cpp
void pop();
```

### <a name="remarks"></a>Uwagi

Jeśli `depth() == 0`, obiekt zostanie iteratorem końca sekwencji. W przeciwnym razie funkcja członkowska kończy skanowanie bieżącego (najgłębszego) katalogu i wznawia się z następną niższą głębokością.

## <a name="recursion_pending"></a>recursive_directory_iterator::recursion_pending

Zwraca `!no_push`.

```cpp
bool recursion_pending() const;
```

## <a name="recursive_directory_iterator"></a>recursive_directory_iterator::recursive_directory_iterator

Konstruuje `recursive_directory_iterator`.

```cpp
recursive_directory_iterator() noexcept;
explicit recursive_directory_iterator(const path& pval);

recursive_directory_iterator(const path& pval,
    error_code& ec) noexcept;
recursive_directory_iterator(const path& pval,
    directory_options opts);

recursive_directory_iterator(const path& pval,
    directory_options opts,
    error_code& ec) noexcept;
recursive_directory_iterator(const recursive_directory_iterator&) = default;
recursive_directory_iterator(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parametry

*pval* \
Określona ścieżka.

*error_code* \
Określony kod błędu.

*\*
Określone opcje katalogu.

*recursive_directory_iterator* \
@No__t_0, do której skonstruowany `recursive_directory_iterator` ma być kopia.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor tworzy iterator końca sekwencji. Drugi i trzeci konstruktory przechowują **fałszywe** w `no_push` i `directory_options::none` w `myoptions`, a następnie próbują otworzyć i odczytać *Pval* jako katalog. Jeśli zakończyło się pomyślnie, inicjują `mystack` i `myentry`, aby wyznaczyć pierwszy plik spoza katalogu w sekwencji zagnieżdżonej; w przeciwnym razie tworzy iterator końca sekwencji.

Czwarte i piąte konstruktory zachowują się tak samo jak drugi i trzeci, z tą różnicą, że najpierw są *one w `myoptions`* . Wartość domyślna construtors zachowuje się zgodnie z oczekiwaniami.

## <a name="see-also"></a>Zobacz także

[Odwołania do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md) \
[\<filesystem >](../standard-library/filesystem.md) \
[Nawigacja w systemie plikówC++()](../standard-library/file-system-navigation.md)
