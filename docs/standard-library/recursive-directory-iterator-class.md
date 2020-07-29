---
title: recursive_directory_iterator — klasa
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::tr2::sys::recursive_directory_iterator
ms.assetid: 79a061bd-5b64-404c-97e8-749c888c2ced
ms.openlocfilehash: 0f9bdc3edd7f5798afaa8d170adc35708a6aafa2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217626"
---
# <a name="recursive_directory_iterator-class"></a>recursive_directory_iterator — klasa

Opisuje iterator danych wejściowych, który umożliwia cykliczne przechodzenie sekwencji między nazwami plików w katalogu. W przypadku iteratora `X` wyrażenie `*X` szacuje obiekt klasy `directory_entry` , która otacza nazwę pliku i wszystkie znane informacje o stanie.

Aby uzyskać więcej informacji i przykładów kodu, zobacz [Nawigacja w systemie plików (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Składnia

```cpp
class recursive_directory_iterator;
```

## <a name="remarks"></a>Uwagi

Szablony klas są przechowywane:

1. Obiekt typu `stack<pair<directory_iterator, path>>` , wywoływany `mystack` w tym miejscu do celów specyfikacji, który reprezentuje zagnieżdżenie katalogów do sekwencjonowania

1. Obiekt typu `directory_entry` o nazwie w `myentry` tym miejscu, który reprezentuje bieżącą nazwę pliku w sekwencji katalogu

1. Obiekt typu **`bool`** , o nazwie `no_push` w tym miejscu, który rejestruje, czy rekursywnie znajduje się w podkatalogach

1. Obiekt typu o `directory_options` nazwie, `myoptions` który rejestruje opcje ustalone w konstrukcji

Domyślny skonstruowany obiekt typu `recursive_directory_entry` ma iterator End of Sequence w `mystack.top().first` i reprezentuje iterator końca sekwencji. Na przykład, mając katalog `abc` z wpisami `def` (katalog), `def/ghi` , i `jkl` , kod:

```cpp
for (recursive_directory_iterator next(path("abc")), end; next != end; ++next)
    visit(next->path());
```

wywoła odwiedzenie z argumentami `path("abc/def/ghi")` i `path("abc/jkl")` . Sekwencjonowanie można zakwalifikować za pomocą poddrzewa katalogów na dwa sposoby:

1. Link symboliczny katalogu zostanie przeskanowany tylko wtedy, gdy konstruujesz `recursive_directory_iterator` z `directory_options` argumentem, którego wartość to `directory_options::follow_directory_symlink` .

1. Jeśli zostanie wywołana, `disable_recursion_pending` kolejny katalog napotkany podczas przyrostu nie będzie przeskanowany cyklicznie.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[recursive_directory_iterator](#recursive_directory_iterator)|Konstruuje a `recursive_directory_iterator` .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[ścisł](#depth)|Zwraca `mystack.size() - 1` , więc `pval` ma głębokość zero.|
|[disable_recursion_pending](#disable_recursion_pending)|Przechowuje **`true`** w `no_push` .|
|[pełny](#increment)|Przechodzi do kolejnej nazwy pliku w sekwencji.|
|[Opcje](#options)|Zwraca wartość `myoptions`.|
|[skakując](#pop)|Zwraca następny obiekt.|
|[recursion_pending](#recursion_pending)|Zwraca wartość `!no_push`.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator! =](#op_neq)|Zwraca wartość `!(*this == right)`.|
|[operator =](#op_as)|Operatory przypisywania domyślnego elementu członkowskiego zachowują się zgodnie z oczekiwaniami.|
|[operator = =](#op_eq)|Zwraca **`true`** tylko wtedy, gdy oba **`*this`** i *prawo* są iteratorami kończącymi sekwencję lub oba nie są kompletnymi iteratorami sekwencji.|
|[zakład](#op_multiply)|Zwraca wartość `myentry`.|
|[operator — >](#op_cast)|Zwraca wartość `&**this`.|
|[operator + +](#op_increment)|Zwiększa `recursive_directory_iterator` .|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<filesystem>

**Przestrzeń nazw:** std:: TR2:: sys

## <a name="recursive_directory_iteratordepth"></a><a name="depth"></a>recursive_directory_iterator::d epth

Zwraca `mystack.size() - 1` , więc `pval` ma głębokość zero.

```cpp
int depth() const;
```

## <a name="recursive_directory_iteratordisable_recursion_pending"></a><a name="disable_recursion_pending"></a>recursive_directory_iterator::d isable_recursion_pending

Przechowuje **`true`** w `no_push` .

```cpp
void disable_recursion_pending();
```

## <a name="recursive_directory_iteratorincrement"></a><a name="increment"></a>recursive_directory_iterator:: Increment

Przechodzi do kolejnej nazwy pliku w sekwencji.

```cpp
recursive_directory_iterator& increment(error_code& ec) noexcept;
```

### <a name="parameters"></a>Parametry

*udziela*\
Określony kod błędu.

### <a name="remarks"></a>Uwagi

Funkcja próbuje przejść do kolejnej nazwy pliku w sekwencji zagnieżdżonej. Jeśli to się powiedzie, przechowuje tę nazwę pliku w `myentry` ; w przeciwnym razie generuje iterator sekwencji końcowej.

## <a name="recursive_directory_iteratoroperator"></a><a name="op_neq"></a>recursive_directory_iterator:: operator! =

Zwraca wartość `!(*this == right)`.

```cpp
bool operator!=(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) do porównania.

## <a name="recursive_directory_iteratoroperator"></a><a name="op_as"></a>recursive_directory_iterator:: operator =

Operatory przypisywania domyślnego elementu członkowskiego zachowują się zgodnie z oczekiwaniami.

```cpp
recursive_directory_iterator& operator=(const recursive_directory_iterator&) = default;
recursive_directory_iterator& operator=(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parametry

*recursive_directory_iterator*\
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) kopiowana do programu `recursive_directory_iterator` .

## <a name="recursive_directory_iteratoroperator"></a><a name="op_eq"></a>recursive_directory_iterator:: operator = =

Zwraca **`true`** tylko wtedy, gdy oba **`*this`** i *prawo* są iteratorami kończącymi sekwencję lub oba nie są kompletnymi iteratorami sekwencji.

```cpp
bool operator==(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) do porównania.

## <a name="recursive_directory_iteratoroperator"></a><a name="op_multiply"></a>recursive_directory_iterator:: operator *

Zwraca wartość `myentry`.

```cpp
const directory_entry& operator*() const;
```

## <a name="recursive_directory_iteratoroperator-"></a><a name="op_cast"></a>recursive_directory_iterator:: operator->

Zwraca wartość `&**this`.

```cpp
const directory_entry * operator->() const;
```

## <a name="recursive_directory_iteratoroperator"></a><a name="op_increment"></a>recursive_directory_iterator:: operator + +

Zwiększa `recursive_directory_iterator` .

```cpp
recursive_directory_iterator& operator++();

recursive_directory_iterator& operator++(int);
```

### <a name="parameters"></a>Parametry

*ZAOKR*\
Określony przyrost.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego wywołuje metodę `increment()` , a następnie zwraca **`*this`** . Druga funkcja członkowska wykonuje kopię obiektu, wywołuje `increment()` , a następnie zwraca kopię.

## <a name="recursive_directory_iteratoroptions"></a><a name="options"></a>recursive_directory_iterator:: Options

Zwraca wartość `myoptions`.

```cpp
directory_options options() const;
```

## <a name="recursive_directory_iteratorpop"></a><a name="pop"></a>recursive_directory_iterator::p op

Zwraca następny obiekt.

```cpp
void pop();
```

### <a name="remarks"></a>Uwagi

Jeśli `depth() == 0` obiekt jest iteratorem końca sekwencji. W przeciwnym razie funkcja członkowska kończy skanowanie bieżącego (najgłębszego) katalogu i wznawia się z następną niższą głębokością.

## <a name="recursive_directory_iteratorrecursion_pending"></a><a name="recursion_pending"></a>recursive_directory_iterator:: recursion_pending

Zwraca wartość `!no_push`.

```cpp
bool recursion_pending() const;
```

## <a name="recursive_directory_iteratorrecursive_directory_iterator"></a><a name="recursive_directory_iterator"></a>recursive_directory_iterator:: recursive_directory_iterator

Konstruuje a `recursive_directory_iterator` .

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

*pval*\
Określona ścieżka.

*error_code*\
Określony kod błędu.

*Zasubskrybowanie*\
Określone opcje katalogu.

*recursive_directory_iterator*\
`recursive_directory_iterator`Którego konstrukcja `recursive_directory_iterator` ma być kopią.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor tworzy iterator końca sekwencji. Drugi i trzeci konstruktorzy przechowują **`false`** w `no_push` i `directory_options::none` w programie `myoptions` , a następnie próbują otworzyć i odczytać *Pval* jako katalog. Jeśli zakończyło się pomyślnie, zainicjują `mystack` i `myentry` wyznaczyli pierwszy plik spoza katalogu w sekwencji zagnieżdżonej; w przeciwnym razie tworzy iterator końca sekwencji.

Czwarte i piąte konstruktory zachowują się tak samo, jak drugi i trzeci, z *opts* tą różnicą, że najpierw są załączane `myoptions` . Wartość domyślna construtors zachowuje się zgodnie z oczekiwaniami.

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)\
[Nawigacja w systemie plików (C++)](../standard-library/file-system-navigation.md)
